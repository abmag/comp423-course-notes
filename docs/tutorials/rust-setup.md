# Setting up a dev container for Rust

* Primary author: [Aidan Maguire](https://github.com/abmag)
* Reviewer: [Anish Toomu](https://github.com/av2mu)


This tutorial will guide you through setting up a Dev Container for Rust development, starting from a blank directory. By the end, you'll have a functional Rust project that prints "Hello COMP423" to standard output.

## Prerequisites

!!!info
    Make sure you have the following installed:
    - Docker
    - VSCode with the Remote - Containers extension
    - Git


## Step 1: Create a New Directory and Initialize Git

1. Open a terminal and create a new directory for your project:
   ```bash
   mkdir rust-dev-container
   cd rust-dev-container
   ```
2. Initialize a new Git repository:
   ```bash
   git init
   ```

## Step 2: Create the Dev Container Configuration Files

1. Create a `.devcontainer` directory:
   ```bash
   mkdir .devcontainer
   cd .devcontainer
   ```
2. Inside the `.devcontainer` directory, create a `devcontainer.json` file with the following content:
   ```json
   {
     "name": "Rust Dev Container",
     "image": "mcr.microsoft.com/devcontainers/rust:1-1.72-bullseye",
     "customizations": {
       "vscode": {
         "extensions": ["rust-lang.rust-analyzer"]
       }
     }
   }
   ```

!!! note
    This configuration uses a base image from Microsoft and installs the `rust-analyzer` extension for VSCode.


## Step 3: Build and Open the Dev Container

1. Open the project in VSCode.
2. Use the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P` on macOS) and select **Remote-Containers: Reopen in Container**.
3. Wait for the container to build and start. Once inside the container, open a terminal in VSCode.

## Step 4: Verify Rust Installation

1. In the terminal, check the installed Rust version:
   ```bash
   rustc --version
   ```
   You should see a recent version of Rust.

## Step 5: Create a New Rust Project

1. Create a new binary project with `cargo`:
   ```bash
   cargo new hello_world --vcs none
   cd hello_world
   ```
2. Open the `hello_world` directory in VSCode.

!!!tip
    The `--vcs none` flag prevents Cargo from initializing a Git repository, as we've already initialized one.


## Step 6: Write and Run a Basic "Hello COMP423" Program

1. Open the `src/main.rs` file. It should already contain a "Hello World" program, so edit it to "Hello COMP423:
   ```rust
   fn main() {
       println!("Hello, COMP423!");
   }
   ```
2. Build the program using the `cargo build` command:
   ```bash
   cargo build
   ```
   This generates a binary in the `target/debug` directory.

!!!info
    ```cargo build``` has a similar function to ```gcc``` from COMP 211. Both commands compile source code into an executable file.

3. Run the built binary directly:
   ```bash
   ./target/debug/hello_world
   ```
   You should see:
   ```
   Hello, COMP423!
   ```

4. Alternatively, use the `cargo run` command to build and run the program in one step:
   ```bash
   cargo run
   ```
   This will output the same "Hello, COMP423!" message.

!!!info
    **Difference between `cargo build` and `cargo run`:**
    - `cargo build` compiles your program without running it.
    - `cargo run` compiles and then immediately runs your program.


## Step 7: Commit Your Work

1. Add all files to Git and commit your changes:
   ```bash
   git add .
   git commit -m "Initial Rust Dev Container setup"
   ```

## Conclusion

Congratulations! You've successfully set up a Rust Dev Container, created a project, and run your first program. You now have a powerful environment for Rust development.
