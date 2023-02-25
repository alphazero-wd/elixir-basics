# Modules

## **What are modules used for?**

Modules are used to organise named and private functions into one namespace.

Here is an example of how a module is created in Elixir.

A function in a module is declared using the `def` keyword.

```exs
defmodule Math do
  def sum(a, b) do
    a + b
  end
end
Math.sum(2, 3)
```

```
5
```

> Modules' names MUST be **capitalised**.
>
> Any named functions MUST be **within** a module.
>
> The last line of a function automatically returns whatever is on that line.

Private functions in a module can only be accessed by functions within that module solely.

Private functions are declared using the `defp` keyword.

```exs
defmodule Greet do
  def hello(name) do
    greeting(name)
  end

  defp greeting(name) do
    "Hello #{name}"
  end
end
Greet.hello("John")
```

```
"Hello John"
```

> Any attempts to access it outside the module will receive an error.

```exs
Greet.greeting("John")
```

```
** (UndefinedFunctionError) function Greet.greet/0 is undefined or private
    Greet.greet()
```

Modules' names can be separated by periods (`.`) as a way of adding clarity and uniqueness to each of them.

```exs
defmodule Greeting.Example do
  def hello(name) do
    "Hello #{name}"
  end
end
```

## **Module Attributes**

Module Attributes are used as constants throughout a module.

```exs
defmodule Greetings do
  @name "George"
  def hello(), do: "Hello #{@name}"
  def morning(), do: "Good morning #{@name}"
  def night(), do: "Good night #{@name}"
end
Greetings.hello()
```

```
"Hello George"
```

## **Module Docs**

Module Docs is an excellent means of making a module and all the functions within it more informative.

```exs
defmodule Example do
  @moduledoc"""
  This is my module documentation
  """

  @doc"""
  This is my test function
  multi-line comment
  and documentation.
  """
  def test(), do: "this is a test"

  # This is a line comment
  def test2(), do: "nothing"
end
```

## **Structs**

Structs are special maps within a defined set of keys and default values.

A struct must be defined within a module, which it takes its name from.

It is common for a struct to be the only thing to define within a module.

To define a struct, we use the `defstruct` keyword, along a keyword list of fields and default values.

```exs
defmodule User do
  defstruct [:name, :age]
end
u = %User{age: 20}
u.age
```

```
20
```

If we don't set the default values, then by default they will be `nil`

```exs
u.name
```

```
nil
```

Pattern matching can also be applied on structs.

```exs
%User{age: age} = u
age
```

```
20
```

## **`alias`**

`alias` is used to alias modules' names when we need to use them within other modules.

In the example below, when we alias the `Display.Result` module, we just need to call it `Result` inside the `Math` module.

```exs
defmodule Display.Result do
  def math(result) do
    "Your result is #{result}"
  end
end

defmodule Math do
  alias Display.Result
  def sum(a, b) do
    a + b
  end

  def display_result() do
    result = sum(1, 2)
    Result.math(result)
  end
end
```

We can assign a different name to the `Display.Result` module when we are within the `Math` module.

```exs
defmodule Display.Result do
  def math(result) do
    "Your result is #{result}"
  end
end

defmodule Math do
  alias Display.Result, as: Show
  def sum(a, b) do
    a + b
  end

  def display_result() do
    result = sum(1, 2)
    Show.math(result)
  end
end
```

Suppose the following example has two modules with the same prefix `Display.`, we can alias both of them like this:

```exs
defmodule Display.Result do
  def math(result) do
    "Your result is #{result}"
  end
end

defmodule Display.Math do
  def add(a, b) do
    "Your result is #{a + b}"
  end
end

defmodule MyModule do
  alias Display.{Result, Math}
  def add(a, b) do
    Math.add(a + b)
  end

  def display_math(result) do
    Result.math(result)
  end
end
MyModule.add(2, 4)
MyModule.display_math(4)
```

```
"Your result is 6"
"Your result is 4"
```

## **`import`**

Similar to `alias`, `import` is used to call a function from another function, but without referring to the module's name.

```exs
defmodule ImportExample do
  import Math
  def import_sum(a, b) do
    sum(a, b)
  end
end
ImportExample.import_sum(1, 2)
```

```
3
```

However, we cannot call the functions in the `Math` module via the `ImportExample` one. Otherwise, we will receive an error.

```exs
ImportExample.display_result()
```

```
** (UndefinedFunctionError) function ImportExample.display_result/0 is undefined or private
    ImportExample.display_result()
```

We can also choose to include/exclude the functions we want to import using the `only` or `except` keyword.

In this code example, we only select the `sum` function from the `Math` module that has exactly two arguments.

```exs
defmodule ImportExample do
  import Math, only: [sum: 2]
end
```

In this code example, we select everything from the `Math` module except for the `sum` function.

```exs
defmodule ImportExample do
  import Math, except: [sum: 2]
end
```
