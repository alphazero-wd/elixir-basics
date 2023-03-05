# Pipe Operator

## **What is the pipe operator?**

The pipe operator (`|>`) passes the result of an expression as the first parameter of another expression.

Here are some examples:

```exs
string = "  My String  "
string
  |> String.downcase()
  |> String.trim()
  |> String.split(" ")
  |> String.join("-")
```

```
"my-string"
```

```exs
list = [-1, 2, -3, 4, -5]
list
  |> Enum.filter(&(&1 < 0))
  |> Enum.map(&(&1 * 2))
  |> Enum.reduce(1, fn acc, x -> acc * x end)
```

```
-60
```
