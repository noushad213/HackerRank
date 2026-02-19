# 1. Nested Loop

In an array of multiple elements e.g student names that have similar value and we need to find particular value
e.g 2nd lowest we can use

### step 1: create a set of the elements present in the array (sets remove redundant values) 
unique_scores = sorted(set(score for name, score in students)) #students is an array 

### Step 2: Get second lowest score
second_lowest = unique_scores[1] #the [1] means the 2nd element in 0 indexing (2nd lowest value)

---

if you have have a **dictionary** and need to add keys and values to it, we do:
```python
dictionary[key] = value
```

**Important: What If Key Already Exists?** then we do:

```python
student["Alice"] = 95
```
This updates the value.

So:
If key doesn’t exist → it gets added

If key exists → value gets updated

# 2.Finding the percentage
we have to take keys and assign multiple values to it

```python
d = {}

n = int(input("How many keys? "))

for _ in range(n):
    key = input("Enter key: ")
    values = list(map(int, input("Enter values separated by space: ").split()))
    d[key] = values

print(d)

```

