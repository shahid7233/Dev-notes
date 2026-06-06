In inheritance, `public`, `protected`, and `private` determine **who can access members** of a class and how they behave after inheritance.

## 1. Public Members

* Accessible inside the class.
* Accessible in derived (child) classes.
* Accessible from outside the class using an object.

```cpp
class Parent {
public:
    int a = 10;
};

class Child : public Parent {
public:
    void show() {
        cout << a;  // Allowed
    }
};

int main() {
    Child c;
    cout << c.a;   // Allowed
}
```

---

## 2. Protected Members

* Accessible inside the class.
* Accessible in derived classes.
* **Not accessible** from outside the class.

```cpp
class Parent {
protected:
    int b = 20;
};

class Child : public Parent {
public:
    void show() {
        cout << b;  // Allowed
    }
};

int main() {
    Child c;
    // cout << c.b;  // Error
}
```

---

## 3. Private Members

* Accessible only inside the class.
* **Not accessible** in derived classes.
* **Not accessible** from outside the class.

```cpp
class Parent {
private:
    int c = 30;
};

class Child : public Parent {
public:
    void show() {
        // cout << c;  // Error
    }
};
```

---

# Effect of Inheritance Type

```cpp
class Parent {
public:
    int a;
protected:
    int b;
private:
    int c;
};
```

### Public Inheritance

```cpp
class Child : public Parent {};
```

| Parent Member | Becomes in Child |
| ------------- | ---------------- |
| public a      | public           |
| protected b   | protected        |
| private c     | Not accessible   |

---

### Protected Inheritance

```cpp
class Child : protected Parent {};
```

| Parent Member | Becomes in Child |
| ------------- | ---------------- |
| public a      | protected        |
| protected b   | protected        |
| private c     | Not accessible   |

---

### Private Inheritance

```cpp
class Child : private Parent {};
```

| Parent Member | Becomes in Child |
| ------------- | ---------------- |
| public a      | private          |
| protected b   | private          |
| private c     | Not accessible   |

---

### Easy Memory Trick

Think of a **house**:

* **Public** = Living room → Everyone can enter.
* **Protected** = Family room → Only family (derived classes) can enter.
* **Private** = Bedroom → Only the owner (same class) can enter.

For interviews, remember:

**Public → Everyone**
**Protected → Class + Derived Classes**
**Private → Class Only**

And **private members are inherited but cannot be accessed directly by the child class.**
