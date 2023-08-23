# 01 Questions

Difficulty: Hard

Quiz focused on C++'s pass-by-value & pass-by-reference semantics.

To learn more about this, check out the [Compound Types: References and Pointers](https://www.learncpp.com/cpp-tutorial/introduction-to-compound-data-types/) chapter in the learncpp tutorial.

## Question 1

When you pass an argument by value, what gets passed to the function?

```cpp
void foo(int x) {
    x = 5;
}
```

- [ ] a. A copy of the argument
- [ ] b. A reference to the argument
- [ ] c. A pointer to the argument
- [ ] d. The argument itself

## Question 2

What does it mean to pass a variable by reference? How does it affect the original variable inside the function?

## Question 3

Generally speaking, which one is typically more expensive in terms of memory and time: passing by value or passing by reference? Why?

## Question 4

Name a scenario when you'd prefer to pass by value and a scenario when you'd prefer to pass by reference.

## Question 5

What are const references, and why might you use them when passing parameters in a function?

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

## Question 8

Can this function modify the content of 'str'? Why or why not?

```cpp
void foo(const std::string &str) { /* ... */ }
```

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

## Question 10

Can you pass the integer literal `42`, to `foo`? Why or why not? What about passing `42` to `bar`?

```cpp
void foo(int &a) { /* ... */ }
void bar(const int &a) { /* ... */ }
```
