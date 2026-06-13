## C++ STL Algorithms Notes

### 1. Iterators and Iterating Algorithms

#### `std::for_each()`

Applies a function to every element in a range.

```cpp
vector<int> v = {1, 2, 3};

for_each(v.begin(), v.end(), [](int x) {
    cout << x << " ";
});
```

**Time Complexity:** O(n)

---

#### `std::find()`

Searches for an element.

```cpp
auto it = find(v.begin(), v.end(), 2);

if(it != v.end())
    cout << "Found";
```

**Time Complexity:** O(n)

---

#### `std::find_if()`

Finds the first element satisfying a condition.

```cpp
auto it = find_if(v.begin(), v.end(),
                 [](int x){ return x > 2; });
```

**Time Complexity:** O(n)

---

#### `std::count()`

Counts occurrences of a value.

```cpp
int c = count(v.begin(), v.end(), 2);
```

**Time Complexity:** O(n)

---

#### `std::count_if()`

Counts elements satisfying a condition.

```cpp
int c = count_if(v.begin(), v.end(),
                [](int x){ return x % 2 == 0; });
```

**Time Complexity:** O(n)

---

#### `std::sort()`

Sorts elements in ascending order.

```cpp
sort(v.begin(), v.end());
```

**Time Complexity:** O(n log n)

---

#### `std::reverse()`

Reverses elements.

```cpp
reverse(v.begin(), v.end());
```

**Time Complexity:** O(n)

---

#### `std::rotate()`

Rotates elements.

```cpp
rotate(v.begin(), v.begin()+2, v.end());
```

Example:

```cpp
1 2 3 4 5
↓
3 4 5 1 2
```

**Time Complexity:** O(n)

---

#### `std::unique()`

Removes consecutive duplicates.

```cpp
sort(v.begin(), v.end());

auto it = unique(v.begin(), v.end());
v.erase(it, v.end());
```

Example:

```cpp
1 1 2 2 3 3
↓
1 2 3
```

**Time Complexity:** O(n)

---

#### `std::partition()`

Divides elements based on a condition.

```cpp
partition(v.begin(), v.end(),
         [](int x){ return x % 2 == 0; });
```

Example:

```cpp
1 2 3 4 5 6
↓
2 4 6 1 3 5
```

**Time Complexity:** O(n)

---

# 2. Set Algorithms

> Both ranges must be sorted.

### `std::set_union()`

```cpp
vector<int> a = {1,2,3};
vector<int> b = {2,3,4};

vector<int> result(10);

auto it = set_union(
    a.begin(), a.end(),
    b.begin(), b.end(),
    result.begin()
);
```

Output:

```cpp
1 2 3 4
```

**Time Complexity:** O(n + m)

---

### `std::set_intersection()`

Common elements.

```cpp
1 2 3
2 3 4
```

Output:

```cpp
2 3
```

**Time Complexity:** O(n + m)

---

### `std::set_difference()`

Elements present in first set but not second.

```cpp
1 2 3
2 3 4
```

Output:

```cpp
1
```

**Time Complexity:** O(n + m)

---

### `std::set_symmetric_difference()`

Elements present in exactly one set.

```cpp
1 2 3
2 3 4
```

Output:

```cpp
1 4
```

**Time Complexity:** O(n + m)

---

# 3. Min and Max Algorithms

### `std::min()`

```cpp
cout << min(10, 20);
```

Output:

```cpp
10
```

**Time Complexity:** O(1)

---

### `std::max()`

```cpp
cout << max(10, 20);
```

Output:

```cpp
20
```

**Time Complexity:** O(1)

---

### `std::min_element()`

```cpp
vector<int> v = {5,2,8,1};

auto it = min_element(v.begin(), v.end());

cout << *it;
```

Output:

```cpp
1
```

**Time Complexity:** O(n)

---

### `std::max_element()`

```cpp
auto it = max_element(v.begin(), v.end());

cout << *it;
```

Output:

```cpp
8
```

**Time Complexity:** O(n)

---

# 4. Searching and Finding Algorithms

> Works on sorted ranges unless specified.

### `std::binary_search()`

Checks whether an element exists.

```cpp
sort(v.begin(), v.end());

bool found =
    binary_search(v.begin(), v.end(), 5);
```

**Time Complexity:** O(log n)

---

### `std::lower_bound()`

Returns first element **>= target**.

```cpp
vector<int> v = {1,2,4,4,4,6};

auto it = lower_bound(
    v.begin(), v.end(), 4
);
```

Returns index of first `4`.

**Time Complexity:** O(log n)

---

### `std::upper_bound()`

Returns first element **> target**.

```cpp
auto it = upper_bound(
    v.begin(), v.end(), 4
);
```

Returns position after last `4`.

**Time Complexity:** O(log n)

---

### `std::equal_range()`

Returns both lower and upper bounds.

```cpp
auto p = equal_range(
    v.begin(), v.end(), 4
);

cout << p.first - v.begin();
cout << p.second - v.begin();
```

**Time Complexity:** O(log n)

---

# DSA Interview Essentials

You should memorize these first:

| Algorithm       | Complexity |
| --------------- | ---------- |
| sort()          | O(n log n) |
| find()          | O(n)       |
| count()         | O(n)       |
| reverse()       | O(n)       |
| binary_search() | O(log n)   |
| lower_bound()   | O(log n)   |
| upper_bound()   | O(log n)   |
| min_element()   | O(n)       |
| max_element()   | O(n)       |
| unique()        | O(n)       |

For LeetCode and DSA, the most frequently used STL algorithms are:

1. `sort()`
2. `reverse()`
3. `find()`
4. `count()`
5. `binary_search()`
6. `lower_bound()`
7. `upper_bound()`
8. `min_element()`
9. `max_element()`
10. `unique()`

Master these 10 before learning the rest.
