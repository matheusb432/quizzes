# 01 Solutions

## Question 1

Is TypeScript interpreted or compiled? Give a brief explanation.

### Answer

TypeScript is compiled. TypeScript is a superset of JavaScript, so it needs to be compiled to JavaScript before it can be interpreted by the browser or Node.js.

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

### Answer

`x = 1, y = 4`

`x` is scoped to the function `foo`, so the previous `x` is used in the `console.log` statement. `y` is scoped to the global scope, so it's value is changed by the `foo` function.

## Question 3

What are the differences between `let`, `const`, and `var`?

### Answer

`let` and `const` are _block scoped_, while `var` is _function scoped_. `let` and `var` can be reassigned, while `const` cannot. `const` must be initialized at declaration, while `let` and `var` can be initialized later.

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

### Answer

`21`, The first `x` to be logged is the one scoped in the `if` block, which is discarded after the block ends. The second `x` to be logged is the one scoped to the `foo` function.

## Question 5

In general, when should you prefer `let` over `const`? And `var` over `const`?

- [x] a. **`let` should be used when it's necessary to reassign a variable, while `const` should be the default choice. `var` should be used when you need to declare a variable in the function scope.**
- [ ] b. `let` and `var` should be used when it's necessary to reassign a variable, while `const` should be the default choice.  
- [ ] c. `const` should be used when performance is critical, while `let` should be the default choice. `var` should be used when you need to declare a variable in the function scope.
- [ ] d. `const` should be used for compile-time constants, while `let` should be the default choice. `var` should be used when you need to declare a variable in the function scope.

### Answer

`let` should be used when it's necessary to reassign a variable, while `const` should be the default choice. `var` should be used when you need to declare a variable in the function scope, however, it should be avoided.

`let` and `var` should NOT be used interchangeably, `var` should be avoided in favor of `let` since it's more restrictive and less error prone due to scope issues.

`const` has no performance benefits over `var`, and only a slight, often insignificant, performance benefit over `let`, it's primary purpose is to prevent reassignment of variables.

There is no such thing as a compile-time constant in TypeScript or JavaScript, the V8 engine can often optimize `const` variables to be fast enough, but there's no built-in way to declare a compile-time constant as there is in other languages.
