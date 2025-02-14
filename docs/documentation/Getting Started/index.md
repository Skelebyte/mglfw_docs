# Getting Started
## Installation
To install MGLFW, there is only 1 way. 

1. Go to the [Github repository](https://github.com/Skelebyte/mglfw/releases) and choose the latest stable release.
2. Move the `mglfw.rs` file into the `src` file of your rust project
3. Run `cargo add glfw` or add `glfw = "0.59.0"` to your `Cargo.toml` file.
4. Build the project to ensure everything is ok.

## Usage
To use MGLFW, you need to add `mod mglfw;` to the top of your code (typically the `main.rs` file).
```rust title="main.rs"
mod mglfw;

fn main() {
    println!("Hi mum!");
}
```
!!! note
    You may want to compile here just to make sure everything is ok and you don't have errors.

Now to start calling MGLFW functions you need to use the modules inside MGLFW. I would recommend using the `core` and `input` modules
```rust title="main.rs"
mod mglfw;
use mglfw::{core, input};

fn main() {
    println!("Hi mum!");
}
```
!!! note
    The `core` module contains everything related to window and glfw context creation, and is required for all other MGLFW modules.

