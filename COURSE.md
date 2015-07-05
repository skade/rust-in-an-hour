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

`Cargo.toml` is a file that describes how to build our project and which dependencies it has. `main.rs` is our main program. If we would build a lib, I'd be called `lib`. Let's have a look:

```
$ cat src/main.rs
fn main() {
    println!("Hello, world!");
}
```

We can build and run it with `cargo run`. Just building works with `cargo build`. Both take a `--release` flag, allowing for optimized builds. Optimization is very important for fast Rust!
