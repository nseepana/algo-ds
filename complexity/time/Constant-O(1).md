# Constant Time Complexity (O(1)):

constant time complexity (O(1)) generally involve direct access to a single element in a data structure or a simple operation that doesn't depend on the size of the input data. 

### 1. Accessing an Array Element

```python
def access_element(array, index):
    return array[index]
```

### 2. Inserting/Removing from the Front of a Linked List

```python
def insert_front(linked_list, value):
    linked_list.insert(0, value)  # Assuming a Python list for simplicity
```

### 3. Checking if a Stack or Queue is Empty

```python
def is_empty(stack):
    return len(stack) == 0
```

### 4. Incrementing a Variable

```python
def increment(x):
    return x + 1
```

### 5. Setting a Dictionary/HashMap Value

```python
def set_value(dictionary, key, value):
    dictionary[key] = value
```

### 6. Getting the Top Element of a Stack

```python
def top_element(stack):
    return stack[-1]
```

### 7. Checking for an Element in a Hash Set

```python
def contains(hash_set, value):
    return value in hash_set
```

### 8. Calculating a Simple Mathematical Expression

```python
def calculate_expression(a, b):
    return a * b + 5
```

### 9. Assigning a Value to a Variable

```python
def assign_value():
    x = 10
    return x
```

### 10. Swapping Two Variables

```python
def swap(a, b):
    return b, a
```

Each of these examples demonstrates an operation that takes a constant amount of time regardless of the size of the input data. This is why they are all considered O(1) operations.
