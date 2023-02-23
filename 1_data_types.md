# **ELIXIR BASICS**

## **Data Types**

A data type is a classification that dictates what a variable or object can hold in.

### **Integers**

Integers are whole numbers which can either be positive or negative

Examples of positive integers

```exs
1
```

```
1
```

```exs
10
```

```
10
```

Examples of negative integers

```exs
-101
```

```
-101
```

```exs
-23
```

```
-23
```

We can also do calculations on integers with operators, e.g. addition (`+`), subtraction (`-`), multiplication (`*`) and division (`/`).

```exs
2 + 2
```

```
4
```

```exs
4 - 2
```

```
2
```

```exs
4 * 4
```

```
16
```

```exs
12 / 2
```

```
6.0
```

> `12 / 2` actually prints out `6.0` instead of `6`, to make an integer division, use `div/2` instead:

```exs
div(12, 2)
```

```
6
```

Modulo operator `rem/2` returns the remainder of a division

```exs
rem(45, 8)
```

```
5
```

### **Floats**

Floats are precised numbers containing decimal points

```exs
3.14
```

```
3.14
```

```exs
1.11
```

```
1.11
```

```exs
2.0004
```

```
2.0004
```

```exs
0.25448
```

```
0.25448
```

### **Strings**

Strings are text between **double quotes (" ")**

```exs
name = "John"
name
```

```
"John"
```

> Addition operator on string `+` will raise an exception

```exs
"14" + "12"
```

```
** (ArithmeticError) bad argument in arithmetic expression: "14" + "12"
    :erlang.+("14", "12")
```

A string can be on multiple lines

```exs
"This is my long

sentence string"
```

```
"This is my long \r\n \r\n sentence string"
```

To use `"` inside a string, we can put the escape character `\` in front of it.

```exs
IO.puts("My \"string\" inside my string")
```

```
"My "string" inside my string"
```

The line break character `\n` is used to break a string into multiple lines

```exs
IO.puts("My line \n Break")
```

```
"My line
 Break"
```

#### **String Interpolation**

String Interpolation is the process of attaching other variables or values inside a string

```exs
name = "Ben"
full_name = "#{name} Simmons"
full_name
```

```
"Ben Simmons"
```

```exs
"#{2 + 2} is the result"
```

```
"4 is the result"
```

#### **String Concatenation**

```exs
name = "Ben"
last_name = "Simmons"
full_name = name <> " " <> last_name
full_name
```

```
"Ben Simmons"
```

### **Booleans**

Booleans are logical expressions which can either be evaluated into `true` or `false`

```exs
true
```

```
true
```

```exs
false
```

```
false
```

### **Atoms**

An atom is a symbol whose value also happens to be its name.

```exs
:red
```

```
:red
```

```exs
:error
```

```
:error
```

```exs
:ok
```

```
:ok
```

### **Lists**

Lists are collections of any type of data inside square brackets (`[]`)

```exs
[12, "my mom", :atom, true, 3.14]
```

```
[12, "my mom", :atom, true, 3.14]
```

```exs
list = [1, 2, 3, 4, 5]
```

```
[1, 2, 3, 4, 5]
```

```exs
colors = ["blue", "red", "white", "black"]
```

```
["blue", "red", "white", "black"]
```

We can do some basic operations on lists, such as

Prepending an element onto an existing list

```exs
list = [2, 3, 4]
[1 | list]
```

```
[1, 2, 3, 4]
```

Concatenating two lists together

```exs
list = [2, 3, 4]
[1 | list]
```

```
[1, 2, 3, 4]
```

Subtracting a list

```exs
list -- [3, 4]
```

```
[2]
```

### **Tuples**

Tuples are collections of items inside curly brackets (`{}`)

```exs
result = {:ok, :ok}
```

```
{:ok, :ok}
```

```exs
result = {:ok, "Done"}
```

```
{:ok, "Done"}
```

```exs
{:error, "Failed"}
```

```
{:error, "Failed"}
```

```exs
{:a, :b, :c, :d}
```

```
{:a, :b, :c, :d}
```

### **Maps**

Maps are collections of data stored in key-value pairs.

A key in a map can be accessed using the square-bracket notation.

```exs
emp = %{"name" => "", "age" => 0}
emp["name"]
```

```
""
```

We can instantiate a map from an existing map with some properties modified by doing the following:

```exs
john = %{emp | "name" => "John", "age": 28}
john["name"]
```

```
"John"
```

If the keys are atoms, then they can also be accessed using the dot notation.

```exs
latters = %{:a => "A", :b => "B", :c => "C", :d => "D"}
letters.a
```

```
"A"
```
