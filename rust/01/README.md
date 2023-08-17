# 01 Questions

## Question 1

Does this code compile? If it does, what is it's output?

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;
    println!("{}", s1);
}
```

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
- [ ] c. Change String to &str in the function signature
- [ ] d. Change String to str in the function signature

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
- [ ] b. The lifetime of the shorter of s1 and s2
- [ ] c. The lifetime of the longer of s1 and s2
- [ ] d. This code doesn't compile

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
