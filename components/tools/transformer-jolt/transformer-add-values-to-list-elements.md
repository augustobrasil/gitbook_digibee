---
description: >-
  Discover more about Transformer and how to add values to list elements on the
  Digibee Integration Platform.
---

# Transformer - Add values to list elements

## **Add a Fixed value to different list elements**

### **Input**

```
{
   "happy": "true",
  "statistics": [
    {
      "id": "A",
      "min": "2.0",
      "max": "10.0",
      "avg": "7.9"
    },
    {
      "min": "6",
      "max": "6",
      "avg": "6"
    },
    {
      "id": "C"
    }
  ]
}
```

### **Transformer Spec**

```
[
  {
    "operation": "modify-overwrite-beta",
// To add the value only if it does not exist, change the operation to "modify-default-beta"
    "spec": {
      "statistics": {
        "*": {
          "newValue": "test123"
        }
      }
    }
  }
]
```

### **Output**

```
{
  "happy": "true",
  "statistics" : [ {
    "id" : "A",
    "min" : "2.0",
    "max" : "10.0",
    "avg" : "7.9",
    "newValue" : "test123"
  }, {
    "min" : "6",
    "max" : "6",
    "avg" : "6",
    "newValue" : "test123"
  }, {
    "id" : "C",
    "newValue" : "test123"
  } ]
}
```

## **Add Dynamic Values**

To add a dynamic value, use the following Transformer Spec structure:

```
[
  {
    "operation": "modify-overwrite-beta",
    // To add the value only if it does not exist, change the operation to "modify-default-beta"
    "spec": {
      "statistics": {
        "*": {
          "newValue": "@(3,happy)"
        }
      }
    }
  }
]
```

Note: in the above example, the number "3" indicates the number of levels that must be uploaded to access the JSON object. To better understand it, see the example below:

### **Input**

```
{
  "levelA": {
    "levelB": {
      "happy": "true"
    }
  },
  "levelX": {
    "statistics": [
      {
        "id": "A",
        "min": "2.0",
        "max": "10.0",
        "avg": "7.9"
      },
      {
        "min": "6",
        "max": "6",
        "avg": "6"
      },
      {
        "id": "C"
      }
    ]
  }
}
```

### **Transformer Spec**

```
[
  {
    "operation": "modify-overwrite-beta",
     "spec": {
      "nivelX": {
        "statistics": {
// the item "*" (all list elements, it is also considered a level)
          "*": {
            "newValue": "@(5,levelA.levelB.happy)"
          }
        }
      }
    }
  }
]
```

\
