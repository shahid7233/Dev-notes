If you want to master pointers in C++, learn them in this order:

# 1. What is a Pointer?

A pointer is a variable that stores the memory address of another variable.

```cpp
int a = 10;
int* ptr = &a;
```

Memory example:

```text
a = 10

Address of a = 1000

ptr = 1000
```

### Symbols

| Symbol | Meaning                               |
| ------ | ------------------------------------- |
| `&`    | Address of variable                   |
| `*`    | Value stored at address (dereference) |

Example:

```cpp
int a = 10;
int* ptr = &a;

cout << a << endl;      // 10
cout << &a << endl;     // address
cout << ptr << endl;    // same address
cout << *ptr << endl;   // 10
```

---

# 2. Changing Variable Through Pointer

```cpp
int a = 10;
int* ptr = &a;

*ptr = 50;

cout << a; // 50
```

`*ptr` directly accesses the value stored at the address.

---

# 3. Pointer Types

```cpp
int a = 10;
double b = 3.14;
char c = 'A';

int* p1 = &a;
double* p2 = &b;
char* p3 = &c;
```

Pointer type must match variable type.

---

# 4. Null Pointer

Pointer pointing nowhere.

```cpp
int* ptr = nullptr;
```

Good practice:

```cpp
int* ptr = nullptr;
```

instead of

```cpp
int* ptr;
```

---

# 5. Pointer Arithmetic

```cpp
int arr[5] = {10,20,30,40,50};

int* ptr = arr;
```

```cpp
cout << *ptr;      // 10
cout << *(ptr+1);  // 20
cout << *(ptr+2);  // 30
```

When you do:

```cpp
ptr++;
```

it moves to the next integer location automatically.

---

# 6. Array and Pointer Relationship

Array name is the address of the first element.

```cpp
int arr[5] = {10,20,30,40,50};

cout << arr << endl;
cout << &arr[0] << endl;
```

Both are same.

Accessing:

```cpp
cout << arr[2];      // 30
cout << *(arr+2);    // 30
```

Equivalent.

---

# 7. Pointer to Array Elements

```cpp
int arr[5] = {10,20,30,40,50};

int* ptr = arr;
```

Loop:

```cpp
for(int i=0;i<5;i++)
{
    cout << *(ptr+i) << " ";
}
```

Output:

```text
10 20 30 40 50
```

---

# 8. Array of Pointers

This is where many beginners get confused.

```cpp
int a = 10;
int b = 20;
int c = 30;

int* arr[3];
```

Meaning:

```text
arr
├── stores address of a
├── stores address of b
└── stores address of c
```

Assign:

```cpp
arr[0] = &a;
arr[1] = &b;
arr[2] = &c;
```

Access:

```cpp
cout << *arr[0]; // 10
cout << *arr[1]; // 20
cout << *arr[2]; // 30
```

Visualization:

```text
a = 10  address=1000
b = 20  address=2000
c = 30  address=3000

arr[0] -> 1000
arr[1] -> 2000
arr[2] -> 3000
```

---

# 9. Pointer to an Array

Different from array of pointers.

```cpp
int arr[5] = {1,2,3,4,5};

int (*ptr)[5] = &arr;
```

Read it inside-out:

```text
ptr is a pointer
to an array
of 5 integers
```

Access:

```cpp
cout << (*ptr)[0]; // 1
cout << (*ptr)[1]; // 2
```

---

# 10. Difference

### Array of Pointers

```cpp
int* arr[3];
```

```text
arr
├─ pointer
├─ pointer
└─ pointer
```

Each element stores an address.

---

### Pointer to Array

```cpp
int (*ptr)[3];
```

```text
ptr
 |
 v
[10][20][30]
```

One pointer points to the entire array.

---

# 11. Double Pointer

Pointer to pointer.

```cpp
int a = 10;

int* ptr = &a;
int** pptr = &ptr;
```

```cpp
cout << a << endl;       // 10
cout << *ptr << endl;    // 10
cout << **pptr << endl;  // 10
```

Visualization:

```text
a = 10

ptr ----> a

pptr ---> ptr ---> a
```

---

# 12. Dynamic Memory (Important)

Allocate memory at runtime.

```cpp
int* ptr = new int;
```

Store value:

```cpp
*ptr = 100;

cout << *ptr;
```

Free memory:

```cpp
delete ptr;
```

Array:

```cpp
int* arr = new int[5];
```

Release:

```cpp
delete[] arr;
```

---

# 13. Interview-Level Question

```cpp
int arr[] = {10,20,30};

int* ptr = arr;

cout << *ptr++;
```

Output:

```text
10
```

Because:

```cpp
*(ptr++)
```

First prints value at current address, then moves pointer.

---

# Roadmap to Master Pointers

1. Variables and memory addresses
2. Basic pointers (`*`, `&`)
3. Dereferencing
4. Pointer arithmetic
5. Arrays and pointers
6. Array of pointers
7. Pointer to array
8. Double pointers
9. Dynamic memory (`new`, `delete`)
10. Function pointers
11. Smart pointers (`unique_ptr`, `shared_ptr`)
12. Data structures (Linked List, Tree, Graph)

Once you are comfortable with steps 1-9, linked lists become much easier because they are essentially objects connected through pointers.
