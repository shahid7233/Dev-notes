int a = 10;
int* ptr = &a;

cout << a << endl;      // 10
cout << &a << endl;     // address
cout << ptr << endl;    // same address
cout << *ptr << endl;   // 10

```cpp
// =============================
// 1. BASIC POINTER
// =============================

int a = 10;
int* ptr = &a;

a;      // 10
&a;     // address of a
ptr;    // address of a
*ptr;   // 10

/*
Memory:

ptr ----> a(10)
*/


// =============================
// 2. ARRAY
// =============================

int arr[3] = {10,20,30};

arr;      // address of arr[0]
&arr[0];  // same address
arr[0];   // 10

/*
Memory:

arr
 |
 v
[10][20][30]
*/


// =============================
// 3. ARRAY AS POINTER
// =============================

int arr[3] = {10,20,30};

*arr;       // 10
*(arr+1);   // 20
*(arr+2);   // 30

/*
Equivalent:

arr[0] == *(arr+0)
arr[1] == *(arr+1)
arr[2] == *(arr+2)
*/


// =============================
// 4. POINTER TO FIRST ELEMENT
// =============================

int arr[3] = {10,20,30};

int* ptr = arr;

ptr;       // address of arr[0]
*ptr;      // 10
*(ptr+1);  // 20
*(ptr+2);  // 30

/*
Memory:

ptr
 |
 v
[10][20][30]
*/


// =============================
// 5. ARRAY OF POINTERS
// =============================

int a = 10;
int b = 20;
int c = 30;

int* arr[3] = {&a,&b,&c};

arr[0];   // address of a
*arr[0];  // 10

arr[1];   // address of b
*arr[1];  // 20

arr[2];   // address of c
*arr[2];  // 30

/*
Memory:

arr
 |
 +--> a(10)
 |
 +--> b(20)
 |
 +--> c(30)

Rule:
Every element is a pointer.
*/


// =============================
// 6. POINTER TO POINTER
// =============================

int a = 10;

int* ptr = &a;
int** pptr = &ptr;

pptr;     // address of ptr
*pptr;    // address of a
**pptr;   // 10

/*
Memory:

pptr
 |
 v
ptr
 |
 v
a(10)
*/


// =============================
// 7. POINTER TO ARRAY
// =============================

int arr[3] = {10,20,30};

int (*ptr)[3] = &arr;

ptr;         // address of whole array
(*ptr)[0];   // 10
(*ptr)[1];   // 20
(*ptr)[2];   // 30

/*
Memory:

ptr
 |
 v
[10][20][30]
*/


// =============================
// MOST IMPORTANT DECLARATIONS
// =============================

int* ptr;
// pointer to int

int* arr[3];
// array of 3 pointers

int** pptr;
// pointer to pointer

int (*ptr)[3];
// pointer to array of 3 ints
```
