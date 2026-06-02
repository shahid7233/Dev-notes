# Array + Pointer Quick Revision Sheet

## 1. Basic Pointer

```cpp
int a = 10;
int* ptr = &a;
```

```cpp
a      // 10
&a     // address of a
ptr    // address of a
*ptr   // 10
```

Memory:

```text
ptr ----> a(10)
```

---

## 2. Array

```cpp
int arr[3] = {10,20,30};
```

```cpp
arr      // address of arr[0]
&arr[0]  // same address
arr[0]   // 10
```

Memory:

```text
arr
 |
 v
[10][20][30]
```

---

## 3. Array as Pointer

```cpp
int arr[3] = {10,20,30};
```

```cpp
*arr       // 10
*(arr+1)   // 20
*(arr+2)   // 30
```

Equivalent:

```cpp
arr[0] == *(arr+0)
arr[1] == *(arr+1)
arr[2] == *(arr+2)
```

---

## 4. Pointer to First Element

```cpp
int arr[3] = {10,20,30};

int* ptr = arr;
```

```cpp
ptr       // address of arr[0]
*ptr      // 10
*(ptr+1)  // 20
*(ptr+2)  // 30
```

Memory:

```text
ptr
 |
 v
[10][20][30]
```

---

## 5. Array of Pointers

```cpp
int a = 10;
int b = 20;
int c = 30;

int* arr[3] = {&a,&b,&c};
```

```cpp
arr[0]   // address of a
*arr[0]  // 10

arr[1]   // address of b
*arr[1]  // 20

arr[2]   // address of c
*arr[2]  // 30
```

Memory:

```text
arr
 |
 +--> a(10)
 |
 +--> b(20)
 |
 +--> c(30)
```

**Rule:** Every element is a pointer.

---

## 6. Pointer to Pointer

```cpp
int a = 10;

int* ptr = &a;
int** pptr = &ptr;
```

```cpp
pptr     // address of ptr
*pptr    // address of a
**pptr   // 10
```

Memory:

```text
pptr
 |
 v
ptr
 |
 v
a(10)
```

---

## 7. Pointer to Array

```cpp
int arr[3] = {10,20,30};

int (*ptr)[3] = &arr;
```

```cpp
ptr         // address of whole array
(*ptr)[0]   // 10
(*ptr)[1]   // 20
(*ptr)[2]   // 30
```

Memory:

```text
ptr
 |
 v
[10][20][30]
```

---

# One-Line Summary

```text
int* ptr;
      ↑
      pointer to int

int* arr[3];
      ↑
      array of 3 pointers

int** pptr;
       ↑
       pointer to pointer

int (*ptr)[3];
        ↑
        pointer to array of 3 ints
```

If you can explain these 4 declarations without looking at notes, you already understand about 80% of the pointer questions asked in interviews and DSA courses.
# Array + Pointer Quick Revision Sheet

## 1. Basic Pointer

```cpp
int a = 10;
int* ptr = &a;
```

```cpp
a      // 10
&a     // address of a
ptr    // address of a
*ptr   // 10
```

Memory:

```text
ptr ----> a(10)
```

---

## 2. Array

```cpp
int arr[3] = {10,20,30};
```

```cpp
arr      // address of arr[0]
&arr[0]  // same address
arr[0]   // 10
```

Memory:

```text
arr
 |
 v
[10][20][30]
```

---

## 3. Array as Pointer

```cpp
int arr[3] = {10,20,30};
```

```cpp
*arr       // 10
*(arr+1)   // 20
*(arr+2)   // 30
```

Equivalent:

```cpp
arr[0] == *(arr+0)
arr[1] == *(arr+1)
arr[2] == *(arr+2)
```

---

## 4. Pointer to First Element

```cpp
int arr[3] = {10,20,30};

int* ptr = arr;
```

```cpp
ptr       // address of arr[0]
*ptr      // 10
*(ptr+1)  // 20
*(ptr+2)  // 30
```

Memory:

```text
ptr
 |
 v
[10][20][30]
```

---

## 5. Array of Pointers

```cpp
int a = 10;
int b = 20;
int c = 30;

int* arr[3] = {&a,&b,&c};
```

```cpp
arr[0]   // address of a
*arr[0]  // 10

arr[1]   // address of b
*arr[1]  // 20

arr[2]   // address of c
*arr[2]  // 30
```

Memory:

```text
arr
 |
 +--> a(10)
 |
 +--> b(20)
 |
 +--> c(30)
```

**Rule:** Every element is a pointer.

---

## 6. Pointer to Pointer

```cpp
int a = 10;

int* ptr = &a;
int** pptr = &ptr;
```

```cpp
pptr     // address of ptr
*pptr    // address of a
**pptr   // 10
```

Memory:

```text
pptr
 |
 v
ptr
 |
 v
a(10)
```

---

## 7. Pointer to Array

```cpp
int arr[3] = {10,20,30};

int (*ptr)[3] = &arr;
```

```cpp
ptr         // address of whole array
(*ptr)[0]   // 10
(*ptr)[1]   // 20
(*ptr)[2]   // 30
```

Memory:

```text
ptr
 |
 v
[10][20][30]
```

---

# One-Line Summary

```text
int* ptr;
      ↑
      pointer to int

int* arr[3];
      ↑
      array of 3 pointers

int** pptr;
       ↑
       pointer to pointer

int (*ptr)[3];
        ↑
        pointer to array of 3 ints
```

