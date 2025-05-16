# Rust
- [The Book](https://doc.rust-lang.org/book/title-page.html)
    - [Keywords](https://doc.rust-lang.org/book/appendix-01-keywords.html)
    - [Operators and Symbols](https://doc.rust-lang.org/stable/book/appendix-02-operators.html)
    - [Dev Tools](https://doc.rust-lang.org/book/appendix-04-useful-development-tools.html)
- [Standard Library](https://doc.rust-lang.org/std/)

## Guidelines / Best Practice
- [API Guidelines](https://rust-lang.github.io/api-guidelines/)

## Useful Macros
```rust
// The print line macro for writing to STDOUT
!println("The value of x is {x}");
!println("The value of x is {}", x);

// The debug macro, !dbg writes out to STDERR and it includes 
// the file and line number where the !dbg invocation was made
!dbg(x);
```

## Comments
```rust
// Single line comment
```
```rust
/// Documentation comment. They also support markdown notation
/// # Heading 1
/// ```
/// let one = 1;
/// ```
```

## Variables
#### Declaration
Declare variables with the `let` keyword. By default variable binding are immutable.
```rust
let     x: i32 = 42;    // immutable binding
let mut x: i32 = 42;    // mutable binding
```
Const keyword

#### Shadowing
Variables can be _shadowed_, which allows reuse of variable names in the same scope
```rust
```

### Numerics
#### Declaration
The Rust compiler can infer what type a variable is
```rust
let x: i32 = 10;
let y: f64 = 2.17;
```

Or you can Use suffixes for explicit initialization of numerics
```rust
let i: i32 = 42i32;     // i = 42
let f: f64 = 3.14f64;   // f = 3.14
```

### Compound Types
- Tuples
- Arrays

### Strings

## Control Flow
- `match`: a control flow construct to compare values against a series of patterns. it is somewhat like a more powerful and complex `switch` statement in C.
    ```rust
    enum Coin {
		Penny,
		Nickel,
		Dime,
		Quarter,
    }

    fn value_in_cents(coin: Coin) -> u8 {
		match coin {
		    Coin::Penny => 1,
		    Coin::Nickel => 5,
		    Coin::Dime => 10,
		    Coin::Quarter => 25,
		}
    }
    ```
- `if let`: acts as a less verbose way to handle match patterns
    - Note that the `if let` construct does not perform exhaustive checking like a `match` statement
    - `if let` is basically syntactic sugar for a `match` that ignores all other values
    ```rust
    let config_max = Some(3u8);
    if let Some(max) = config_max {
        println!("The maximum is configured to be {}", max);
    }
    ```

- Looping
```rust
// loop
fn main() {
    let mut counter = 0;
    let result = loop {
	counter += 1;

	if counter == 10 {
	    break counter * 2;
	}
    };

    println!("The result is {result}");
}

// while

// while let

// for in

// loop labels for disambiguation between loops

// Using `enumerate` over for loop
```


## Functions
```rust
// Returns are implicit with no semicolon on the last line
fn multiply(x: i32, y: i32) -> i32 {
    x * y
}

// You can also use an explicit `return` statement
fn multiply(x: i32, y:i32) -> i32 {
    return x * y;
}
```

The conventional style for function names in rust is _snake case_.
```rust
fn hello_world() {
    println!("Hello World!");
}
```


## Scoping
- Curly braces `{}`
- The `use` keyword
- `local` keyword
- `static` lifetime

### Non-Lexical Lifetimes (NLL)


## Memory Management
### Ownership
Ownership refers to the set of rules used by Rust to ensure safety during memory management. 

### References and Borrowing
A _reference_ is specified with the ampersand (`&`).
_Dereferencing_ is done with the asterisk (`*`)
```rust
fn main() {
    let s1 = String::from("hello");
    let len = calculate_length(&s1); // calculate length with borrowed s1
    println!("The length of '{}' is {}.", s1, len);
}
```
Rust allows for as many unmutable (default) references to a variable as  you want. However, you can only have a single _mutable_ reference to a variable.
 
### Slices
#### String Slices
```rust
let s = String::from("hello");
let slice = &s[0..2]; 	// slice from index 0 with length of 2
let slice = &s[..2];	// same as above
let slice = &s[2..];	// slice from index 2 to end of string
let slice = &s[..];		// slice of entire string
```
Be wary of mutibyte UTF-8 characters. See [Storing UTF-8 Encoded Text with Strings](https://doc.rust-lang.org/book/ch08-02-strings.html#storing-utf-8-encoded-text-with-strings)

#### Collection Slices
```rust
let a = [1, 2, 3, 4, 5];
let slice = &a[1..3];
assert_eq!(slice, &[2, 3]);
```

## Data Structures
### Enums
```rust
#[derive(Debug, PartialEq, Copy, Clone)]
pub enum VideoGameGenre {
	FPS,
	MOBA,
	Platformer,
	Metroidvania,
	RPG,
}
```

### Structs
#### Declaration
```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```
Struct update syntax allows the remaining, unspecified fields of a new instantiation to be filled in by the values of another. The following example 
```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}

fn main() {
    // --snip--

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```
#### [Update Syntax](https://doc.rust-lang.org/book/ch05-01-defining-structs.html#creating-instances-from-other-instances-with-struct-update-syntax)
#### Useful Articles / Docs
- [self Keyword](https://doc.rust-lang.org/std/keyword.self.html)
- [Mutable References To 'self' In Rust's Objecdt Methods](https://oswalt.dev/2020/05/mutable-references-to-self-in-rusts-object-methods/)

#### Tuple structs 
```rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);

fn main() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
}
```

### Associated Function
An associated function refers to any function defined withing an `impl`. These functions can be methods or non-methods. 
- Methods include `self` as the first parameter. Methods are accessed `.` 
- Non-methods do not require a `self`. Non-methods are accessed with `::`
#### Methods
Use the `impl` keyword to define methods on `structs`. A method must have a either `self`, `&self`, or `&mut self` as it's first parameter.
```rust
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        rect1.area()
    );
}
```

### Collections
#### Vec and !vec

## Error Handling
### Result Type
```rust
```

## Generics
### Traits
#### Traits as Parameters
#### Traits Bounds
- Compound trait bounds with `+`
- `where` clause
    ```
    fn some_function<T, U>(t: &T, u: &U) -> i32
	where T: Display + Clone,
	      U: Clone + Debug
    {
    ```
### Lifetimes
#### Lifetime Annotation Syntax
```rust
&i32        // a reference
&'a i32     // a reference with an explicit lifetime
&'a mut i32 // a mutable reference with an explicit lifetime

fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

#### Lifetime Ellision Rules
#### The Static Lifetime

```

## Attributes


### [panic!](https://doc.rust-lang.org/book/ch09-03-to-panic-or-not-to-panic.html)



## Compilation / Building
### Cargo
- Run `cargo doc --open` from the project directory to open a local webpage listing docs for all the project's dependencies listed in `Cargo.toml`
### rustc
- Use `rustc file.rs` to compile a rust binary

### rustup

## [Paths](https://doc.rust-lang.org/book/ch07-03-paths-for-referring-to-an-item-in-the-module-tree.html) / [using modules](https://doc.rust-lang.org/book/ch07-02-defining-modules-to-control-scope-and-privacy.html)
- The [`pub` keyword](https://doc.rust-lang.org/book/ch07-03-paths-for-referring-to-an-item-in-the-module-tree.html#exposing-paths-with-the-pub-keyword)

## Packages and Crates
- _Packages_: one or more _crates_ that provide functionality. A package contains a `Cargo.toml` files that describes how to build the crates.
- _Crates_ 
    - Binary crate: programs that can be compiled into an executable, must have a `main` functions
    - Library crate: defines functions to be shared to other projects, does __NOT__ have a `main` function
- A package can contain at most one library crate. It can contain as many binary crates as you’d like, but it must contain at least one crate (either library or binary).
    - Use `cargo new <dir>` to create a new crate (library crate by default) in the `dir` directory
    - Specify a binary crate with `cargo new <dir> --bin`
