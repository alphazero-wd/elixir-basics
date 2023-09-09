# Functions

## **Functions Arguments**

Functions Arguments are what is passed into a function when it is called, based on the corresponding parameters required by that function.

In the following example, we can see there are multiple `hello` functions with different number of arguments required.

Supposing there is a function named `hello` that receives 2 arguments is denoted as `hello/2`.

```exs
defmodule Say do
  # hello/0
  def hello(), do: "Hello!"

  # hello/1
  def hello(name), do: hello() <> " " <> name

  # hello/2
  def hello(first_name, last_name) do
    "Hello #{first_name} #{last_name}!"
  end

  # hello/3
  def hello(greeting, first_name, last_name) do
    "#{greeting}! {first_name} {last_name}"
  end
end

Say.hello()
Say.hello("John")
Say.hello("John", "Doe")
Say.hello("Hi", "John", "Doe")
```

```
"Hello!"
"Hello! John"
"Hello! John Doe"
"Hi! John Doe"
```

Note when we call the same function `hello` multiple times with different number of arguments, the module `Say` finds the function that matches the same number of arguments with the called one and execute that function.

Suppose in the last line of the code above, we call `Say.hello` with 3 arguments: `"Hi"`, `"John"`, `"Doe"`, the module finds the function having 3 parameters: `greeting`, `first_name`, `last_name` and execute that one with the passed-in arguments.

## **Functions Pattern Matching**

Similar to pattern matching in conditions with `case`, `cond` and `with`, the called function corresponds to whichever one in the module whose arguments match all the pre-defined parameters.

```exs
defmodule Alphabet do
  def letter(:a), do: "a"
  def letter(:b), do: "b"
  def letter(:c), do: "c"
  def letter(letter), do: letter
end
Alphabet.letter(:a)
```

```
"a"
```

In the example above, there is a default case where the argument does not match any of the first three cases.

Suppose we remove the default case and call the function with an argument that does not hit any of the first three conditions, we will receive an error.

```exs
defmodule Alphabet do
  def letter(:a), do: "a"
  def letter(:b), do: "b"
  def letter(:c), do: "c"
end
Alphabet.letter("letter")
```

```
** (FunctionClauseError) no function clause matching in Alphabet.letter/1
    The following arguments were given to Alphabet.letter/1:
        # 1
        "letter"
    iex:3: Alphabet.letter/1
```

## **Functions Conditions**

Conditions are added to the function clause to ensure that it only executes when the given arguments satisfy a particular condition.

```exs
defmodule Math do
  def div(a, b) when b !== 0 do
    a / b
  end

  def div(a, b) do
    "Cannot divide by 0"
  end
end
Math.div(8, 2)
Math.div(8, 0)
```

```
4.0
"Cannot divide by 0"
```

Like pattern matching functions, we need to specify the default case where the arguments passed into the function do not satisfy any conditions. Otherwise, an error is thrown.

```exs
defmodule Math do
  def div(a, b) when b !== 0 do
    a / b
  end
end
Math.div(8, 0)
```

```
** (FunctionClauseError) no function clause matching in Math.div/2
    The following arguments were given to Math.div/2:
        # 1
        8
        # 2
        0
    iex:10: Math.div/2
```
