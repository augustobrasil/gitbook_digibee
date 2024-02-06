---
description: >-
  Discover the Double Braces functions offered in the Digibee iPaaS. This page
  covers how best for users to create and implement String functions. Learn more
  here.
---

# String functions

String functions are used to manipulate string data. These are the string functions you can use with Digibee's Double Braces language:

## CAPITALIZE <a href="#u5refs2xpjlr" id="u5refs2xpjlr"></a>

Capitalizes the first character of a string. Other characters are not affected.

### Syntax <a href="#id-6s6rcbdgcmc6" id="id-6s6rcbdgcmc6"></a>

```
CAPITALIZE(value : string) -> string
```

* `value` : the string whose first letter is to be capitalized.

Returns: a string that is a version of value with the first character in upper case.

### Usage example <a href="#x0vw7o6t67vq" id="x0vw7o6t67vq"></a>

```
{{ CAPITALIZE("hello, world!") }}
```

The expected result is:

```
"Hello, world!"
```

## CONCAT <a href="#id-8prry81brr15" id="id-8prry81brr15"></a>

Concatenates any number of strings into a single string.

### Syntax <a href="#uby7flrwwf94" id="uby7flrwwf94"></a>

```
CONCAT(*values: string) -> string
```

* `values`: any number of strings to be concatenated.

Returns: the concatenated string.

### Usage example <a href="#kh4zq3bj4kzz" id="kh4zq3bj4kzz"></a>

```
{{ CONCAT("Hello", ", ", "world!") }}
```

The expected result is:

<pre><code><strong>"Hello, world!"
</strong></code></pre>

## CONTAINS <a href="#qct9pufrayjq" id="qct9pufrayjq"></a>

Checks if a substring is contained in a given string.

### Syntax <a href="#id-458txb5idk20" id="id-458txb5idk20"></a>

```
CONTAINS(main_string: string, sub_string: string) -> boolean
```

* `main_string`: a string representing the main string to search in.
* `sub_string`: a string representing the substring to search for.

Returns: a boolean value indicating whether the substring is found or not. true is returned if the substring is found in the main string, and false is returned otherwise.

### Usage example <a href="#id-5ruj3vqxkwiv" id="id-5ruj3vqxkwiv"></a>

```
{{ CONTAINS("Hello, world!", "world") }}
```

The expected result is:

```
true
```

## DEFAULT <a href="#u0ejuwlrilku" id="u0ejuwlrilku"></a>

Returns a default value when a reference is made to a null or nonexistent value.

### Syntax <a href="#dop8rov3lypp" id="dop8rov3lypp"></a>

```
DEFAULT(value : string, defaultValue : string) -> string
```

* `value`: the value to be checked for null or nonexistence.
* `defaultValue`: the default value to be returned if value is null or nonexistent.

Returns: either value, if value is not null or nonexistent, or defaultValue, if it is.

### Usage example <a href="#gho3jiacv49a" id="gho3jiacv49a"></a>

Suppose you are using this function in the JSON parameter of a JSON Generator component that receives the following payload:

```json
{
"name" : "John Doe",
"age" : null
}
```

You can use the DEFAULT function to replace the null value with a “not available” string.

```json
{
"name" : "John Doe",
"age" : {{ DEFAULT(message.age, "not available") }}
}
```

The expected result is:

```json
{
"name" : "John Doe",
"age" : "not available"
}
```

Read [this article](../how-to-reference-data-using-double-braces.md) to learn more about referencing data with Double Braces.

## ESCAPE <a href="#jcnbxsk1rf4u" id="jcnbxsk1rf4u"></a>

Encode a string using escape sequences.

### Syntax <a href="#iacdzn8uylg5" id="iacdzn8uylg5"></a>

```
ESCAPE(value: string, escapeType: string<optional>) -> string
```

* `value`: the string to be encoded.
* `escapeType`: the type of escaping to be used. Valid options are `"JSON"`, `"XML"`, `"CSV"`, and `"HTML"`. Defaults to `“JSON”`.

Returns: a new string in which certain characters have been escaped.

### Usage example <a href="#q7iuh97f1pq" id="q7iuh97f1pq"></a>

```
{{ ESCAPE("<h1>Hello, world!</h1>", "HTML") }}
```

The expected result is:

```
"&lt;h1&gt;Hello, world!&lt;/h1&gt;"
```

## INDEXOF <a href="#kswb7z2j6nn1" id="kswb7z2j6nn1"></a>

Returns the index of the first occurrence of a substring within a given string. This search is case-sensitive and the index starts at 0.

### Syntax <a href="#id-9c39nu7bpwdg" id="id-9c39nu7bpwdg"></a>

```
INDEXOF(main_string: string, sub_string: string, fromIndex: integer<optional>) -> int
```

* `main_string`: a string representing the main string to search in.
* `sub_string`: a string representing the substring to search for.
* `fromIndex`: the index from which the search should start. Defaults to 0.

Returns: an integer indicating the index of the first occurrence of the substring in the main string. If the substring is not found, the function returns -1.

### Usage examples <a href="#q7imvveo5mhr" id="q7imvveo5mhr"></a>

```
{{ INDEXOF("Hello, world!", "world") }}
```

The expected result is:

```
7
```

```
{{ INDEXOF("Hello, world!", "welcome") }}
```

The expected result is:

```
-1
```

## JOIN <a href="#xefrecgsy97h" id="xefrecgsy97h"></a>

Concatenates a list of strings into a single string with a specified separator character between each string.

### Syntax <a href="#tjipxi8tdjus" id="tjipxi8tdjus"></a>

```
JOIN(separator: string, *values: string) -> string
```

* `separator`: a string representing the separator character to be used between each string.
* `values`: any number of strings to be concatenated.

Returns: a string value representing the concatenated string with the specified separator character between each string in the input list.

### Usage examples <a href="#a0rnwz6l4ijv" id="a0rnwz6l4ijv"></a>

```
{{ JOIN(" ", "These","words", "are", "separated","by","spaces") }}
```

The expected result is:

```
"These words are separated by spaces"
```

```
{{ JOIN("-", "These","words", "are","separated","by","hyphens") }}
```

The expected result is:

```
"These-words-are-separated-by-hyphens"
```

## LASTINDEXOF <a href="#owe5flwpcov" id="owe5flwpcov"></a>

Returns the index of the last occurrence of a substring within a given string. This search is case-sensitive and the index starts at 0.

### Syntax <a href="#sthrzot2h1zp" id="sthrzot2h1zp"></a>

```
LASTINDEXOF(main_string: string, sub_string: string) -> int
```

* `main_string`: a string representing the main string to search in.
* `sub_string`: a string representing the substring to search for.
* `fromIndex`: the index from which the search should start. Defaults to 0.

Returns: an integer indicating the index of the last occurrence of the substring in the main string. If the substring is not found, the function returns -1.

### Usage examples <a href="#k7sx9ikrxytw" id="k7sx9ikrxytw"></a>

```
{{ LASTINDEXOF("Hello, world!", "o") }}
```

The expected result is:

```
8
```

```
{{ LASTINDEXOF("Hello, world!", "a") }}
```

Because the substring “a” is not contained in the string “Hello, world!”, the expected result is:

```
-1
```

## LEFTPAD <a href="#i5y3iur4q91u" id="i5y3iur4q91u"></a>

Fills the left side of a given string with a specified character to a specific length.

### Syntax <a href="#id-19khl617u9dv" id="id-19khl617u9dv"></a>

```
LEFTPAD(value: string, length: integer, character:string<optional>) -> string
```

* `value`: the input string to be padded.
* `length`: the length of the desired string.
* `character`: the character that will be used to pad the left side of the input string. Defaults to a blank space.

Returns: a padded string of the desired length with the specified character filling the left side of the input string. If the input string is already longer than the specified length, the original string is returned.

### Usage examples <a href="#id-901u12i46to1" id="id-901u12i46to1"></a>

```
{{ LEFTPAD("example", 10, "-")
```

The expected result is:

```
"---example"
```

```
{{ LEFTPAD("hello", 5, "*")
```

Because “hello” already has 5 characters, the expected result is:

```
"hello"
```

## LOWERCASE <a href="#id-1qtjpnqc926u" id="id-1qtjpnqc926u"></a>

Converts all characters to lowercase.

### Syntax <a href="#e2dahugdq9eb" id="e2dahugdq9eb"></a>

```
LOWERCASE(value: string) -> string
```

* `value`: the input string to be converted to lowercase.

Returns: the string that is the lowercase equivalent of the input string.

### Usage example <a href="#jwtcq8vpgtk4" id="jwtcq8vpgtk4"></a>

```
{{ LOWERCASE("HELLO, WorLD!") }}
```

The expected result is:

```
"hello, world!"
```

## MATCHES <a href="#id-5twdmzt1o15n" id="id-5twdmzt1o15n"></a>

Checks if a string matches a regular expression.

### Syntax <a href="#sz6pggv20xpg" id="sz6pggv20xpg"></a>

```
MATCHES(value: string, pattern: string) -> boolean
```

* `value`: a string that is to be matched against the given regular expression.
* `pattern`: a regular expression pattern that is to be used to match against the input string.

Returns: true if the input string matches the regular expression, false, otherwise.

### Usage example <a href="#v2fv78elowng" id="v2fv78elowng"></a>

```
{{ MATCHES("123-456-7890", "\\d{3}-\\d{3}-\\d{4}") }}
```

The expected result is:

```
true
```

## NORMALIZE <a href="#qgr0hemlgztw" id="qgr0hemlgztw"></a>

Transforms any special characters into non-special characters.

### Syntax <a href="#kyisoauwfqhp" id="kyisoauwfqhp"></a>

```
NORMALIZE(value: string) -> string
```

* `value`: the string to be normalized.

Returns: the normalized string with special characters replaced by their non-special counterparts.

### Usage example <a href="#m40boknqon1o" id="m40boknqon1o"></a>

```
{{ NORMALIZE("São Paulo") }}
```

The expected result is:

```
"Sao Paulo"
```

## RANDOMSTRINGS <a href="#id-59ckydivpz17" id="id-59ckydivpz17"></a>

Generate random strings given a charset and string length.

### Syntax <a href="#id-1c5lm1kzig1m" id="id-1c5lm1kzig1m"></a>

```
RANDOMSTRINGS(charset: string, length: int) -> string
```

* `charset` : the charset to be used. Options are: `"ALPHANUMERIC”`, `"ALPHABETIC"` `"ASCII"`, and `"NUMERIC"`.
* `length`: the length of the output string.

### Usage example <a href="#u9pc3a26p6tc" id="u9pc3a26p6tc"></a>

```
{{ RANDOMSTRINGS("ALPHANUMERIC",10) }}
```

The output varies because it is random. One possible output is:

```
"lUbCIs7T3G"
```

## REPLACE <a href="#ab5usfq04ub0" id="ab5usfq04ub0"></a>

Replaces all occurrences of a substring in a string based on a given regular expression.

### Syntax <a href="#kjovog5400n4" id="kjovog5400n4"></a>

```
REPLACE(value: string, pattern: string, replacement: string) -> string
```

* `value`: the string to be searched and altered.
* `pattern`: a regular expression pattern that specifies the substring to search for.
* `replacement`: a string that will replace all occurrences of the matched pattern in the input string.

### Usage example <a href="#s6p5s6ciiy91" id="s6p5s6ciiy91"></a>

```
{{ REPLACE("Hello, world!", "Hello", "Bonjour") }}
```

The expected result is:

```
"Bonjour, world!"
```

## RIGHTPAD <a href="#abaqq7vaco4v" id="abaqq7vaco4v"></a>

Fills the right side of a given string with a specified character to a specific length.

### Syntax <a href="#nrl46ji1uy" id="nrl46ji1uy"></a>

```
RIGHTPAD(value: string, length: integer, character:string<optional>) -> string
```

* `value`: the input string to be padded.
* `length`: the length of the desired string.
* `character`: the character that will be used to pad the right side of the input string. Defaults to a blank space.

Returns: a padded string of the desired length with the specified character filling the right side of the input string. If the input string is already longer than the specified length, the original string is returned.

### Usage examples <a href="#id-96a3m2a6t8ot" id="id-96a3m2a6t8ot"></a>

```
{{ RIGHTPAD("example", 10, "-") }}
```

The expected result is:

```
"Example---"
```

```
{{ RIGHTPAD("hello", 5, "*") }}
```

Because “hello” already has 5 characters, the expected result is:

```
"hello"
```

## SPLIT <a href="#nqvcbybjckxv" id="nqvcbybjckxv"></a>

Splits a string into an array of strings based on a specified regular expression pattern.

### Syntax <a href="#id-88tmjxmdgfdm" id="id-88tmjxmdgfdm"></a>

```
SPLIT(value: string, pattern: string) -> Array[string]
```

* `value`: the string to be split.
* `pattern`: a regular expression pattern that specifies the split point. The string will be split at all occurrences of the pattern.

Returns: an array of strings resulting from the split operation.

### Usage example <a href="#dgmmk5jpdi99" id="dgmmk5jpdi99"></a>

```
{{ SPLIT("Hello, world!", " ") }}
```

The expected result is:

```
["Hello,", "world!"]
```

## STRINGMATCHES <a href="#ofjxv13z3aye" id="ofjxv13z3aye"></a>

Returns an array of all the matched expressions in a string that satisfy a given pattern.

### Syntax <a href="#a1t1wj98psbs" id="a1t1wj98psbs"></a>

```
STRINGMATCHES(value: string, pattern: string, patternFlag: string<optional>) -> Array[string]
```

* `value`: a string to search for matches.
* `pattern`: a regular expression pattern to match against the string.
* `patternFlag`: the behavior of the regular expression engine. This can be used to modify the matching behavior of the regular expression, such as case-insensitive matching, multi-line matching, or extended syntax. If not specified, the regular expression engine uses its default behavior. Options are:
  * `CANON_EQ`: activate canonical equivalence matching of Unicode characters. When this flag is activated, characters that look identical are matched even if they have different Unicode codepoints.
  * `CASE_INSENSITIVE`: deactivate case sensitivity.
  * `COMMENTS`: allow comments in the regular expression pattern. You can add comments after a hashtag #.
  * `DOTALL`: activate “dotall” mode, that allows a dot . to match the newline character \n.
  * `LITERAL`: when this flag is specified then the input string that specifies the pattern is treated as a sequence of literal characters. Metacharacters or escape sequences in the input sequence will be given no special meaning.
  * `MULTILINE`: activate matching across multiple lines.
  * `UNICODE_CASE`: allows case-insensitive matching of Unicode characters, taking into account Unicode case folding rules.
  * `UNICODE_CHARACTER_CLASS`: allows Unicode character classes in the regular expression pattern.
  * `UNIX_LINES`: changes the behavior of the ^ and $ metacharacters to match the beginning and end of a line, respectively, rather than the beginning and ending of the input string.

Returns: an array of all the matched expressions in the string that satisfy the pattern.

### Usage example <a href="#o90k2cjhdf73" id="o90k2cjhdf73"></a>

```
{{ STRINGMATCHES("Hello, world!", "hello", "CASE_INSENSITIVE") }}
```

The expected result is:

```
["Hello"]
```

## SUBSTRING <a href="#id-4lv8cj2bw3yp" id="id-4lv8cj2bw3yp"></a>

Extract a substring from a given string.

### Syntax <a href="#zbja9kv9tu53" id="zbja9kv9tu53"></a>

```
SUBSTRING(value: string, start: int, end: int<optional>, throwIndexOutOfBoundError: boolean<optional>) -> string
```

* `value`: the original string from which the substring is to be extracted.
* `start`: the starting index of the substring. The index starts at 0.
* `end`: the ending index of the substring. If not provided, the extraction will end at the last character of the original string.
* `throwIndexOutOfBoundError`: if `true`, an error will be thrown if the provided indexes are out of range. Otherwise, the original string will be returned. Defaults to `true`.

Returns: the extracted substring from the original string.

### Usage example <a href="#yx33otwo5z89" id="yx33otwo5z89"></a>

```
{{ SUBSTRING("Hello, world!", 0, 5) }}
```

The expected result is:

```
"Hello"
```

## TOSTRING <a href="#wkohwbnpqdjx" id="wkohwbnpqdjx"></a>

Convert an object to its string representation.

### Syntax <a href="#qhjkeg4256p" id="qhjkeg4256p"></a>

```
TOSTRING(object: any) -> string
```

* `object`: the object to be converted to a string. It can be of any type.

### Usage example <a href="#z38h9j3mb06s" id="z38h9j3mb06s"></a>

```
{{ TOSTRING(123) }}
```

The expected result is:

```
"123"
```

## TRIM <a href="#r5osknm614n5" id="r5osknm614n5"></a>

Removes blank spaces at the beginning and end of a string.

### Syntax <a href="#yg6q0zbm7yuu" id="yg6q0zbm7yuu"></a>

```
TRIM(value : string) -> string
```

* `value`: the string to be trimmed.

Returns: a string that is a trimmed version of value.

### Usage example <a href="#id-3rybn846ywry" id="id-3rybn846ywry"></a>

```
{{ TRIM(" Hello, world! ") }}
```

The expected result is:

```
"Hello, world!"
```

## UNESCAPE <a href="#vwrtkku5t0ab" id="vwrtkku5t0ab"></a>

Unencode a string that has escape sequences.

### Syntax <a href="#kxdb7tczlzfb" id="kxdb7tczlzfb"></a>

```
UNESCAPE(value: string, escapeType: string<optional>) -> string
```

* `value`: the string to be unencoded.
* `escapeType`: the type of escaping to be used. Valid options are `"JSON"`, `"XML"`, `"CSV"`, and `"HTML"`. Defaults to `“JSON”`.

Returns: a new string in which certain characters have been unescaped.

### Usage example <a href="#kwxq4uz99533" id="kwxq4uz99533"></a>

```
{{ UNESCAPE("&lt;h1&gt;Hello, world!&lt;/h1&gt;", "HTML") }}
```

The expected result is:

```
"<h1>Hello, world!</h1>"
```

## UPPERCASE <a href="#id-8fagsvhi79b4" id="id-8fagsvhi79b4"></a>

Converts all characters to uppercase.

### Syntax <a href="#tn6cmucn4z5a" id="tn6cmucn4z5a"></a>

```
UPPERCASE(value: string) -> string
```

* `value`: the input string to be converted to uppercase.

Returns: the string that is the uppercase equivalent of the input string.

### Usage example <a href="#ifo9sfjnp4ap" id="ifo9sfjnp4ap"></a>

```
{{ UPPERCASE("Hello, world!") }}
```

The expected result is:

```
"HELLO, WORLD!"
```
