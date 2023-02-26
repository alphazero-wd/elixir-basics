# Useful built-in modules and functions

## **Integer**

### `to_string/1`

`to_string/1` function takes in an integer and converts it into a string.

```exs
Integer.to_string(1)
```

```
1
```

## **String**

### `capitalize/1`

`capitalize/1` function takes in a string and capitalize it i.e. make the first letter of every word in the string uppercase.

```exs
String.capitalize("hello world")
```

```
"Hello World"
```

### `downcase/1`

`downcase/1` function transforms all letters in a string into the lowercase version.

```exs
String.downcase("JOHN")
```

```
"john"
```

### `upcase/1`

`upcase/1` function transforms all letters in a string into the uppercase version.

```exs
String.upcase("john")
```

```
"JOHN"
```

### `contains/2`

`contains/2` function takes in two arguments:

- `string`: the string to work with
- `contents`: the substring to search for in `string`

and returns a boolean whether the substring `contents` is included in `string`.

```exs
String.contains?("abc", "c")
String.contains?("abc", "d")
```

```
true
false
```

> We need to put a question mark after the function name to indicate that function returns a boolean.

### `split/3`

`split/3` function takes in three arguments:

- `string`: the string to work with
- `pattern`: the pattern by which the string is split
- `options \\ []`: additional options (by default is an empty list)

and returns a list of strings after `string` has been split by `pattern`.

```exs
String.split("a-b-c", "-")
String.split("Hello my friend", " ")
```

```
["a", "b", "c"]
["Hello", "my", "friend"]
```

### `to_integer/1`

`to_integer/1` function takes in a string and convert it into an integer. If the argument is not a numeric string (like in the second line below), an error is thrown.

```exs
String.to_integer("100")
String.to_integer("a")
```

```
100

** (ArgumentError) errors were found at the given arguments:
  * 1st argument: not a textual representation of an integer
    :erlang.binary_to_integer("a")
```

### `length/1`

`length/1` function takes in a string and returns the length of it i.e. the number of characters within the string.

```exs
String.length("abcdef")
```

```
6
```

### `trim/1` and `trim/2`

`trim/1` function takes in a string and removes all the white spaces at the beginning and end of it.

```exs
String.trim("   abc   ")
```

```
"abc"
```

`trim/2` function takes in two arguments:

- `string`: the string to work with
- `to_trim`: the pattern to by which `string` is trimmed

and returns a string after being trimmed

```exs
String.trim("aaaa  abc  aaaa", "a")
```

```
"  abc  "
```

`replace/3` function takes in three following arguments:

- `string`: the string to work with
- `pattern`: the substring to be replaced in `string`
- `replacement`: the substring that will replace every `pattern` in `string`

and returns a string with every `pattern` replaced with `replacement`

```exs
String.replace("abc", "a", "d")
```

```
"dbc"
```

`reverse/1` function takes in a string and reverse it.

```exs
String.reverse("abc")
```

```
"cba"
```
