# Advanced String Manipulation & Mutability

## 🔹 Understanding String Immutability

Python strings are **immutable** (cannot be changed in place). Direct index assignment throws an error:

```python
string = "abracadabra"
string[5] = 'k' # ❌ TypeError

```

To modify a string, you must construct a completely **new** one.

---

## ✅ Method 1: String Slicing

Slicing breaks the string into pieces, drops in the new character, and welds them back together.

```python
def mutate_string(string, position, character):
    return string[:position] + character + string[position+1:]

```

### 🔍 Slicing Mechanics (`string = "abracadabra"`, `position = 5`, `character = 'k'`)

* `string[:5]` → Grabs indices `0` to `4` (`"abrac"`)
* `+ "k"` → Injects the new character (`"abrack"`)
* `string[6:]` → Grabs index `6` to the end (`"dabra"`)
* **Result:** `"abrackdabra"`

---

## ✅ Method 2: List Conversion & `.join()`

Lists are **mutable**. Convert the string to a list, modify the index, and rejoin it.

```python
def mutate_string(string, position, character):
    string_list = list(string)
    string_list[position] = character
    return "".join(string_list)

```

### 🧩 How `.join()` Works

The syntax uses the string before the dot as the **glue (separator)** to combine items in a collection.

```
"glue".join([elements])

```

* `"".join(['a', 'b', 'c'])` → `"abc"` (Empty string glue)
* `" ".join(["Hello", "world"])` → `"Hello world"` (Space glue)
* `"-".join(["2026", "06", "16"])` → `"2026-06-16"` (Hyphen glue)

⚠ **Constraint:** `.join()` throws a `TypeError` if any element in the collection is not a string (e.g., integers).

---

## String Formatting: f-Strings

**f-strings** (formatted string literals) cleanly evaluate variables directly inside curly braces `{}`.

```python
first = "Ross"
last = "Taylor"

print(f"Hello {first} {last}! You just delved into python.")

```

### 🔄 Legacy Alternatives

* **`.format()` method:** `"Hello {}!".format(name)`
* **Concatenation:** `"Hello " + name + "!"`

# Counting Overlapping Substrings

Python's built-in `string.count()` does **not** count overlapping matches. To capture overlaps, use a manual sliding window approach with string slicing.

## ✅ The Sliding Window Implementation

```python
def count_substring(string, sub_string):
    count = 0
    sub_len = len(sub_string)
    
    # Restrict range to prevent the window from overshooting the string length
    for i in range(len(string) - sub_len + 1):
        if string[i : i + sub_len] == sub_string:
            count += 1
            
    return count

```

## 🧠 Core Revision Mechanics

### 1. The Slice Formulator: `[i : i + sub_len]`

* Captures a precise window matching the size of the target substring.
* As `i` increments by 1, the window slides right, catching both overlapping and distinct matches.

### 2. The Boundary Constraint: `len(string) - sub_len + 1`

* **Why the subtraction?** Finds the absolute last index where a valid substring match can possibly start.
* **Why the `+ 1`?** Python's `range(stop)` is exclusive. Adding `1` forces the loop to actually execute and check that final valid index.

# String Validation & The `any()` Function

Python provides built-in validation methods to inspect individual characters:
* `.isalnum()` ➡️ `True` if alphanumeric (a-z, A-Z, 0-9)
* `.isalpha()` ➡️ `True` if alphabetic (a-z, A-Z)
* `.isdigit()` ➡️ `True` if digit (0-9)
* `.islower()` ➡️ `True` if lowercase letter
* `.isupper()` ➡️ `True` if uppercase letter

## ⚠ Competitive Programming Trap: Entire vs. Partial Match
Evaluating methods on the whole string (e.g., `s.isalpha()`) checks if **all** characters pass. To check if a string merely **contains** at least one matching character, combine the validation method with `any()`.

```python
# Returns True if at least one character satisfies the condition
print(any(char.isalpha() for char in s))

# String Alignment: ljust, center, rjust

These methods pad a string to a target `width` using a specific fill character (defaults to a space).

```python
text = "H"
width = 5

print(text.ljust(width, '-'))   # ➡️ "H----" (Left-aligned)
print(text.center(width, '-'))  # ➡️ "--H--" (Centered)
print(text.rjust(width, '-'))   # ➡️ "----H" (Right-aligned)