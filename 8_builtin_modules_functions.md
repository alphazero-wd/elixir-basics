# Useful built-in modules and functions

## **`Integer`**

### `to_string/1`

`to_string/1` function takes in an integer and converts it into a string.

```exs
Integer.to_string(1)
```

```
1
```

## **`String`**

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

## **`List`**

`first/1` function takes in a list and returns the first element in a list.

```exs
l = [1, 2, 3]
List.first(l)
```

```
1
```

`last/1` function takes in a list and returns the last element in a list.

```exs
l = [1, 2, 3]
List.last(l)
```

```
3
```

`to_string/1` function takes in a list and convert it into a string

```exs
List.to_string(["a", "b", "c"])
```

```
"abc"
```

## **`Map`**

`put/3` function takes in three following arguments:

- `map`: the map to work with
- `key`: a key to put in `map`
- `value`: a value put in `map` associated with `key`

and inserts a new `key`-`value` pair into `map`

> If `key` is already in `map` then the `value` of `key` will be modified (see the second line of code below).

```exs
m = %{"a" => "A", "b" => "B"}
Map.put(m, "c", "C")
Map.put(m, "a", "D")
```

```
%{"a" => "A", "b" => "B", "c" => "C"}
%{"a" => "D", "b" => "B"}
```

`put_new/3` function is identical to `put/3` except for the following fact:

> If `key` is already in `map` then the `value` of `key` **will NOT** be modified (see the second line of code below).

```exs
m = %{"a" => "A", "b" => "B"}
Map.put_new(m, "c", "C")
Map.put_new(m, "a", "D")
```

```
%{"a" => "A", "b" => "B", "c" => "C"}
%{"a" => "A", "b" => "B"}
```

`has_key/2` function takes in two following arguments:

- `map`: the map to work with
- `key`: the key to search for in `map`

and returns a boolean indicating whether `key` exists in `map`

```exs
Map.has_key?(m, "a")
Map.has_key?(m, "e")
```

```
true
false
```

`values/1` function takes in a map and returns a list of values in that map.

```exs
Map.values(m)
```

```
["A", "B"]
```

`delete/2` function takes in a map and a key to remove from the map.

```exs
Map.delete(m, "a")
```

```
%{"b" => "B"}
```

## **`Enum`**

`each/2` function takes in an enumerable, an anonymous function and iterates over all elements in that enumerable.

```exs
l = [1, 2, 3]
Enum.each(l, fn x -> IO.puts(x) end)
Enum.each(l, &(IO.puts(&1))) # shorthand
```

```
1
2
3

1
2
3
```

`map/2` function takes in an enumerable, an anonymous function indicating how an enumerable is modified and returns a newly-modified enumerable.

The code example below returns a new list in which every number is squared.

```exs
Enum.map(l, fn x -> x * x end)
Enum.map(l, &(&1 * &1))
```

```
[1, 4, 9]
[1, 4, 9]
```

`into/2` function takes two enumerables and merge them together into one.

```exs
Enum.into(l, [5, 6, 7])
```

```
[1, 2, 3, 5, 6, 7]
[1, 2, 3, 5, 6, 7]
```

`all/2` function takes in an enumerable, an anonymous function and returns a boolean indicating whether **every element** in that enumerable satisfies the conditions specified in the anonymous function.

```exs
Enum.all?(l, fn x -> x > 0 end)
Enum.all?(l, &(&1 > 0))
```

```
true
true
```

`any/2` function takes in an enumerable, an anonymous function and returns a boolean indicating whether there is **at least one element** in that enumerable satisfies the conditions specified in the anonymous function.

```exs
Enum.any?(l, fn x -> x == 1 end)
Enum.any?(l, &(&1 == 1))
```

```
true
true
```

`filter/2` function takes in an enumerable, an anonymous function and returns another enumerable only with elements satisfy pre-defined conditions in the anonymous function.

```exs
Enum.filter(l, fn x -> x > 1 end)
Enum.filter(l, &(&1 > 1))
```

```
[2, 3]
[2, 3]
```

`to_list/1` function takes in a map and convert it into a list of two-element tuples: the first and second elements in each of them form a key-value pair.

```exs
Enum.to_list(m)
```

```
[{"a", "A"}, {"b", "B"}]
```

`shuffle/1` function takes in an enumerable and shuffles it

```exs
Enum.shuffle(l)
```

```
[2, 1, 3]
```

`random/1` function takes in a starting number `start`, ending number `end` in the following syntax: `start..end` and generates an arbitrary number within the range [`start`, `end`]

```exs
Enum.random(1..10)
```

```
6
```

`sum/1` function takes in an enumerable and returns the sum of all elements within it

```exs
Enum.sum(l)
```

```
6
```

`uniq/1` function takes in an enumerable and returns only the distinct elements in it.

```exs
Enum.uniq([1, 1, 1, 2, 2, 3, 3])
```

```
[1, 2, 3]
```

There are plenty of other useful built-in functions in the `Enum` module that are worth researching in the docs [here](https://hexdocs.pm/elixir/1.12/Enum.html).
