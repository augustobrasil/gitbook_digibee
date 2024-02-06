---
description: >-
  Discover more about the gRPC component and how to use it on the Digibee
  Integration Platform.
---

# gRPC

**gRPC** enables calls to gRPC service of the unary and client stream type via payload or via file.

## Parameters

Take a look at the configuration options for the component. Parameters supported by [Double Braces expressions](https://docs.digibee.com/documentation/build/double-braces) are marked with `(DB)`.

<table data-full-width="true"><thead><tr><th>Parameter</th><th width="267">Description</th><th>Default value</th><th>Data type</th></tr></thead><tbody><tr><td><strong>Authenticate with client certificates</strong></td><td>When it's activated, it can select client authentication with client certificates (mTLS). Use the Certificate Chain account type.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Authenticate with Google Key</strong></td><td>When it's activated, it can select client authentication with Google Key. Use the Google Key account type.</td><td>False</td><td>Boolean</td></tr><tr><td><strong>Method Type</strong></td><td>Type of method to be used in the service invocation. The supported method types are <strong>Unary</strong>, <strong>Client Stream - via Payload</strong>, and <strong>Client Stream - via File</strong>.</td><td>Unary</td><td>String</td></tr><tr><td><strong>URL</strong></td><td>Call address of the gRPC service, for example: localhost:50051.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Headers</strong> <code>(DB)</code></td><td>Configures all the types of necessary headers for the call (for example: Authorization: Bearer Co4ECg1FeGFtcGxlLnByb3RvIjwKDEh).</td><td>N/A</td><td>Key-value pair</td></tr><tr><td><strong>Custom Accounts</strong></td><td>Set the custom account label to be used in Double Braces expressions.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Service Name</strong></td><td>Name of the service described inside the configuration file .proto of the gRPC server. Learn more in <a href="grpc.md#service-name">Parameters additional information</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Method Name</strong></td><td>Name of the method to be described inside the configuration file .proto of the gRPC server. Learn more in <a href="grpc.md#method-name">Parameters additional information</a>.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Proto Descriptor File</strong></td><td>Base64 of the “Descriptor” file from the .proto file. Learn more in <a href="grpc.md#proto-descriptor-file">Parameters additional information</a>.</td><td>N/A</td><td>String (Base64)</td></tr><tr><td><strong>Payload</strong> <code>(DB)</code></td><td>The request payload to be sent to the gRPC server. For the <strong>Unary</strong> method type, a simple object that has the fields defined in the .proto file must be used. For the <strong>Client Stream - via Payload</strong> type method, an object array, in which each array item is a message to be sent to the gRPC server, must be used.</td><td>N/A</td><td>JSON Object or Array</td></tr><tr><td><strong>File Name</strong></td><td>Name of the file used to send the payload data in <strong>Client Stream - via File</strong> mode. This file must be a JSON file that has received an array. This array must contain the messages to be sent asynchronously to the gRPC server (stream).</td><td>N/A</td><td>String</td></tr><tr><td><strong>JSON Path</strong></td><td>JSON Path expression that determines how the JSON file in the stream is read. Only for the <strong>Client Stream - via File</strong> mode.</td><td>N/A</td><td>String</td></tr><tr><td><strong>Connect Timeout</strong></td><td>Expiration time of the connection with the server (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Request Timeout</strong></td><td>Expiration time of the component request call with the gRPC server (in milliseconds).</td><td>30000</td><td>Integer</td></tr><tr><td><strong>Fail On Error</strong></td><td>If the option is activated, the execution of the pipeline with an error will be interrupted; otherwise, the pipeline execution proceeds, but the result will show a false value for the “success” property.</td><td>False</td><td>Boolean</td></tr></tbody></table>

### Parameters additional information

#### Service Name

See an example of **Service Name** as “Greeter”:

```protobuf
service Greeter {
  rpc helloMethod(Hellorequest) returns (HelloResponse);
​
}
```

#### Method Name

See an example of **Method Name** as “helloMethod”:

```protobuf
service Greeter {
  rpc helloMethod(Hellorequest) returns (HelloResponse);
​
}
```

#### Proto Descriptor File

To use this parameter, the “descriptor” must first be created from a .proto file. To create it, please follow the steps below:

1. Create the descriptor file by executing the following commands in the current directory located in the .proto file:

* **.proto file of the directory:** Example.proto
* **Name of the descriptor file to be created:** proto.desc

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

You can download the protoc compiler at [Protocol Buffer Compiler Installation](https://grpc.io/docs/protoc-installation/).

2. Encode this file to base64:

```
tLmRpZ2liZWUuZ3JwY0IMRGlnaWJlZVByb3RvUAGiAgNITFdiBnByb3RvMw==

```

3. Inform this base64 in the **Proto Descriptor File** property.

## Messages flow

### Input

An input payload to be used inside the component **Payload** parameter is expected.

### Output

When executing a SFTP component using the download, upload or move operations, the following JSON structure will be generated:

```
{
   "response": {},
   "success": "true"
}

```

* **response:** response JSON received from the gRPC service.
* **success:** "true" if there’s a connection and the script is executed even without returning errors in stderr.

### Output with error

```
{
"success": false,
"message": "Something went wrong while trying to call the gRPC server",
"error": "java.net.SocketTimeoutException: connect timed out"
}

```

* **success:** “false” when the operation fails.
* **message:** message about the error.
* **exception:** information about the type of occurred error.

To better understand the message flow in the Platform, read the [documentation on Message processing](https://docs.digibee.com/documentation/build/pipelines/messages-processing).

## gRPC component in action

### Unary

Given the .proto file example:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
rpc unary (HelloRequest) returns (HelloReply) {}
rpc clientStream (stream HelloRequest) returns (HelloReply) {}
rpc serverStream (HelloRequest) returns (stream HelloReply) {}
rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
string name = 1;
string address = 2;
}
​
message HelloReply {
string message = 1;
int32 status = 2;
}
```

Firstly, it’s necessary to generate the “descriptor” file:

1. Inside the file directory, execute the command:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. With the “descriptor” at hand, generate the base64 of the proto.desc file and add it in the **Proto Descriptor File** field.

Component configurations:

**Method Type:** Unary

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** unary

**Proto Descriptor File:** \<BASE64 OF THE DESCRIPTOR FILE GENERATE ABOVE>

**Payload:**

```
{
   "name": "Charles",
   "address": "390 Fifth Avenue"
}
```

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** disabled

**Response**

```
{
   "message": "Hi Charles",
   "status": 200
}
```

### Client Stream - via Payload

Given the .proto file:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
rpc unary (HelloRequest) returns (HelloReply) {}
rpc clientStream (stream HelloRequest) returns (HelloReply) {}
rpc serverStream (HelloRequest) returns (stream HelloReply) {}
rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
string name = 1;
string address = 2;
}
​
message HelloReply {
string message = 1;
int32 status = 2;
}
```

Firstly, it’s necessary to generate the “descriptor” file:

1. Inside the file directory, execute the command:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. With the “descriptor” at hand, generate the base64 of the proto.desc file and add it in the **Proto Descriptor File** field.

Component configurations:

**Method Type:** Client Stream - via Payload

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** clientStream

**Proto Descriptor File:** \<BASE64 OF THE DESCRIPTOR FILE GENERATED ABOVE>

**Payload:**

```
[
   {
       "name": "Charles",
       "address": "390 Fifth Avenue"
   },
   {
       "name": "Paul",
       "address": "32 Seventh Avenue"
   },
​
   {
       "name": "Yan",
       "address": "12 Fourth Avenue"
   }
]
```

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** disabled

**Response**

```
{
   "message": "Hi Charles, Paul and Yan",
   "status": 200
}
```

### Client Stream - via File

Given the following .proto file:

```protobuf
Example.proto
​
syntax = "proto3";
package digibee;
​
service Greeter {
rpc unary (HelloRequest) returns (HelloReply) {}
rpc clientStream (stream HelloRequest) returns (HelloReply) {}
rpc serverStream (HelloRequest) returns (stream HelloReply) {}
rpc Bidi(stream HelloRequest) returns (stream HelloReply);
}
​
message HelloRequest {
string name = 1;
string address = 2;
}
​
message HelloReply {
string message = 1;
int32 status = 2;
}
```

Firstly, it’s necessary to generate the “descriptor” file:

1. Inside the file directory, execute the command:

```
protoc --include_imports --descriptor_set_out=proto.desc Example.proto
```

2. With the “descriptor” at hand, generate the base64 of the proto.desc file and add it in the **Proto Descriptor File** field.

Component configurations:

**Method Type:** Client Stream - via Payload

**URL:** localhost:50051

**Service Name:** Greeter

**Method Name:** clientStream

**Proto Descriptor File:** \<BASE64 OF THE DESCRIPTOR FILE GENERATED ABOVE>

**File Name:** file.json

{% code title="file.json" %}
```
{ 
    "infos": [
    {
        "name": "Charles",
        "address": "390 Fifth Avenue"
    },
    {
        "name": "Paul",
        "address": "32 Seventh Avenue"
    },
    {
        "name": "Yan",
        "address": "12 Fourth Avenue"
    }
    ]
}
```
{% endcode %}

**JSON Path:** $.infos\[\*]

**Connect Timeout:** 30000

**Request Timeout:** 30000

**Fail On Error:** disabled

**Response**

```
{
   "message": "Hi Charles, Paul and Yan",
   "status": 200
}
```
