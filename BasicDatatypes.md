# 1️⃣ Working with Tuples & Finding the Second Lowest Value

## 🔹 Problem Context

Given a list like:

```python
students = [
    ("Alice", 50),
    ("Bob", 40),
    ("Charlie", 50),
    ("David", 30)
]
```

You want to find the **second lowest unique score**.

---

## ✅ Step 1: Extract Unique Scores

Use a **set** to remove duplicates, then sort:

```python
unique_scores = sorted(set(score for name, score in students))
```

### Why This Works

* `score for name, score in students` → extracts scores
* `set(...)` → removes duplicate values
* `sorted(...)` → sorts values in ascending order

Result:

```python
[30, 40, 50]
```

---

## ✅ Step 2: Get the Second Lowest

```python
second_lowest = unique_scores[1]
```

### Why `[1]`?

Python uses **0-based indexing**:

| Index | Value         |
| ----- | ------------- |
| 0     | Lowest        |
| 1     | Second lowest |
| 2     | Third lowest  |

⚠ Important: Always ensure the list has at least 2 unique values to avoid `IndexError`.

---

# 2️⃣ Dictionaries (Key-Value Pairs)

A dictionary stores data in:

```
key → value
```

Example:

```python
student = {}
student["Alice"] = 95
```

---

## 🔹 What Happens Internally?

| Case              | Result                  |
| ----------------- | ----------------------- |
| Key doesn’t exist | Adds new key-value pair |
| Key exists        | Updates the value       |

Example:

```python
student["Alice"] = 90
student["Alice"] = 95   # updates value
```

Final dictionary:

```python
{"Alice": 95}
```

---

## 🔹 Storing Multiple Values per Key

You can store a **list** as a dictionary value:

```python
d = {}

n = int(input("How many keys? "))

for _ in range(n):
    key = input("Enter key: ")
    values = list(map(int, input("Enter values separated by space: ").split()))
    d[key] = values

print(d)
```

Example output:

```python
{
  "Alice": [80, 90, 100],
  "Bob": [70, 85, 95]
}
```

---

## 🔹 Calculating an Average

```python
avg = sum(d["Alice"]) / len(d["Alice"])
```

---

## 🔹 Formatting to 2 Decimal Places

```python
print("{:.2f}".format(avg))
```

Meaning:

* `:.2f` → format as float
* `2` → two decimal places

Example:

```
83.33
```

---

# 3️⃣ Lists & Dynamic Method Execution

## 🔹 Basic List Operations

```python
my_list = []
my_list.append(5)
my_list.remove(5)
```

Lists support methods like:

* `append()`
* `extend()`
* `insert()`
* `remove()`
* `pop()`
* `sort()`
* `reverse()`

---

## 🔹 What If the Method Name Is Dynamic?

If the method name is stored as a string:

```python
method_name = "append"
```

Use `getattr()`:

```python
method = getattr(my_list, method_name)
method(5)
```

---

## 🔹 Syntax of `getattr()`

```python
getattr(object, "attribute_name", default)
```

### Parameters:

| Parameter      | Meaning                        |
| -------------- | ------------------------------ |
| object         | The object you're inspecting   |
| attribute_name | String name of method/variable |
| default        | Optional fallback value        |

Example with safety:

```python
method = getattr(my_list, "append", None)

if method:
    method(10)
```

---

# 4️⃣ Understanding Sets

A **set**:

* Removes duplicates
* Is unordered
* Does not allow indexing

Example:

```python
numbers = [1, 2, 2, 3, 3, 3]
unique = set(numbers)
```

Result:

```python
{1, 2, 3}
```

Set operations:

```python
a = {1, 2, 3}
b = {3, 4, 5}

a.union(b)
a.intersection(b)
a.difference(b)
```

---

# 5️⃣ Summary of Core Data Types

| Data Type  | Ordered                              | Mutable | Allows Duplicates | Example   |
| ---------- | ------------------------------------ | ------- | ----------------- | --------- |
| List       | ✅                                    | ✅       | ✅                 | `[1,2,3]` |
| Tuple      | ✅                                    | ❌       | ✅                 | `(1,2,3)` |
| Set        | ❌                                    | ✅       | ❌                 | `{1,2,3}` |
| Dictionary | ❌ (insertion ordered in Python 3.7+) | ✅       | Keys unique       | `{"a":1}` |

---

# 🔎 Important Concept: Mutability

* **Mutable** → Can change after creation (list, dict, set)
* **Immutable** → Cannot change (tuple, int, str)

Example:

```python
t = (1, 2)
t[0] = 5   # ❌ Error
```

---

# 🎯 Key Takeaways

* Use `set()` to remove duplicates.
* Use `sorted()` when order matters.
* Dictionaries update values if keys exist.
* Lists are flexible and mutable.
* `getattr()` allows dynamic method execution.
* Use formatting like `:.2f` for clean numeric output.

