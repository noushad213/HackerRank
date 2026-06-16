# 6️⃣ Advanced String Manipulation & Mutability

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

## 7️⃣ String Formatting: f-Strings

**f-strings** (formatted string literals) cleanly evaluate variables directly inside curly braces `{}`.

```python
first = "Ross"
last = "Taylor"

print(f"Hello {first} {last}! You just delved into python.")

```

### 🔄 Legacy Alternatives

* **`.format()` method:** `"Hello {}!".format(name)`
* **Concatenation:** `"Hello " + name + "!"`