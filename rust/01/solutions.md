# 01 Solutions

## Question 1

Does this code compile? If it does, what is it's output?

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;
    println!("{}", s1);
}
```

### Answer

This code **DOES NOT** compile, since ownership of s1 is moved to s2, trying to use s1 will cause a compile-time error.

## Question 2

What is the most idiomatic way to fix this code?

```rust
fn print_str(s: String) {
    println!("{}", s);
}

fn main() {
    let s = String::from("world");
    print_str(s);
    println!("{}", s);
}
```

- [ ] a. Add s.clone() before passing to take_ownership
- [ ] b. Change String to &String in the function signature
- [x] c. **Change String to &str in the function signature**
- [ ] d. Change String to str in the function signature

### Answer

Cloning the string will work, but it's inefficient and unnecessary.

The `&String` type incurs a runtime cost to dereference the pointer to the `String` on the heap, due to double indirection.

`&str` is a reference to a string slice, which is a pointer to the slice on the heap. Further, since `String` implements the `Deref<Target = str>`, it can be coerced into a `&str` without any runtime cost.

The `str` type does not have a known memory size since it is a dynamically sized type, so using it as the parameter type would not compile.

## Question 3

Does this code compile? If it does, what is it's output?

```rust
fn main() {
    let mut s = String::from("hello");
    s.push_str(", world");
    let t = s;
    println!("{}", t);
}
```

### Answer

The code **DOES** compile, and it's output is:

```rust
"hello, world"
```

## Question 4

What's the lifetime of `r` in this code snippet?

```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

fn main() {
    let s1 = String::from("long string is long");
    let s2 = "xyz";
    let r = longest(&s1, s2);
}
```

- [ ] a. The entire scope of main
- [x] b. **The lifetime of the shorter of s1 and s2**
- [ ] c. The lifetime of the longer of s1 and s2
- [ ] d. This code doesn't compile

### Answer

The `r` string slice reference will only be valid as long as both s1 and s2 are valid, since the compiler can't infer which one is shorter at compile time, any one of these references becoming invalid could lead to _UB_ if `r` were to be used after that.

## Question 5

Does this code compile? If it does, what is it's output?

```rust
fn main() {
    let s = String::from("hello");
    let r1 = &s;
    let r2 = &s;
    let r3 = &mut s;
    println!("{}, {}", r1, r2);
}
```

### Answer

This code **DOES NOT** compile, since the `r3` mutable borrow is live, using `r1` or `r2` would be in violation of the borrow checker, as it could lead to _data races_, unpredictable behaviour, and even point to invalid memory in the event of a _reallocation_.
