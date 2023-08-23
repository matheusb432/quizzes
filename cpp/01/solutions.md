# 01 Solutions

Difficulty: Hard

Quiz focused on C++'s pass-by-value & pass-by-reference semantics.

## Question 1

When you pass an argument by value, what gets passed to the function?

```cpp
void foo(int x) {
    x = 5;
}
```

- [x] a. A copy of the argument
- [ ] b. A reference to the argument
- [ ] c. A pointer to the argument
- [ ] d. The argument itself

### Answer

A copy of the argument is passed to the function. This means that any changes made to the argument inside the function will not affect the original variable.

## Question 2

What does it mean to pass a variable by reference? How does it affect the original variable inside the function?

### Answer

It passes an alias, or _constant pointer_, to the original variable.

if the variable is an _lvalue reference to non-const_, the original variable can be changed, if it’s an _lvalue reference to const_, it cannot be changed.

## Question 3

Generally speaking, which one is typically more expensive in terms of memory and time: passing by value or passing by reference? Why?

### Answer

Pass by value is generally more expensive for classes and large data types. This is because a copy of the object is made, which can be expensive in terms of memory and time.

## Question 4

Name a scenario when you'd prefer to pass by value and a scenario when you'd prefer to pass by reference.

### Answer

For primitive types (like `int`, `long`, `double`, ...), the overhead of copying the address in memory and dereferencing it is larger than it is to simply copy it. So for small data types in general, pass by value is better.

## Question 5

What are const references, and why might you use them when passing parameters in a function?

### Answer

Const references are references that disallow modifying the object it points to, they should always be used unless changing the value of the underlying reference is the intended function behavior.

## Question 6

```cpp
void foo(int a) { 
    a = 99; 
}
int main() {
  int x = 5;
  foo(x);
  // Q: What is the value of x here?
}
```

### Answer

The value of `x` is still `5`, since `foo` takes the argument by value, it makes a copy of `x` and assigns `99` to it, but the original `x` is not affected.

## Question 7

```cpp
void foo(int &a) { 
    a = 99; 
}
int main() {
  int x = 5;
  foo(x);
  // Q: What is the value of x here?
}
```

### Answer

The value of `x` is `99`, since `foo` takes the argument by reference, it makes an alias to `x` and assigns `99` to it, which affects the original `x`.

## Question 8

Can this function modify the content of 'str'? Why or why not?

```cpp
void foo(const std::string &str) { /* ... */ }
```

### Answer

No, because the function takes a const reference to `str`, which means that the function cannot modify the underlying object.

## Question 9

```cpp
void foo(int &a, int b) { 
    b += 30;
    a = b; 
    b = 0;
}
int main() {
  int x = 10, y = 5;
  foo(x, y);
  // Q: What are the values of x and y here?
}
```

### Answer

The value of `x` is `35` and the value of `y` is `5`, since `foo` takes the first argument by reference, it makes an alias to `x` and assigns `35` to it, which affects the original `x`. The second argument is passed by value, so it makes a copy of `y` and assigns `30` to it, but the original `y` is not affected.

Note that references, unlike pointers, cannot be reassigned, so `a = b` in `foo` is **NOT** reassigning the reference, but rather assigning the _value_ of `b` to the underlying object of `a`.

## Question 10

Can you pass the integer literal `42`, to `foo`? Why or why not? What about passing `42` to `bar`?

```cpp
void foo(int &a) { /* ... */ }
void bar(const int &a) { /* ... */ }
```

### Answer

You can pass `42` to `bar`, but not to `foo`. This is because `foo` takes a non-const reference, which **cannot be bound to an rvalue**, while `bar` takes a const reference, which can be bound to an rvalue.

The compiler can create a temporary variable to hold the value of the rvalue, and bind the const reference to it, since the const reference cannot modify the underlying object, this is safe.
