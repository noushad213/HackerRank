# 🧠 Python List Comprehension – 3D Coordinates Problem

## 🎯 Problem

Given four integers:

- `x`
- `y`
- `z`
- `n`

Generate all possible coordinates `[i, j, k]` such that:

- `0 ≤ i ≤ x`
- `0 ≤ j ≤ y`
- `0 ≤ k ≤ z`
- `i + j + k != n`

Output must be in **lexicographic increasing order**.

---

# 1️⃣ Step-by-Step Understanding

## Normal Nested Loop Version (Basic Form)

```python
result = []

for i in range(x + 1):
    for j in range(y + 1):
        for k in range(z + 1):
            if i + j + k != n:
                result.append([i, j, k])

print(result)
````

### 🔎 What This Does

* Tries all combinations of `(i, j, k)`
* Adds only those where sum is NOT equal to `n`

---

# 2️⃣ Converting to List Comprehension

## General Pattern

```python
[expression 
 for variable1 in iterable1
 for variable2 in iterable2
 ...
 if condition]
```

---

## 3D Version (Final Answer)

```python
result = [[i, j, k]
          for i in range(x + 1)
          for j in range(y + 1)
          for k in range(z + 1)
          if i + j + k != n]

print(result)
```

---

# 3️⃣ Why `range(x + 1)`?

`range()` is **exclusive** at the end.

Example:

```python
range(1)  → [0]
range(2)  → [0, 1]
```

To include `x`, we use:

```python
range(x + 1)
```

---

# 4️⃣ Mental Model

This:

```python
[[i, j, k]
 for i in ...
 for j in ...
 for k in ...
 if condition]
```

Is equivalent to:

```python
for i:
    for j:
        for k:
            if condition:
                append
```

List comprehension is just a **compact syntax for loops + append**.

---

# 5️⃣ Time Complexity

Total combinations:

(x + 1) × (y + 1) × (z + 1)

So complexity is:

O((x + 1)(y + 1)(z + 1))

---

# 6️⃣ Full Program With Input

```python
x = int(input())
y = int(input())
z = int(input())
n = int(input())

result = [[i, j, k]
          for i in range(x + 1)
          for j in range(y + 1)
          for k in range(z + 1)
          if i + j + k != n]

print(result)
```

---

# 🔥 Key Takeaways

* List comprehension replaces loops + append.
* Multiple `for` statements simulate nested loops.
* `if` at the end filters values.
* Always remember `range(limit + 1)` when including the upper bound.

```

```
