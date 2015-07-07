# Rust in an Hour

## Context

Rust is a systems level programming language initially developed by Graydon Hoare and later adopted by Mozilla.

Its goals are to be:
* Fast
* Memory-Safe
* Safe in the face of concurrency

## A few words upfront

This course cannot cover all aspects of Rust. As many of the gains of Rust are based on its primitives, we might not be able to cover the mind-boggling things shere - we will provide some examples and outlook in the end.

## Toolchain

Rust comes with a full toolchain. A compiler (`rustc`), a documentation tool (`rustdoc`) and a build and dependency manager (`cargo`). It is recommended to use those immediately.

## Starting your first Rust project

Download the current stable release of Rust, install and run:

```sh
$ cargo new --bin my-project
```

and you will find the following layout:

```sh
.
├── Cargo.toml
└── src
    └── main.rs
```

`Cargo.toml` is a file that describes how to build our project and which dependencies it has. `main.rs` is our main program. If we would build a lib, I'd be called `lib`. Let's have a look at it:

```
fn main() {
    println!("Hello, world!");
}
```

We see a function called `main`, used as the entry point into the program and a _macro_ printing "Hello, world!". Rust looks a bit like C here, but that will not last very long.

We can build and run it with `cargo run`. Just building works with `cargo build`. Both take a `--release` flag, allowing for optimized builds. Optimization is very important for fast Rust!

Let's extend this a little:

```
use std::env;

fn main() {
    let what: Option<String> = env::args().next();
    match what {
        Some(string) => println!("Hello, {}", string),
        None => panic!("Nothing to print passed!")
    }
}
```

There are more things to see here: Rust is a statically typed language, so the compiler knows that `what` is of the type `Option<String>`. `Option<Something>` is a data structure that we will see quite often: it either holds some data (`Some(Something)`) or not (then, it is `None`).

The next is _destructuring_ using `match`. `match` takes variable, _matches_ on its structure and does something depending on the result. In this case, it does something different depending on the first argument of the program being present or not.

To avoid long tedious typing of long type signatures, Rust also provides local type inference, so the type of the variable can be left of:

```
use std::env;

fn main() {
    let what = env::args().next();
    match what {
        Some(string) => println!("Hello, {}", string),
        None => panic!("Nothing to print passed!")
    }
}
```