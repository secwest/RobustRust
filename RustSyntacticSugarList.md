Rust Syntactic Sugar

(Robust Rust)

Dragos Ruiu (2023 May 1)

Here's a list of shorthand notations, shortcuts, and other syntactically unusual aspects of Rust, along with explanations and code examples:



1. Field Init Shorthand: `Point { x, y }` instead of `Point { x: x, y: y }`.
2. Destructuring: `let Point { x, y } = point;` or `let (a, b, c) = tuple;`.
3. Match Arms with Identical Expressions: `Message::ChangeColor(0, 0, 0) | Message::Move { x: 0, y: 0 } => println!("Do nothing")`.
4. Method Chaining: `"hello world".to_string().to_uppercase()`.
5. Closure Shorthand: `|&x| x * x` instead of `|x: &i32| -> i32 { *x * *x }`.
6. `?` Operator: `File::open("file.txt")?` instead of explicit error handling with `match`.
7. Turbofish Operator: `x.parse::&lt;i32>()` when type inference is not possible.
8. Underscores in Numeric Literals: `1_000_000` for better readability.
9. Type Aliases: `type Kilometers = i32;` for code clarity.
10. Associated Constants: `const PI: f64` inside a trait or struct.
11. Inclusive Range: `1..=5` includes both 1 and 5.
12. Range Expression: `0..5` for loop iteration or slicing.
13. Lazy Static: `lazy_static! { static ref VAR: Type = value; }` for lazily initialized static variables.
14. Module-level Constants: `const CONST_NAME: Type = value;`.
15. Wildcard Import: `use some_module::*;` to import all items from a module.
16. Lifetime Elision: Omitting lifetime parameters when the compiler can infer them.
17. Immutable References: `&T` for shared, immutable references.
18. Mutable References: `&mut T` for exclusive, mutable references.
19. Reference Operator: `&` for creating a reference to a value.
20. Dereference Operator: `*` for accessing the value behind a reference.
21. Ownership Transfer: `let x = y;` moves ownership of `y` to `x`.
22. Borrowing: `&y` to create a shared reference without transferring ownership.
1. Impl Trait: `fn return_iterator() -> impl Iterator&lt;Item = i32>` for returning an anonymous type that implements a specific trait.
2. Extern Crate: `extern crate my_crate;` for including external crates in Rust 2015 edition (not required in Rust 2018 edition and later).
3. Macro Invocation: `println!("Hello, world!");` invoking a macro with a `!` at the end.
4. Attribute Macros: `#[derive(Debug)]` for automatically implementing traits or other code-generation tasks.
5. Module Declaration: `mod my_module;` for declaring a module in a separate file.
6. Nested Module Declaration: `mod inner { ... }` for declaring a nested module within the same file.
7. Visibility Modifiers: `pub` keyword for making items public, and `pub(crate)` for making items visible only within the current crate.
8. Struct Update Syntax: `Point { x: 3, ..point }` for creating a new struct instance while reusing the values from an existing instance.
9. Or Patterns: `Some(0) | Some(1)` in pattern matching to match against multiple patterns.
10. If Let: `if let Some(x) = option { ... }` for concise single pattern matching.
11. While Let: `while let Some(x) = iterator.next() { ... }` for loop iteration with single pattern matching.
12. Function Pointer: `fn add(x: i32, y: i32) -> i32;` for specifying a function as a value.
13. AsRef and AsMut: `as_ref()` and `as_mut()` for converting a value into a reference or mutable reference of a different type.
14. Try Blocks: `try { ... }` for a block returning a `Result`, available in nightly Rust builds.
15. Associated Types: `type Output;` within a trait, for specifying a type that is associated with the implementing type.
16. Default Trait Implementations: `fn method(&self) -> Type { ... }` within a trait, for providing default implementations that can be overridden by implementers.
17. Trait Bounds: `T: Trait` in generic function signatures, for constraining the generic types to implement specific traits.
18. Higher-Ranked Trait Bounds: `for&lt;'a> T: Trait&lt;'a>` for constraining a generic type to implement a trait with an associated lifetime.
19. Lifetime Annotations: `'a` for explicitly specifying lifetimes of references in structs, functions, and traits.
20. Static Lifetimes: `'static` for references with the longest possible lifetime, living for the entire duration of the program.
1. Range Syntax: `a..b` for creating a range of values between `a` and `b`.
2. Inclusive Range Syntax: `a..=b` for creating an inclusive range, including both `a` and `b`.
3. Array and Slice Pattern: `[a, b, .., y, z]` for destructuring arrays or slices.
4. Field Init Shorthand: `Foo { a, b }` for initializing a struct's fields with the same name as the variables.
5. C-style Enum: `enum Enum { A, B, C }` for declaring a C-style enumeration.
6. Use Renaming: `use std::io::Result as IoResult;` for renaming an imported item.
7. Type Alias: `type MyResult&lt;T> = Result&lt;T, MyError>;` for creating an alias for a type.
8. Raw Pointers: `*const T` and `*mut T` for raw (unsafe) pointers.
9. Repeat Expression: `[0; 5]` for creating an array with repeated values.
10. String Literal Concatenation: `"Hello, " "world!"` for concatenating adjacent string literals.
11. Unreachable Code: `unreachable!()` macro for marking a code location as unreachable.
12. Underscore in Numeric Literals: `1_000_000` for improving readability in large numeric literals.
13. Dereference Operator: `*x` for dereferencing a reference or pointer.
14. Raw Identifier: `r#type` for using reserved keywords as identifiers.
15. Loop Labels: `'label: loop { ... }` for labeling loops, and `break 'label;` or `continue 'label;` for breaking or continuing labeled loops.
16. Async Functions: `async fn foo() -> Result&lt;(), ()> { ... }` for declaring asynchronous functions.
17. Pin: `std::pin::Pin` for creating a pinned reference, which ensures the memory it points to will not be moved.
18. Unsized Types: `T: ?Sized` trait bound for allowing generic types to be unsized.
1. Zero-sized types: `struct Zst;` for declaring a zero-sized type (ZST) that occupies no memory.
2. Constant Function: `const fn foo() { ... }` for declaring a function that can be evaluated at compile-time.
3. Associated Constants: `const VALUE: i32 = 42;` for defining associated constants within trait or struct implementations.
4. Or-patterns: `Some(0) | Some(1) | Some(2)` for matching multiple patterns in a single arm.
5. Anonymous Lifetime: `'_` for specifying an anonymous lifetime parameter.
6. Boxed trait objects: `Box&lt;dyn Trait>` for creating a boxed trait object, which can hold any type that implements the trait.
7. Dereference coercion: Automatically dereferencing a reference to a reference, e.g., `&String` to `&str`.
8. Diverging type: `!` for specifying a diverging type, which indicates that the function does not return.
9. Module shorthand: `mod.rs` for defining a module in a separate file.
10. Eager macro expansion: `macro_rules! foo { ... }` for defining macros that are eagerly expanded during parsing.
11. Lazy macro expansion: `proc_macro! { ... }` for defining procedural macros that are expanded during code generation.
12. Type ascription: `let x: Type = expr;` for annotating the type of a variable explicitly.
13. Extern crate: `extern crate foo;` for explicitly linking an external crate.
14. NLL (Non-Lexical Lifetimes): More precise lifetime analysis, reducing restrictions on borrowing.
1. Field init shorthand: When initializing a struct, if a variable with the same name as a field is in scope, you can use the shorthand `fieldname` instead of `fieldname: fieldname`.
2. Inclusive Ranges: `1..=3` for creating an inclusive range that includes the end value.
3. Byte string literals: `b"Hello, world!"` for creating a byte string literal (an array of `u8` values).
4. Raw string literals: `r#"..."#` for creating a raw string literal, which does not process escape characters.
5. Doc comments: `///` and `//!` for creating documentation comments that are processed by the Rust documentation tool (rustdoc).
6. Macro reexport: `#[macro_export]` for making a macro available to other crates when the module is used.
7. Global allocator: `#[global_allocator]` for specifying a custom global memory allocator for a Rust program.
8. Auto traits: Automatically implementing a trait for types that meet certain criteria, such as `Send` and `Sync`.
9. Scoped attributes: `#[attr]` for applying an attribute to an item in a limited scope.
10. Custom derive: `#[derive(MyTrait)]` for implementing custom derive macros that generate trait implementations.
11. Nested imports: `use std::{fs, io};` for importing multiple items from the same path in a single `use` statement.
12. Underscore in numeric literals: `1_000_000` for improving readability in numeric literals.
13. Extern types: `extern type Foo;` for declaring an opaque type with an unknown size and alignment.
14. Binding modes: `ref` and `ref mut` for binding to a reference or mutable reference in pattern matching.
1. Try blocks: `try { ... }` for using the `?` operator within the block and propagating errors to the enclosing scope (experimental feature).
2. Negative implementations: `impl !Trait for Type` for specifying that a given type does not implement a particular trait.
3. Array concatenation: `[a; N]` for creating an array of length `N` with all elements set to `a`.
4. Array repeating: `[a; N]` for creating an array of length `N` with all elements set to `a`.
5. Scoped lint attributes: `#[allow(clippy::lint_name)]` for allowing or disallowing specific lints within a limited scope.
6. Lazy static: `lazy_static! { ... }` for declaring lazily initialized static values (provided by the `lazy_static` crate).
7. Associated consts: `const NAME: Type = value;` for declaring associated constants within a trait or implementation block.
8. Existential types: `existential type Foo: Trait;` for declaring a type alias for an opaque type that implements a given trait (experimental feature).
9. Struct update syntax: `..base` for creating a new struct with some fields updated from an existing struct.
10. Or patterns: `A | B` for matching on multiple patterns in a single arm of a `match` or `if let` expression.
11. Const generics: `struct Foo&lt;const N: usize> { ... }` for defining generic parameters with constant values (experimental feature).
12. Inline attributes: `#[inline]` and `#[inline(always)]` for suggesting that a function be inlined by the compiler.
1. Trait objects: `Box&lt;dyn Trait>` for creating a trait object, which is a dynamically dispatched, heap-allocated object implementing a specific trait.
2. Automatic dereferencing: Rust automatically dereferences references and smart pointers when calling methods, so you don't need to explicitly dereference them using `*`.
3. Range patterns: `a..=b` for matching a range of values inclusively within a `match` expression.
4. Nested import groups: `use foo::{bar, baz::{qux, quux}};` for importing multiple items from the same module in a more concise way.
5. Enum variant aliases: `type Alias = Enum::Variant;` for creating a type alias for a specific enum variant.
6. Destructuring assignment: `let (a, b) = (1, 2);` for unpacking a tuple or struct into individual variables.
7. "turbofish" for const generics: `foo::&lt;{ value }>()` for specifying const generic parameters (similar to the turbofish operator for type generics).
8. Nested functions: Rust allows you to define functions inside other functions, which can help with organizing code and encapsulating logic.
1. Visibility shortcut: `pub(crate)` or `pub(super)` can be used to specify the visibility of an item within a crate or its parent module, respectively.
2. Inline assembly: Rust provides support for inline assembly through the `asm!` macro, which enables you to include assembly language code directly in your Rust program for highly optimized or low-level operations.
3. "or patterns": You can match multiple patterns in a single arm of a `match` expression using the `|` operator, e.g., `Some(x) | Some(y)` matches `Some(x)` or `Some(y)`.
4. Non-exhaustive enums: You can mark an enum as non-exhaustive with the `#[non_exhaustive]` attribute. This signals to users of the API that the enum may have additional variants in the future, so they should include a catch-all `_` match arm when pattern matching.
5. Pinning: The `Pin` type is used to express that the memory address of a value should not change, which can be useful when working with self-referential types or certain async contexts.
6. Async closure: The `async` keyword can be used with closures to create asynchronous closures, although they are currently unstable and available only in nightly Rust.
1. Type-level integers: Rust supports type-level integers through the `typenum` crate, which allows you to create types with integers as type parameters. This can enable type-level programming techniques and compile-time computations.
2. Wrapping arithmetic: Rust provides the `Wrapping` type, which performs arithmetic operations that "wrap" on overflow or underflow, useful in certain low-level or cryptographic applications.
3. Uninhabited types: Rust has a special type called `!`, which represents an uninhabited type. It is used to indicate that a function never returns, such as a function that calls `std::process::exit` or enters an infinite loop.
4. Multidispatch: Rust supports limited multiple dispatch through traits and trait objects. This allows for more dynamic method resolution at runtime, depending on the actual types of the involved objects.
5. Custom dereference coercions: Implementing the `Deref` and `DerefMut` traits allows you to create custom dereference coercions for your types, effectively providing a way to overload the `*` operator.
1. Safe transmutes: The `safe-transmute` crate allows you to safely transmute one type to another, ensuring that the conversion is valid and well-defined, unlike the unsafe `std::mem::transmute` function.
2. Const generics: As of Rust 1.51, const generics allow you to parameterize types over constant values, enabling more expressive and powerful generic programming techniques.
3. Associated consts: You can define associated constants in traits, which allow you to provide constant values that are associated with a trait implementation for a specific type.
4. Unsafe traits: You can mark a trait as `unsafe`, which indicates that implementing the trait requires adhering to certain invariants that the Rust compiler cannot enforce. This feature is useful for creating abstractions over low-level or unsafe operations.
1. Diverging functions: Functions that never return have a special return type `!`, which is called the "never" type. This can be useful in cases where the function panics or enters an infinite loop.
2. Function pointers: Rust supports function pointers, which allow you to store references to functions and use them as arguments or return values. The syntax for a function pointer is `fn(ArgumentTypes) -> ReturnType`.
3. Custom allocators: Rust allows you to use custom memory allocators instead of the default global allocator. To do this, you can implement the `std::alloc::GlobalAlloc` trait and use the `#[global_allocator]` attribute to specify your custom allocator.
4. Macros: Rust has a powerful macro system that allows you to create reusable chunks of code using a concise syntax. Macros in Rust use the `macro_rules!` keyword to define patterns and expansions.
5. Custom derive: Rust allows you to implement custom derive macros, which can automatically generate trait implementations for your types based on the structure and fields of the type.
1. Attributes: Rust attributes are metadata applied to modules, items, or expressions. Attributes are denoted by a `#[]` or `#![]` syntax (the latter is used for inner attributes). Attributes can be used for various purposes, such as conditional compilation, customizing derives, or specifying test functions.

Field Init Shorthand

When initializing a struct, if the variable names match the field names, you can use the field init shorthand:


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let x = 3;
    let y = 4;

    let point = Point { x, y }; // Equivalent to `Point { x: x, y: y }`
    println!("({}, {})", point.x, point.y);
}
```


Destructuring and Pattern Matching

You can destructure structs, tuples, and enums using pattern matching:


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let point = Point { x: 3, y: 4 };

    let Point { x, y } = point;
    println!("({}, {})", x, y);

    let tuple = (1, 2, 3);
    let (a, b, c) = tuple;
    println!("{}, {}, {}", a, b, c);
}
```


Match Arms with Identical Expressions

If multiple match arms have the same expression, you can use a pipe (`|`) to simplify the code:


```
enum Message {
    Quit,
    ChangeColor(u8, u8, u8),
    Move { x: i32, y: i32 },
}

fn process_message(msg: Message) {
    match msg {
        Message::Quit => println!("Quit"),
        Message::ChangeColor(0, 0, 0) | Message::Move { x: 0, y: 0 } => println!("Do nothing"),
        _ => println!("Do something"),
    }
}
```


Method Chaining

You can chain methods using the dot (`.`) operator:


```
fn main() {
    let s = "hello world".to_string().to_uppercase();
    println!("{}", s);
}
```


Closure Shorthand

When using closures, you can use the shorthand notation for parameters and their types:


```
fn main() {
    let numbers = vec![1, 2, 3, 4, 5];
    let squares: Vec<i32> = numbers.iter().map(|&x| x * x).collect();
    println!("{:?}", squares);
}
```




? Operator

The `?` operator is a shorthand for error handling, returning the error early if a result is an `Err` variant:


```
use std::fs::File;

fn main() -> Result<(), std::io::Error> {
    let file = File::open("file.txt")?;
    Ok(())
}
```


Turbofish Operator

The turbofish operator (`::&lt;>`) is used to specify generic type parameters when the type cannot be inferred:


```
fn main() {
    let nums = vec!["1", "2", "3"];
    let nums: Vec<i32> = nums.into_iter().map(|x| x.parse::<i32>().unwrap()).collect();
    println!("{:?}", nums);
}
```


Underscores in Numeric Literals:


```
let million = 1_000_000;
println!("One million is written as: {}", million);
```


Type Aliases:


```
type Kilometers = i32;

fn distance_in_km(distance: Kilometers) {
    println!("The distance is {} kilometers", distance);
}

let km: Kilometers = 42;
distance_in_km(km);
```


Associated Constants:


```
struct Circle {
    radius: f64,
}

impl Circle {
    const PI: f64 = 3.141592653589793;

    fn area(&self) -> f64 {
        self.radius * self.radius * Self::PI
    }
}

let circle = Circle { radius: 5.0 };
println!("The area of the circle is: {}", circle.area());
```


Inclusive Range:


```
for i in 1..=5 {
    print!("{} ", i);
}
```


Range Expression:


```
for i in 0..5 {
    print!("{} ", i);
}

let arr = [1, 2, 3, 4, 5];
let slice = &arr[1..4];
```


Lazy Static:


```
use lazy_static::lazy_static;
use std::collections::HashMap;

lazy_static! {
    static ref FRUITS: HashMap<&'static str, u32> = {
        let mut map = HashMap::new();
        map.insert("apple", 5);
        map.insert("banana", 3);
        map.insert("orange", 2);
        map
    };
}

fn main() {
    let count = FRUITS.get("apple").unwrap();
    println!("There are {} apples", count);
}

count); }
```


Module-level Constants:


```
const MAX_SIZE: usize = 100;

fn main() {
    let mut array = [0; MAX_SIZE];
    array[0] = 42;
    println!("The first element of the array is: {}", array[0]);
}
```


Wildcard Import:


```
mod some_module {
    pub fn function_one() {
        println!("Function one");
    }

    pub fn function_two() {
        println!("Function two");
    }
}

use some_module::*;

fn main() {
    function_one();
    function_two();
}
```


Lifetime Elision:


```
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

fn main() {
    let s1 = String::from("short");
    let s2 = String::from("longer");

    let res = longest(&s1, &s2);
    println!("The longest string is: {}", res);
}
```


Immutable References:


```
fn print_length(s: &String) {
    println!("The length of the string is: {}", s.len());
}

fn main() {
    let s = String::from("Hello, world!");
    print_length(&s);
}
```


Mutable References:


```
fn change(s: &mut String) {
    s.push_str(", world!");
}

fn main() {
    let mut s = String::from("Hello");
    change(&mut s);
    println!("{}", s);
}
```


Reference Operator:


```
fn main() {
    let x = 42;
    let y = &x;
    println!("The value of y is: {}", y);
}
```


Dereference Operator:


```
fn main() {
    let x = 42;
    let y = &x;
    let z = *y;
    println!("The value of z is: {}", z);
}

}
```


Ownership Transfer:


```
fn main() {
    let x = String::from("hello");
    let y = x;
    println!("The value of y is: {}", y);
}
```


Borrowing:


```
fn print_length(s: &String) {
    println!("The length of the string is: {}", s.len());
}

fn main() {
    let s = String::from("Hello, world!");
    print_length(&s);
}
```


Impl Trait:


```
fn evens() -> impl Iterator<Item = i32> {
    (0..).step_by(2)
}

fn main() {
    let mut iterator = evens();
    println!("First even number: {}", iterator.next().unwrap());
    println!("Second even number: {}", iterator.next().unwrap());
    println!("Third even number: {}", iterator.next().unwrap());
}
```


Extern Crate (only required in Rust 2015 edition):


```
// Cargo.toml
[dependencies]
rand = "0.8.3"

// main.rs
extern crate rand;

use rand::Rng;

fn main() {
    let random_number = rand::thread_rng().gen_range(1, 101);
    println!("Random number: {}", random_number);
}
```


Macro Invocation:


```
fn main() {
    println!("Hello, world!");
}
```


Attribute Macros:


```
#[derive(Debug)]
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let p = Point { x: 1, y: 2 };
    println!("{:?}", p);
}
```


Module Declaration:


```
// my_module.rs
pub fn hello() {
    println!("Hello from my_module!");
}

// main.rs
mod my_module;

fn main() {
    my_module::hello();
}
```


Nested Module Declaration:


```
mod outer {
    pub mod inner {
        pub fn hello() {
            println!("Hello from inner module!");
        }
    }
}

fn main() {
    outer::inner::hello();
}
```


Visibility Modifiers:


```
mod outer {
    pub mod inner {
        pub fn hello() {
            println!("Hello from inner module!");
        }
    }
}

fn main() {
    outer::inner::hello();
}
```


Struct Update Syntax: Create a new struct instance while reusing values from an existing instance.


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let point = Point { x: 1, y: 2 };
    let new_point = Point { x: 3, ..point };
    println!("New point: ({}, {})", new_point.x, new_point.y);
}
```


Or Patterns: Match against multiple patterns in pattern matching.


```
fn main() {
    let value = Some(0);

    match value {
        Some(0) | Some(1) => println!("Matched 0 or 1"),
        _ => println!("Didn't match 0 or 1"),
    }
}
```


If Let: Concise single pattern matching.


```
fn main() {
    let option = Some(42);

    if let Some(x) = option {
        println!("Got a value: {}", x);
    }
}
```


While Let: Loop iteration with single pattern matching.


```
fn main() {
    let mut iterator = 0..3;

    while let Some(x) = iterator.next() {
        println!("Value: {}", x);
    }
}
```


Function Pointer: Specify a function as a value.


```
fn add(x: i32, y: i32) -> i32 {
    x + y
}

fn main() {
    let f: fn(i32, i32) -> i32 = add;
    println!("Result: {}", f(1, 2));
}
```


AsRef and AsMut: Convert a value into a reference or mutable reference of a different type.


```
fn print_length<T: AsRef<str>>(s: T) {
    println!("Length: {}", s.as_ref().len());
}

fn main() {
    let s = String::from("hello");
    print_length(s);
}
```


Try Blocks: A block returning a Result, available in nightly Rust builds.


```
trait Iterator {
    type Item;

    fn next(&mut self) -> Option<Self::Item>;
}

// Implementation of Iterator for a custom struct
```


Associated Types: Specify a type that is associated with the implementing type within a trait.


```
trait Iterator {
    type Item;

    fn next(&mut self) -> Option<Self::Item>;
}

// Implementation of Iterator for a custom struct
```


Default Trait Implementations: Provide default implementations that can be overridden by implementers within a trait.


```
trait MyTrait {
    fn method(&self) -> &str {
        "Default implementation"
    }
}

struct MyStruct;

impl MyTrait for MyStruct {}

fn main() {
    let my_struct = MyStruct;
    println!("{}", my_struct.method()); // Uses the default implementation
}
```


Trait Bounds: Constrain generic types to implement specific traits in generic function signatures.


```
fn print_length<T: AsRef<str>>(s: T) {
    println!("Length: {}", s.as_ref().len());
}

fn main() {
    let s = String::from("hello");
    print_length(s);
}
```


Higher-Ranked Trait Bounds: Constrain a generic type to implement a trait with an associated lifetime.


```
trait Callable<'a> {
    fn call(&self, arg: &'a str);
}

fn call_twice<T>(f: T, arg: &str)
where
    for<'a> T: Callable<'a>,
{
    f.call(arg);
    f.call(arg);
}

struct Printer;

impl<'a> Callable<'a> for Printer {
    fn call(&self, arg: &'a str) {
        println!("{}", arg);
    }
}

fn main() {
    let printer = Printer;
    call_twice(printer, "Hello");
}
```


Lifetime Annotations: Explicitly specify lifetimes of references in structs, functions, and traits.


```
struct Foo<'a> {
    bar: &'a str,
}

fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

fn main() {
    let s1 = String::from("short");
    let s2 = String::from("longer");

    let result = longest(s1.as_str(), s2.as_str());
    println!("Longest: {}", result);
}
```


Static Lifetimes: References with the longest possible lifetime, living for the entire duration of the program.


```
static HELLO: &str = "Hello, world!";

fn main() {
    println!("{}", HELLO);
}

}
```


Range Syntax: Create a range of values between `a` and `b`.


```
fn main() {
    for i in 1..5 {
        println!("{}", i);
    }
}
```


Inclusive Range Syntax: Create an inclusive range, including both `a` and `b`.


```
fn main() {
    for i in 1..=5 {
        println!("{}", i);
    }
}

}
```


Array and Slice Pattern: Destructure arrays or slices.


```
fn print_first_two_elements(slice: &[i32]) {
    if let [first, second, ..] = slice {
        println!("First two elements: {}, {}", first, second);
    }
}

fn main() {
    let numbers = [1, 2, 3, 4, 5];
    print_first_two_elements(&numbers);
}

}
```


Field Init Shorthand: Initialize a struct's fields with the same name as the variables.


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let x = 3;
    let y = 4;
    let point = Point { x, y };
    println!("Point: ({}, {})", point.x, point.y);
}
```


C-style Enum: Declare a C-style enumeration.


```
enum Direction {
    Up,
    Down,
    Left,
    Right,
}

fn print_direction(direction: Direction) {
    match direction {
        Direction::Up => println!("Going up!"),
        Direction::Down => println!("Going down!"),
        Direction::Left => println!("Going left!"),
        Direction::Right => println!("Going right!"),
    }
}

fn main() {
    let direction = Direction::Up;
    print_direction(direction);
}
```


Use Renaming: Rename an imported item.


```
use std::io::Result as IoResult;
use std::fs::File;

fn open_file(filename: &str) -> IoResult<File> {
    File::open(filename)
}

fn main() {
    let result = open_file("file.txt");
    match result {
        Ok(file) => println!("File opened successfully!"),
        Err(e) => println!("Failed to open the file: {}", e),
    }
}
```


Type Alias: Provide a new name for an existing type, often for clarity or to shorten type names.


```
type Kilometers = i32;

fn distance_in_miles(distance: Kilometers) -> f64 {
    const KILOMETERS_TO_MILES: f64 = 0.621371;
    f64::from(distance) * KILOMETERS_TO_MILES
}

fn main() {
    let distance: Kilometers = 100;
    println!("100 kilometers is {:.2} miles", distance_in_miles(distance));
}

```


`Raw Pointers: *const T and *mut T for raw (unsafe) pointers.`


```
fn main() {
    let x = 10;
    let y = &x as *const i32;
    unsafe {
        assert_eq!(*y, x);
    }
}

 } }
```


Repeat Expression: `[0; 5]` for creating an array with repeated values.


```
fn main() {
    let a = [0; 5];
    assert_eq!(a, [0, 0, 0, 0, 0]);
}
```


String Literal Concatenation: Concatenate adjacent string literals.


```
fn main() {
    let s = "Hello, " "world!";
    assert_eq!(s, "Hello, world!");
}
```


Unreachable Code: `unreachable!()` macro for marking a code location as unreachable.


```
fn process_data(data: Option<&str>) {
    match data {
        Some(value) => println!("Processing data: {}", value),
        None => unreachable!(),
    }
}

fn main() {
    process_data(Some("Hello, world!"));
}
```


Underscore in Numeric Literals: Improve readability in large numeric literals.


```
fn main() {
    let million = 1_000_000;
    println!("One million is written as: {}", million);
}

million); }
```


Dereference Operator: `*x` for dereferencing a reference or pointer.


```
fn main() {
    let x = 10;
    let y = &x;
    assert_eq!(*y, x);
}
```


Raw Identifier: `r#type` for using reserved keywords as identifiers.


```
fn main() {
    let r#type = "Reserved keyword as an identifier";
    println!("{}", r#type);
}
```


Loop Labels: `'label: loop { ... }` for labeling loops, and `break 'label;` or `continue 'label;` for breaking or continuing labeled loops.


```
fn main() {
    'outer: for x in 1..5 {
        'inner: for y in 1..5 {
            if x * y == 6 {
                println!("Found a match: {} * {} = 6", x, y);
                break 'outer;
            }
        }
    }
}
```


Async Functions: `async fn foo() -> Result&lt;(), ()> { ... }` for declaring asynchronous functions.


```
use std::time::Duration;
use async_std::task;

async fn async_sleep(seconds: u64) {
    task::sleep(Duration::from_secs(seconds)).await;
}

async fn example() {
    println!("Start");
    async_sleep(2).await;
    println!("Finish after 2 seconds");
}

fn main() {
    let fut = example();
    async_std::task::block_on(fut);
}

```



1. 

Pin: `std::pin::Pin` for creating a pinned reference, which ensures the memory it points to will not be moved.


```
use std::pin::Pin;

fn main() {
    let x = 5;
    let pinned = Pin::new(&x);
    println!("Pinned value: {}", *pinned);
}
```


Unsized Types: `T: ?Sized` trait bound for allowing generic types to be unsized.


```
fn print_value<T: ?Sized + std::fmt::Display>(value: &T) {
    println!("Value: {}", value);
}

fn main() {
    let value: &dyn std::fmt::Display = &42;
    print_value(value);
}
```


Zero-sized types: `struct Zst;` for declaring a zero-sized type (ZST) that occupies no memory.


```
struct Zst;

fn main() {
    let _zst = Zst;
    println!("Size of Zst: {}", std::mem::size_of::<Zst>());
}

std::mem::size_of::<Zst>()); }
```


Constant Function: `const fn foo() { ... }` for declaring a function that can be evaluated at compile-time.


```
rconst fn square(x: i32) -> i32 {
    x * x
}

const VAL: i32 = square(4);

fn main() {
    println!("The square of 4 is: {}", VAL);
```


}

Associated Constants: `const VALUE: i32 = 42;` for defining associated constants within trait or struct implementations.


```
trait HasValue {
    const VALUE: i32;
}

struct MyStruct;

impl HasValue for MyStruct {
    const VALUE: i32 = 42;
}

fn main() {
    println!("MyStruct value: {}", MyStruct::VALUE);
}

t::VALUE); }
```


Or-patterns: `Some(0) | Some(1) | Some(2)` for matching multiple patterns in a single arm.


```
fn match_small_numbers(n: Option<usize>) {
    match n {
        Some(0) | Some(1) | Some(2) => println!("Small number"),
        _ => println!("Not a small number"),
    }
}

fn main() {
    match_small_numbers(Some(1));
    match_small_numbers(Some(5));
}
```


Anonymous Lifetime: `'_` for specifying an anonymous lifetime parameter.


```
fn foo(s: &'_ str) -> &'_ str {
    &s[0..5]
}

fn main() {
    let s = String::from("Hello, world!");
    let result = foo(&s);
    println!("{}", result);
}
```


Boxed trait objects: `Box&lt;dyn Trait>` for creating a boxed trait object, which can hold any type that implements the trait.


```
trait Animal {
    fn speak(&self);
}

struct Dog;
struct Cat;

impl Animal for Dog {
    fn speak(&self) {
        println!("Woof!");
    }
}

impl Animal for Cat {
    fn speak(&self) {
        println!("Meow!");
    }
}

fn make_animal_speak(animal: Box<dyn Animal>) {
    animal.speak();
}

fn main() {
    let dog: Box<dyn Animal> = Box::new(Dog);
    let cat: Box<dyn Animal> = Box::new(Cat);

    make_animal_speak(dog);
    make_animal_speak(cat);
}
```


Dereference coercion: Automatically dereferencing a reference to a reference, e.g., &String to &str.


```
fn print_str(s: &str) {
    println!("{}", s);
}

fn main() {
    let s = String::from("Hello, world!");
    print_str(&s);
}
```


Diverging type: `!` for specifying a diverging type, which indicates that the function does not return.


```
fn panic_now() -> ! {
    panic!("This function never returns");
}

fn main() {
    println!("This will panic...");
    panic_now();
}
```


Module shorthand: `mod.rs` for defining a module in a separate file.


```
// src/my_module/mod.rs
pub fn say_hello() {
    println!("Hello from my_module!");
}

// src/main.rs
mod my_module;

fn main() {
    my_module::say_hello();
}
```


Eager macro expansion: `macro_rules! foo { ... }` for defining macros that are eagerly expanded during parsing.


```
macro_rules! print_sum {
    ($a:expr, $b:expr) => {
        println!("The sum is: {}", $a + $b);
    };
}

fn main() {
    print_sum!(3, 5);
}
```


Lazy macro expansion: `proc_macro! { ... }` for defining procedural macros that are expanded during code generation. Procedural macros are more complex and require a separate crate of type `proc-macro`. Here's an example of a simple procedural macro to derive a custom trait `HelloWorld`:


```
// hello_world_macro/Cargo.toml
[lib]
proc-macro = true

// hello_world_macro/src/lib.rs
extern crate proc_macro;

use proc_macro::TokenStream;
use quote::quote;
use syn::{parse_macro_input, DeriveInput};

#[proc_macro_derive(HelloWorld)]
pub fn hello_world_derive(input: TokenStream) -> TokenStream {
    let input = parse_macro_input!(input as DeriveInput);
    let ident = input.ident;

    let expanded = quote! {
        impl HelloWorld for #ident {
            fn hello_world() {
                println!("Hello, world! My name is {}!", stringify!(#ident));
            }
        }
    };

    TokenStream::from(expanded)
}

// hello_world/Cargo.toml
[dependencies]
hello_world_macro = { path = "../hello_world_macro" }

// hello_world/src/main.rs
use hello_world_macro::HelloWorld;

#[derive(HelloWorld)]
struct MyStruct;

fn main() {
    MyStruct::hello_world();
}
```


Type ascription: `let x: Type = expr;` for annotating the type of a variable explicitly.


```
fn main() {
    let x: i32 = 5;
    println!("x is {}", x);
}
```


Extern crate: `extern crate foo;` for explicitly linking an external crate (only required in Rust 2015 edition, not in Rust 2018 edition and later).


```
// Rust 2015 edition
// Cargo.toml
[dependencies]
rand = "0.8.5"

// main.rs
extern crate rand;

use rand::Rng;

fn main() {
    let num = rand::thread_rng().gen_range(1..=10);
    println!("Random number: {}", num);
}
```


NLL (Non-Lexical Lifetimes): More precise lifetime analysis, reducing restrictions on borrowing.

Non-Lexical Lifetimes (NLL) is an enhancement to Rust's borrow checker that allows for more precise and flexible lifetime analysis. In Rust, lifetimes are used to ensure that references to memory are always valid. Before NLL, Rust's borrow checker used a more conservative approach based on lexical scopes, which sometimes resulted in false positives, making it harder to write certain code patterns.

NLL improves the lifetime analysis by allowing the borrow checker to better understand when a reference is no longer used, even if it's still in scope. This can help reduce unnecessary restrictions on borrowing and make the code more ergonomic.

Here's an example to illustrate the difference between lexical lifetimes and non-lexical lifetimes:


```
fn main() {
    let mut x = 5;
    let y = &x;


    x = 6; // Error: cannot assign to `x` because it is borrowed
    println!("{}", y);
}
```


In this example, the borrow checker with lexical lifetimes would produce an error because `x` is borrowed by `y` and cannot be modified. However, with NLL, the borrow checker can recognize that the reference `y` is not used after the assignment to `x`, and therefore, it's safe to modify `x`.

Here's another example where NLL makes a difference:


```
fn process(val: &i32) {
    // Do something with val
}

fn main() {
    let mut data = vec![1, 2, 3, 4, 5];

    let item;
    {
        let first = &data[0];
        process(first);
        item = first;
    }

    data.push(6); // Error with lexical lifetimes, OK with NLL
}

 NLL }
```


In this example, the reference `first` is borrowed from `data` and processed, then assigned to `item`. With lexical lifetimes, the borrow checker would consider the borrow of `data` to be active until the end of the inner scope, which would make the `data.push(6)` call invalid. However, with NLL, the borrow checker can recognize that `first` is not used after it's assigned to `item`, and therefore, the `data.push(6)` call is safe and allowed.

Non-Lexical Lifetimes is a significant improvement to Rust's borrow checker that allows for more precise lifetime analysis, making the code more ergonomic and flexible without compromising safety.

Field init shorthand:


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let x = 3;
    let y = 5;
    let point = Point { x, y }; // Shorthand for Point { x: x, y: y }
}
```


Field init shorthand allows you to concisely initialize a struct when variables with the same names as the fields are in scope.

Inclusive Ranges:


```
for i in 1..=3 {
    println!("{}", i);
}
```


Inclusive Ranges create a range that includes both the start and end values, in this case, it will print 1, 2, and 3.

Byte string literals:


```
let byte_string = b"Hello, world!";
```


Byte string literals create an array of `u8` values, where each character in the string is represented by its ASCII value.

Raw string literals:


```
let raw_string = r#"This is a "raw" string with "quotes" and \slashes\."#;
```


Raw string literals allow you to create strings that do not process escape characters, making it easier to include quotes and backslashes.

Doc comments:


```
/// This function adds two numbers.
///
/// # Examples
///
/// ```
/// let result = my_function(2, 3);
/// assert_eq!(result, 5);
/// ```
pub fn my_function(a: i32, b: i32) -> i32 {
    a + b
}
```


Doc comments are used to create documentation for functions, structs, and other items in your code, which are then processed by the Rust documentation tool `rustdoc`.

Macro reexport:


```
#[macro_export]
macro_rules! my_macro {
    () => {
        println!("This is my exported macro!");
    };
}
```


Macro reexport makes a macro available to other crates when the module is used, allowing them to use the macro as if it was defined in their own code.

Global allocator:


```
use std::alloc::System;

#[global_allocator]
static GLOBAL: System = System;

fn main() {
    let v = vec![1, 2, 3];
}
```


Global allocator attribute allows you to specify a custom global memory allocator for a Rust program, which can be useful for optimizing memory usage or for using custom allocators.

Auto traits:


```
// Compiler automatically implements Send and Sync for MyStruct
struct MyStruct {
    a: i32,
    b: String,
}
```


Auto traits are traits that the Rust compiler automatically implements for types that meet certain criteria, such as `Send` and `Sync`. This can simplify code and reduce boilerplate.

Scoped attributes:


```
fn main() {
    #[cfg(target_os = "windows")]
    {
        println!("Running on Windows");
    }

    #[cfg(not(target_os = "windows"))]
    {
        println!("Not running on Windows");
    }
}
```


Scoped attributes apply an attribute to an item within a limited scope, making it easier to conditionally compile or execute code based on configuration.

Custom derive:


```
// In a separate crate
use proc_macro::TokenStream;

#[proc_macro_derive(MyTrait)]
pub fn my_trait_derive(input: TokenStream) -> TokenStream {
    // Implement your custom derive macro here
}

// In your main crate
#[derive(MyTrait)]
struct MyStruct {
    a: i32,
    b: String,
}
```


Custom derive allows you to implement macros that generate trait implementations for your structs or enums.

Nested imports:


```
use std::{fs, io};

fn main() {
    let mut file = fs::File::open("file.txt").unwrap();
    let mut buffer = String::new();
    io::Read::read_to_string(&mut file, &mut buffer).unwrap();
}
```


Nested imports let you import multiple items from the same path in a single `use` statement, making imports more concise.

Underscore in numeric literals:


```
fn main() {
    let large_number = 1_000_000;
    println!("One million: {}", large_number);
}

er); }
```


Underscores in numeric literals improve readability by visually separating digits in large numbers.

Extern types:


```
extern "C" {
    type Foo;
    fn foo_new() -> *const Foo;
}
```


Extern types are used to declare an opaque type with an unknown size and alignment, often when interfacing with foreign code.

Binding modes:


```
fn main() {
    let x = 5;
    match x {
        ref y => println!("Got a reference to {}", y),
    }
}
```


Binding modes `ref` and `ref mut` allow you to bind to a reference or mutable reference in pattern matching, providing more control over how values are accessed.

Try blocks (experimental):


```
#![feature(try_blocks)]

fn main() {
    let result: Result<i32, std::num::ParseIntError> = try {
        let x = "3".parse()?;
        let y = "5".parse()?;
        x + y
    };

    match result {
        Ok(sum) => println!("Sum: {}", sum),
        Err(err) => eprintln!("Error: {}", err),
    }
}
```


Try blocks enable the use of the `?` operator within a block, propagating errors to the enclosing scope (note that this is an experimental feature and requires a nightly Rust build).

Negative implementations:


```
struct MyType;

impl !std::fmt::Display for MyType {}
```


Negative implementations specify that a given type does not implement a particular trait, providing more precise control over trait bounds and coherence.

Array concatenation (Note: Rust does not support array concatenation directly, but you can achieve this using the `concat` macro from the `arraytools` crate.):


```
use arraytools::concat;

fn main() {
    let a = [1, 2, 3];
    let b = [4, 5, 6];
    let c = concat!(a, b);
    println!("{:?}", c);
}
```


Array concatenation joins two arrays end-to-end, forming a new array.

Array repeating:


```
fn main() {
    let arr = [1; 5];
    println!("{:?}", arr);
}
```


Array repeating creates an array of length N with all elements set to a.

Scoped lint attributes:


```
fn main() {
    #[allow(unused_variables)]
    let x = 5;
}
```


Scoped lint attributes allow or disallow specific lints within a limited scope, providing granular control over compiler warnings.

Lazy static:


```
use lazy_static::lazy_static;
use std::collections::HashMap;

lazy_static! {
    static ref CONSTANTS: HashMap<&'static str, i32> = {
        let mut m = HashMap::new();
        m.insert("ONE", 1);
        m.insert("TWO", 2);
        m
    };
}

fn main() {
    println!("One: {}", CONSTANTS.get("ONE").unwrap());
}
```


Lazy static enables the declaration of lazily initialized static values, provided by the `lazy_static` crate.

Associated consts:


```
trait Named {
    const NAME: &'static str;
}

struct Person;

impl Named for Person {
    const NAME: &'static str = "Person";
}

fn main() {
    println!("Name: {}", Person::NAME);
}

E); }
```


Associated consts allow declaring associated constants within a trait or implementation block.

Existential types (Note: existential types have been replaced by `impl Trait` in type aliases):


```
trait Foo {}

struct Bar;

impl Foo for Bar {}

type MyFoo = impl Foo;

fn create_foo() -> MyFoo {
    Bar
}

fn main() {
    let _foo = create_foo();
}
```


Existential types (replaced by `impl Trait` in type aliases) allow declaring a type alias for an opaque type that implements a given trait.

Struct update syntax:


```
struct Point {
    x: i32,
    y: i32,
}

fn main() {
    let point1 = Point { x: 1, y: 2 };
    let point2 = Point { x: 3, ..point1 };
    println!("point2: x = {}, y = {}", point2.x, point2.y);
}
```


Struct update syntax enables creating a new struct with some fields updated from an existing struct.

Or patterns:


```
fn main() {
    let value = Some(1);

    match value {
        Some(0) | Some(1) => println!("Matched 0 or 1"),
        Some(_) => println!("Matched another value"),
        None => println!("Matched None"),
    }
}
```


Or patterns allow matching on multiple patterns in a single arm of a `match` or `if let` expression.

Const generics (experimental feature):


```
#![feature(const_generics)]
#![allow(incomplete_features)]

struct Array<T, const N: usize> {
    items: [T; N],
}

impl<T, const N: usize> Array<T, N> {
    fn new(value: T) -> Self
    where
        T: Copy,
    {
        Array { items: [value; N] }
    }
}

fn main() {
    let arr: Array<i32, 5> = Array::new(42);
    println!("{:?}", arr.items);
}
```


Const generics enable defining generic parameters with constant values, allowing more powerful compile-time computations.

Inline attributes:


```
#[inline(always)]
fn add(a: i32, b: i32) -> i32 {
    a + b
}

fn main() {
    let result = add(2, 3);
    println!("Result: {}", result);
}
```


Inline attributes suggest that a function be inlined by the compiler, potentially improving performance at the cost of increased code size.

Trait objects:


```
trait Speak {
    fn speak(&self);
}

struct Dog;
struct Cat;

impl Speak for Dog {
    fn speak(&self) {
        println!("Woof!");
    }
}

impl Speak for Cat {
    fn speak(&self) {
        println!("Meow!");
    }
}

fn main() {
    let animals: Vec<Box<dyn Speak>> = vec![Box::new(Dog), Box::new(Cat)];
    for animal in animals {
        animal.speak();
    }
}
```


Trait objects allow creating a dynamically dispatched, heap-allocated object implementing a specific trait.

Automatic dereferencing:


```
struct Person {
    name: String,
}

impl Person {
    fn greet(&self) {
        println!("Hello, {}!", self.name);
    }
}

fn main() {
    let person = Person {
        name: "Alice".to_string(),
    };
    let person_ref = &person;
    person_ref.greet(); // Rust automatically dereferences person_ref
}
```


Automatic dereferencing allows calling methods on references or smart pointers without the need to explicitly dereference them using `*`.

Range patterns:


```
fn main() {
    let value = 2;

    match value {
        0..=2 => println!("Matched 0, 1, or 2"),
        _ => println!("Matched another value"),
    }
}
```


Range patterns allow matching a range of values inclusively within a match expression.

Nested import groups:


```
mod foo {
    pub mod bar {
        pub fn hello() {
            println!("Hello from bar!");
        }
    }

    pub mod baz {
        pub mod qux {
            pub fn hello() {
                println!("Hello from qux!");
            }
        }

        pub mod quux {
            pub fn hello() {
                println!("Hello from quux!");
            }
        }
    }
}

use foo::{bar, baz::{qux, quux}};

fn main() {
    bar::hello();
    qux::hello();
    quux::hello();
}
```


Nested import groups allow importing multiple items from the same module in a more concise way.

Enum variant aliases (Note: Rust does not support enum variant aliases, but you can create a wrapper function to achieve a similar effect.):


```
enum Color {
    Red,
    Green,
    Blue,
}

fn red() -> Color {
    Color::Red
}

fn main() {
    let color = red();
    match color {
        Color::Red => println!("It's red!"),



    Color::Green => println!("It's green!"),
    Color::Blue => println!("It's blue!"),
}

)
```


Destructuring assignment allows unpacking a tuple or struct into individual variables.


```
fn main() {
    let tuple = (1, 2);
    let (a, b) = tuple;
    println!("a: {}, b: {}", a, b);

    struct Point {
        x: i32,
        y: i32,
    }

    let point = Point { x: 3, y: 4 };
    let Point { x, y } = point;
    println!("x: {}, y: {}", x, y);
}

"turbofish" for const generics:
rstruct Array<const N: usize>([i32; N]);

fn make_array<const N: usize>() -> Array<N> {
    Array([0; N])
}

fn main() {
    let array: Array<{ 5 }> = make_array::<{ 5 }>();
    println!("array length: {}", array.0.len());
}
```


Use the "turbofish" syntax for const generics to specify the value of a const generic parameter, like in this example with an array of a specified length.

Nested functions:


```
fn main() {
    fn greet(name: &str) {
        println!("Hello, {}!", name);
    }

    greet("Alice");
    greet("Bob");
}
```


Nested functions can be defined inside other functions to help organize code and encapsulate logic.

Visibility shortcut:


```
mod my_module {
    pub(crate) fn public_within_crate() {
        println!("This function is visible within the crate");
    }
}

fn main() {
    my_module::public_within_crate();
}
```


Use `pub(crate)` to make a function or item visible only within the current crate.

Inline assembly (requires nightly Rust):


```
#![feature(asm)]

fn main() {
    let x: u32;
    unsafe {
        asm!("mov {}, 42", out(reg) x);
    }
    println!("x: {}", x);
}
```


Inline assembly can be used for highly optimized or low-level operations, but it requires nightly Rust and is unsafe.

"or patterns":


```
enum Fruit {
    Apple,
    Orange,
    Banana,
}

fn is_citrus(fruit: Fruit) -> bool {
    match fruit {
        Fruit::Orange | Fruit::Lemon => true,
        _ => false,
    }
}

fn main() {
    let orange = Fruit::Orange;
    println!("Is orange a citrus fruit? {}", is_citrus(orange));
}
```


Or patterns in match expressions allow matching multiple patterns in a single arm.

Non-exhaustive enums:


```
#[non_exhaustive]
pub enum Status {
    Ok,
    Error,
}

fn process_status(status: Status) {
    match status {
        Status::Ok => println!("Everything is OK"),
        Status::Error => println!("There was an error"),
        _ => println!("Unknown status"),
    }
}
```


Non-exhaustive enums signal that an enum may have additional variants in the future, so users should include a catch-all `_` match arm.

Pinning:


```
use std::pin::Pin;

fn main() {
    let value = Box::new(42);
    let pinned_value: Pin<Box<i32>> = Box::pin(*value);

    println!("The pinned value is: {}", *pinned_value);
}
```


The Pin type ensures that the memory address of the value it wraps won't change, which can be useful in certain contexts like async programming or working with self-referential types.

Async closure (requires nightly Rust):


```
#![feature(async_closure)]

async fn run_async_closure<F, Fut>(f: F)
where
    F: FnOnce() -> Fut,
    Fut: std::future::Future<Output = i32>,
{
    let result = f().await;
    println!("Result: {}", result);
}

fn main() {
    let async_closure = async || async { 42 };
    let fut = run_async_closure(async_closure);
    futures::executor::block_on(fut);
}
```


Async closures allow you to create closures that return a `Future`, but they are currently unstable and require nightly Rust.

Type-level integers (using typenum crate):


```
use typenum::{U3, U4};

fn main() {
    let array1: [i32; U3::to_usize()] = [1, 2, 3];
    let array2: [i32; U4::to_usize()] = [1, 2, 3, 4];
}
```


Use type-level integers from the typenum crate to create types with integer parameters, enabling type-level programming techniques.

Wrapping arithmetic:


```
use std::num::Wrapping;

fn main() {
    let a = Wrapping(u32::MAX);
    let b = Wrapping(1u32);
    let result = a + b;
    println!("Wrapped addition result: {}", result.0);
}

}
```


The `Wrapping` type performs arithmetic operations that "wrap" on overflow or underflow, useful in low-level or cryptographic applications.

Uninhabited types:


```
fn never_returns() -> ! {
    loop {
        // This function never returns
    }
}

eturns } }
```


The `!` type is used to indicate that a function never returns, such as a function that enters an infinite loop.

Multidispatch (limited example):


```
trait Animal {
    fn speak(&self);
}

struct Cat;
struct Dog;

impl Animal for Cat {
    fn speak(&self) {
        println!("Meow!");
    }
}

impl Animal for Dog {
    fn speak(&self) {
        println!("Woof!");
    }
}

fn main() {
    let animals: Vec<Box<dyn Animal>> = vec![Box::new(Cat), Box::new(Dog)];
    for animal in animals {
        animal.speak(); // Multidispatch based on the actual type of the object
    }
}
```


Rust supports limited multiple dispatch through traits and trait objects, allowing dynamic method resolution at runtime based on object types.


```
Custom dereference coercions:
use std::ops::Deref;

struct Wrapper(String);

impl Deref for Wrapper {
    type Target = str;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

fn main() {
    let wrapper = Wrapper(String::from("Hello, world!"));
    let string_ref: &str = &wrapper;
    println!("{}", string_ref);
}

; }
```


Implementing the `Deref` trait enables custom dereference coercions for your types, overloading the `*` operator.

Safe transmutes (using safe-transmute crate):


```
use safe_transmute::guarded_transmute;

fn main() {
    let bytes: &[u8] = &[0, 0, 0, 42];
    let result = guarded_transmute::<i32>(bytes);
    match result {
        Ok(value) => println!("Transmuted value: {}", value),
        Err(_) => println!("Invalid transmutation"),
    }
}
```


The safe-transmute crate

Const generics (available since Rust 1.51):


```
struct ArrayWrapper<const N: usize> {
    array: [i32; N],
}

impl<const N: usize> ArrayWrapper<N> {
    fn new(array: [i32; N]) -> Self {
        ArrayWrapper { array }
    }

    fn sum(&self) -> i32 {
        self.array.iter().sum()
    }
}

fn main() {
    let wrapper1 = ArrayWrapper::new([1, 2, 3]);
    let wrapper2 = ArrayWrapper::new([1, 2, 3, 4, 5]);

    println!("Sum of wrapper1: {}", wrapper1.sum());
    println!("Sum of wrapper2: {}", wrapper2.sum());
}

Const generics allow you to parameterize types over constant values, enabling more expressive and powerful generic programming techniques.

Associated consts:
trait HasArea {
    const PI: f64;

    fn area(&self) -> f64;
}

struct Circle {
    radius: f64,
}

impl HasArea for Circle {
    const PI: f64 = 3.14159265359;

    fn area(&self) -> f64 {
        Self::PI * self.radius * self.radius
    }
}
```


Associated consts allow you to define constant values within a trait implementation for a specific type.

Unsafe traits:


```
unsafe trait UnsafeCounter {
    fn increment(&mut self);
}

struct Counter {
    value: i32,
}

unsafe impl UnsafeCounter for Counter {
    fn increment(&mut self) {
        self.value += 1;
    }
}
```


Unsafe traits indicate that implementing the trait requires adhering to certain invariants that the Rust compiler cannot enforce.

Diverging functions:


```
fn infinite_loop() -> ! {
    loop {}
}
```


Diverging functions have a special return type !, which is called the "never" type, indicating the function never returns.

Function pointers:


```
fn add(x: i32, y: i32) -> i32 {
    x + y
}

fn main() {
    let add_fn: fn(i32, i32) -> i32 = add;
    println!("Result: {}", add_fn(2, 3));
}
```


Function pointers store references to functions, allowing you to use them as arguments or return values.

Custom allocators:


```
use std::alloc::{GlobalAlloc, Layout, System};

struct MyAllocator;

unsafe impl GlobalAlloc for MyAllocator {
    unsafe fn alloc(&self, layout: Layout) -> *mut u8 {
        System.alloc(layout)
    }

    unsafe fn dealloc(&self, ptr: *mut u8, layout: Layout) {
        System.dealloc(ptr, layout)
    }
}

#[global_allocator]
static GLOBAL: MyAllocator = MyAllocator;
```


Custom allocators let you implement the GlobalAlloc trait and use the #[global_allocator] attribute to specify a custom allocator.

Macros:


```
macro_rules! vec {
    ($($x:expr),*) => {
        {
            let mut temp_vec = Vec::new();
            $(
                temp_vec.push($x);
            )*
            temp_vec
        }
    };
}

fn main() {
    let v = vec![1, 2, 3];
    println!("{:?}", v);
}
```


Macros in Rust use the macro_rules! keyword to define patterns and expansions, allowing you to create reusable chunks of code with a concise syntax.

Custom derive:


```
// Create a simple custom derive macro for a trait named "Hello"
use proc_macro::TokenStream;
use quote::quote;
use syn::{parse_macro_input, DeriveInput};

#[proc_macro_derive(Hello)]
pub fn hello_derive(input: TokenStream) -> TokenStream {
    let input = parse_macro_input!(input as DeriveInput);
    let name = input.ident;

    let expanded = quote! {
        impl Hello for #name {
            fn hello(&self) {
                println!("Hello from {}", stringify!(#name));
            }
        }
    };

    TokenStream::from(expanded)
}

// Use the custom derive macro in your code
#[derive(Hello)]
struct MyStruct;

fn main() {
    let my_struct = MyStruct;
    my_struct.hello();
}
```


Custom derive macros can automatically generate trait implementations for your types based on the structure and fields of the type.

Attributes:


```
// Conditional compilation
#[cfg(target_os = "linux")]
fn on_linux() {
    println!("You are running on Linux!");
}

#[cfg(not(target_os = "linux"))]
fn on_linux() {
    println!("You are not running on Linux.");
}

// Customizing derives
#[derive(Debug)]
struct Point {
    x: i32,
    y: i32,
}

// Specifying test functions
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_point() {
        let p = Point { x: 3, y: 4 };
        assert_eq!(p.x, 3);
        assert_eq!(p.y, 4);
    }
}

fn main() {
    on_linux();
    let point = Point { x: 1, y: 2 };
    println!("{:?}", point);
}

}
```


Rust attributes are metadata applied to modules, items, or expressions for various purposes, such as conditional compilation, customizing derives, or specifying test functions.
