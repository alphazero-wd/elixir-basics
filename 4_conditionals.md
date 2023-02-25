# Conditionals

## **What are conditionals?**

We can use conditional statements to handle decisions and to determine what to do based on those conditions.

## **`if` and `unless`**

The `if` statement executes the code block within if the specified condition is **true**.

```exs
color = "blue"
if color == "blue" do
  "yes"
end
```

```
"yes"
```

`unless` executes the code block within if the specified condition is **false**.

```exs
unless color == "blue" do
  "yes"
end
```

```
nil
```

### Shorthand syntax

```exs
if color == "blue", do: "yes"
```

```
"yes"
```

```exs
unless color != "blue", do: "yes"
```

```
"yes"
```

`else` executes the code block within if the specified condition `if` or `unless` does not satisfy.

```exs
color = "red"
if color == "blue" do
  "yes"
else
  "no"
end
```

```
"no"
```

There is also a shorthand syntax for the above conditional statement:

```exs
if color == "blue", do: "yes", else: "no"
```

```
"no"
```

In a similar manner, we can use `else` with `unless`:

```exs
unless color == "red" do
  "no"
else
  "yes"
end
```

```
"yes"
```

```exs
unless color == "red", do: "no", else: "yes"
```

```
"yes"
```

## **`case`**

This is used when we need to match against multiple patterns.

```exs
result = {:ok, "success"}
case result do
  {:ok, _result} -> "this matches"
  {:error, _error} -> "this won't match"
  _ -> "this matches against anything else"
end
```

```
"this matches"
```

```exs
result = {:error, "error"}
case result do
  {:ok, _result} -> "this won't match"
  {:error, _error} -> "now this one matches"
  _ -> "this matches against anything else"
end
```

```
"now this one matches"
```

```exs
result = "error"
case result do
  {:ok, _result} -> "this won't match"
  {:error, _error} -> "now this one matches"
  _ -> "this matches against anything else"
end
```

```
"this matches against anything else"
```

## **`cond`**

`cond` matches against conditions instead of values

```exs
color = "blue"
cond do
  color == "blue" -> color
  color == "red" -> color
  color == "green" -> color
  color == "black" -> color
  true -> "this catches everything else, result: #{color}"
end
```

```
"blue"
```

```exs
color = "color"
cond do
  color == "blue" -> color
  color == "red" -> color
  color == "green" -> color
  color == "black" -> color
  true -> "this catches everything else, result: #{color}"
end
```

```
"this catches everything else, result: color"
```

## **`with`**

`with` is useful when we need more than one match for the code to be executed.

```exs
result = {:ok, "success"}
error = {:error, "error"}
with {:ok, result} <- result do
  result
end
```

```
"success"
```

Here is how `with` can be used to validate multiple matches.

```exs
with {:ok, _result} <- result,
  {:error, _result} <- error do
  "This gets executed"
end
```

```
"This gets executed"
```

`with` can also be used with `else`

```exs
result = {:ok, "successs"}
with {:ok, "success"} <- result do
  result
else
  {:ok, _result} -> "This gets executed"
end
```

```
"This gets executed"
```
