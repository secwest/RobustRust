

Rust Syntactic Sugar

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




`` Operator


<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: Definition term(s) &uarr;&uarr; missing definition? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>






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



1. Reference Operator:


```
fn main() {
    let x = 42;
    let y = &x;
    println!("The value of y is: {}", y);
}

```



1. Dereference Operator:


```
fn main() {
    let x = 42;
    let y = &x;
    let z = *y;
    println!("The value of z is: {}", z);
}

}

```



1. Ownership Transfer:


```
fn main() {
    let x = String::from("hello");
    let y = x;
    println!("The value of y is: {}", y);
}

```



1. Borrowing:


```
fn print_length(s: &String) {
    println!("The length of the string is: {}", s.len());
}

fn main() {
    let s = String::from("Hello, world!");
    print_length(&s);
}

```



1. Impl Trait:


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
