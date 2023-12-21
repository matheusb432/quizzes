# Legend & Concepts

- _UB_ - Undefined Behaviour
- _Data races_ - When two or more pointers access the same memory location at the same time, and at least one of them is writing to that location, leading to _UB_.
- _Reallocation_ - When a dynamic array's (e.g. `Vec<T>`, `String`) capacity is exceeded, it's contents are copied to a new location in memory with a larger capacity, and the old memory is freed, invalidating any references to the old memory location.
