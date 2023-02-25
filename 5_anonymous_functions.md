# Anonymous functions

## **What are anonymous functions used for?**

We can use anonymous functions when we want to group a block of code that can analyse data.

## **Examples**

### **Example 1: Calculate the sum of two numbers**

```exs
sum = fn a, b -> a + b end
sum
```

```
#Function<43.65746770/2 in :erl_eval.expr/5>
```

As seen, the variable `sum` only returns a reference to the anonymous function associated with it.

We can **call** the anonymous function above using the following syntax:

```exs
sum.(2, 3)
```

```
5
```

The initialization syntax can also be shortened even further like this:

```exs
sum = &(&1 + &2)
sum.(2, 3)
```

```
5
```

### **Example 2: Print a greeting string**

```exs
say_hello = fn name -> "Hello #{name}" end
say_hello.("John")
```

```
"Hello John"
```

Similar to the example above, the shorthand syntax can be achieved in the following manner:

```exs
say_hello = &("Hello #{&1}")
say_hello.("John")
```

```
"Hello John"
```

### **Example 3: Pattern Matching**

The anonymous function below returns either `result` or `error` depending on whichever tuple matches the one passed into the argument.

```exs
handle_result = fn
  {:ok, result} -> result
  {:error, error} -> error
end
```

```
#Function<44.65746770/1 in :erl_eval.expr/5>
```

In this case, the tuple passed into the argument matches the first tuple case, thus returning `result`, which is `"success"`.

```exs
handle_result.({:ok, "success"})
```

```
"success"
```
