# Basics

- `cargo new 'project name'` for initialising a new project in a ./ folder
  creating ./project_name with cargo.toml,cargo.lock .... . We can also use
  cargo init to initialise a folder as a project.
- All the code shall be in src/ which shall be compiled and executed via `cargo
  run` .
- If we wanted to compile a single file and execute it we can use `rustc file.rs
  && ./file`  .
- There are four primitive datatypes in rust which are "Integers(i8 -> i128,u8
  \-> u128),Floats(f32,f64),Bool,Char"
- Also there are four compound datatypes which are
  "Arrays,Tuples,Slices,Strings(slice strings)"

## Strings vs String Slices(\&str) :

- A `String` stores its text data on the heap. It is growable because it keeps
  track of three things: a pointer to the heap, the length, and the *capacity*
- `\&str` (String slice): An immutable borrow (a view) into string data
- It is a "fat pointer" — it stores a pointer to the start of the slice and the
  length of the slice. Because `\&str` is an immutable reference, it cannot
  modify or grow the underlying string.
