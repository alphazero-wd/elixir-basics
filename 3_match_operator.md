# Match Operator

## **What is Pattern Matching?**

Pattern matching is the act of a strict comparison of two values.

## **Match operator**

Elixir does not do assignments with the `=` sign like in other programming languages, instead, what it does is **match what is on the right against what is on the left**

If we are creating a variable that **does not have any value**, the value on the right will **be bound to the variable on the left**.

```exs
x = 1
1 = x
```

```
1
```

If we try to match a valued variable to a different value, an exception will be raised.

```exs
2 = x
```

```
** (MatchError) no match of right hand side value: 1
```

The match operator can also be used on tuples.

```exs
{:ok, value} = {:ok, "success"}
```

```
{:ok, "success"}
```

Similarly, an exception is thrown if the value does not correspond to the one that the variable is holding.

```exs
{:ok, "error"} = {:ok, value}
```

```
** (MatchError) no match of right hand side value: {:ok, "success"}
```

## **Pin Operator**

The pin operator (`^`) accesses variables that already has a value, allowing us to avoid rebinding a variable with an existing value, instead, a pattern matching is performed.

Here is an example using the match operator. Initially, `x` is bound to the value `1`; then, it is rebound to `2`.

```exs
x = 1
x = 2
```

```
2
```

However, if we want to perform pattern matching between `x` and what is on the right side, the pin operator is the means to achieve this.

```exs
^x = 2
```

```
2
```

An exception is thrown if the value on the right side does not match the value the variable on the left side is holding.

```exs
^x = 3
```

```
** (MatchError) no match of right hand side value: 3
```

The pin operator can also be applied to tuples

```exs
result = "success"
{:ok, ^result} = {:ok, "success"}
```

```
{:ok, "success"}
```

```exs
result = "success"
{:ok, ^result} = {:ok, "error"}
```

```
** (MatchError) no match of right hand side value: {:ok, "error"}
```

We can reassign a different value to the `result` variable using the match operator.

```exs
{:ok, result} = {:ok, "error"}
result
```

```
"error"
```

## **Discard Unused Values with Underscores (`_`)**

If some values are not needed to be captured, they can be discarded altogether with underscores (`_`).

Take a look at an example:

```exs
{a, b, c} = {"a", "b", "c"}
```

```
{"a", "b", "c"}
```

In the example above, suppose the variable `c` is not needed elsewhere, then we can replace it with an underscore `_`.

```exs
{a, b, _} = {"a", "b", "c"}
a
```

```
"a"
```

If pattern matching is executed between two tuples of different sizes, an error is thrown.

```exs
{a, b, _} = {"a", "b"}
```

```
** (MatchError) no match of right hand side value: {"a", "b"
```
