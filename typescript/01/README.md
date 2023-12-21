# 01 Questions

Difficulty: Easy

Quiz focused on TypeScript's basics.

## Question 1

Is TypeScript interpreted or compiled? Give a brief explanation.

## Question 2

What is the output of this code?

```ts
const x = 1;
var y = 2;

function foo() {
  const x = 3;
  y = 4;
}

foo();
console.log(`x = ${x}, y = ${y}`);
```

## Question 3

What are the differences between `let`, `const`, and `var`?

## Question 4

What is the output of this code?

```ts
function foo() {
  const x = 1;
  if (true) {
    const x = 2;
    console.log(x);
  }
  console.log(x);
}
```

## Question 5

In general, when should you prefer `let` over `const`? And `var` over `const`?

- [ ] a. `let` should be used when it's necessary to reassign a variable, while `const` should be the default choice. `var` should be used when you need to declare a variable in the function scope.
- [ ] b. `let` and `var` can be used interchangeably when it's necessary to reassign a variable, while `const` should be the default choice.  
- [ ] c. `const` should be used when performance is critical, while `let` should be the default choice. `var` should be used when you need to declare a variable in the function scope.
- [ ] d. `const` should be used for compile-time constants, while `let` should be the default choice. `var` should be used when you need to declare a variable in the function scope.
