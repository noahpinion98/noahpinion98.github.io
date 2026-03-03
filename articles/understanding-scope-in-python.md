---
layout: default
title: Understanding Scope in Python
description: A beginner-friendly explanation of Python scope, including local, enclosing, global, and built-in name resolution.
permalink: /articles/understanding-scope-in-python
---

When you're starting out with Python, one of the first tricky concepts you'll run into is **scope** - the idea that a variable isn't always accessible from everywhere in your code.

## The LEGB Rule

Python resolves variable names using the **LEGB** rule, checking these scopes in order:

1. **Local** - inside the current function.
2. **Enclosing** - in any enclosing (outer) function.
3. **Global** - at the top level of the module.
4. **Built-in** - Python's built-in names like `len` and `print`.

## Local Scope

Variables created inside a function only exist inside that function:

```python
def greet():
    message = "Hello!"
    print(message)

greet()       # prints "Hello!"
print(message)  # NameError: name 'message' is not defined
```

## Global Scope

Variables defined at the module level are accessible everywhere in that file, but you need the `global` keyword to modify them inside a function:

```python
count = 0

def increment():
    global count
    count += 1

increment()
print(count)  # 1
```

## Enclosing Scope

When you nest functions, the inner function can read variables from the outer function. To modify them, use `nonlocal`:

```python
def outer():
    x = 10
    def inner():
        nonlocal x
        x += 5
    inner()
    print(x)  # 15

outer()
```

## Key Takeaways

- Always think about *where* a variable is defined - that determines where it's visible.
- Avoid overusing `global`; it makes code harder to reason about.
- The LEGB rule is your mental model for how Python looks up names.
