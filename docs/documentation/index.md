# Introduction
## What is MGLFW?
MGLFW (or Minimal GLFW) is a wrapper for the [glfw-rs](https://crates.io/crates/glfw) crate. It aims to make using GLFW easier.

## Example
This is the standard window example provided on the [crates.io](https://crates.io) page.
```rust
extern crate glfw;

use glfw::{Action, Context, Key};

fn main() {
    let mut glfw = glfw::init(glfw::fail_on_errors).unwrap();

    let (mut window, events) = glfw.create_window(300, 300, "Hello this is window", glfw::WindowMode::Windowed)
        .expect("Failed to create GLFW window.");

    window.set_key_polling(true);
    window.make_current();

    while !window.should_close() {
        glfw.poll_events();
        for (_, event) in glfw::flush_messages(&events) {
            handle_window_event(&mut window, event);
        }
    }
}

fn handle_window_event(window: &mut glfw::Window, event: glfw::WindowEvent) {
    match event {
        glfw::WindowEvent::Key(Key::Escape, _, Action::Press, _) => {
            window.set_should_close(true)
        }
        _ => {}
    }
}
```

And this is the same example, but using MGLFW.
```rust
mod mglfw;
use mglfw::{core, input};

fn main() {
    let mut mglfw = core::Mglfw::new("Hello, MGLFW!", 300, 300);
    let mut input = input::Input::new();

    let escape = input.new_keybind(input::KeyCode::Escape, input::Activation::Press);

    while mglfw.is_running() {
        mglfw.update();

        if input.is_bind_active(&mglfw, &escape) {
            mglfw.quit();
        }
    }
}
```

## Warnings
This is not ready for any proper use, I am just work on this a hobby project so updates will probably be infrequent and small.
