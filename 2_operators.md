# Operators

### **What are operators?**

Operators are characters that allow us to perform logical operations.

We have seen arthimetical operations (`+`, `-`, `*`, `/`) in the [first section](https://github.com/alphazero-wd/elixir-basics/blob/master/1_data_types.md). In this section, we will be discussing 3 more types of operators: boolean operators, comparison operators and membership operators.

### **Boolean operators**

These operators are expected to be evaluated to booleans as their arguments.

#### **and, or, not**

`and` operator will be evaluated to `true` if **all** of the conditions within an expression satisfy.

```exs
true and false
```

```
false
```

```exs
false and "result"
```

```
false
```

```exs
true and "result"
```

```
"result"
```

`or` operator will be evaluated to `true` if **one** of the conditions within an expression satisfies.

```exs
true or false
```

```
truw
```

```exs
false or "result"
```

```
"result"
```

```exs
true or "result"
```

```
"result"
```

`not` operator will switch an expression from `true` to `false`, and vice versa.

```exs
not true
```

```
false
```

```exs
not false
```

```
true
```

#### **&&, ||, !**

`&&`, `||` and `!` are equivalent to `and`, `or` and `not` respectively. However, these operators can accept any type of arguments. Everything except for `nil` or `false` gets evaluated to `true`.

```exs
"result" && 12
```

```
12
```

```exs
false && "result"
```

```
false
```

```exs
11 && 100
```

```
100
```

```exs
nil && 12
```

```
nil
```

```exs
100 || 11
```

```
100
```

```exs
11 || nil
```

```
11
```

```exs
nil || 11
```

```
nil
```

```exs
false || "result"
```

```
"result"
```

```exs
!false
```

```
true
```

```exs
!11
```

```
false
```

```exs
!nil
```

```
true
```

```exs
!"result"
```

```
false
```

### **Comparison Operators**

These operators will compare any 2 values and return `true` or `false`

The strict equal operator (`===`) checks for equality of type and value.

```exs
1 === 1
```

```
true
```

```exs
1 === 1.0
```

```
false
```

```exs
"false" === "False"
```

```
false
```

The strict unequal operator (`!==`) checks for difference in type or value.

```exs
1 !== 1.0
```

```
true
```

```exs
1 !== 1
```

```
false
```

```exs
"true" !== "True"
```

```
true
```

```exs
"true" !== "True"
```

```
true
```

```exs
"true" !== "True"
```

```
true
```

The equal operator (`==`) only checks for the equality of value, ignores the type

```exs
1 == 1
```

```
true
```

```exs
1 == 1.0
```

```
true
```

The unequal operator (`==`) only checks for the inequality of value, ignores the type

```exs
1 != 1
```

```
false
```

```exs
1 != 1.0
```

```
false
```

The greater than (or equal) operator (`>`, `>=`) is used to check if the number before the operator is **greater than** (or equal to) the number after the operator.

```exs
11 > 1
```

```
true
```

```exs
11 > 100
```

```
false
```

```exs
11 >= 11
```

```
true
```

```exs
11 >= 100
```

```
false
```

The less than (or equal) operator (`<`, `<=`) is used to check if the number before the operator is **less than** (or equal to) the number after the operator.

```exs
11 < 1
```

```
false
```

```exs
11 < 100
```

```
true
```

```exs
11 <= 1
```

```
false
```

```exs
11 <= 11
```

```
true
```
