# Hello Cargo

Just compiling with `rustc` is fine for small projects with only a few source files, but as your project grows, you'll want to manage your project's dependencies, build configuration, and other options. For this reason, the Rust community has developed a number of tools to make managing these tasks easier. The most commonly used one is Cargo.

Cargo is Rust's build system and package manager. Most Rustaceans use Cargo to manage their Rust projects because Cargo handles a lot of tasks for you, such as building your code, downloading the libraries your code depends on, and building those libraries (we call the libraries that your code needs dependencies).

The simplest Rust programs, like the one in the previous section, don't have any dependencies. If you had built the "Hello, World!" program using Cargo, it would only use the part of Cargo that builds your code. As your programs become more complex, Cargo will handle much more, such as building multiple source files into one program, downloading libraries your program depends on, and building those libraries.

Becouse the majority of the Rust projects use Cargo, for now on in the repository we will assume that you are using Cargo to build your projects.

To check if you have Cargo installed, run this command:

```bash
$ cargo --version
cargo 1.51.0 (43b129a20 2021-03-16)
```

If you see a version number, you have it! If you see an error, such as `command not found`, visit [the installation page](https://www.rust-lang.org/tools/install) to install it.

## Creating a Project with Cargo

Let's create a project that uses Cargo so you can see how it works and how it differs from the original "Hello, World!" program. We'll use Cargo to create a new project called `hello_cargo`, and then we'll build and run that project. Navigate where you want to create your project base directory and run this command:

```bash
$ cargo new hello_cargo
     Created binary (application) `hello_cargo` package
$ cd hello_cargo
```

The first command creates a new directory and project called `hello_cargo`. Since we've named our project `hello_cargo`, Cargo has generated a directory with the same name.  
Go into the `hello_cargo` directory and you'll see that Cargo has generated two files and one directory for us:

```bash
$ tree
.
├── Cargo.toml
└── src
    └── main.rs

1 directory, 2 files
```

Cargo will also initialize a new git repository for you, along with a `.gitignore` file and an initial commit. Git files won't be generated if you already have a git repository in the current directory. You can override this behavior with the `cargo new --vcs=git` command. 

__Note__: Git is a common version control system. You can change the `cargo new` command to use a different version control system, such as Mercurial, by using the `--vcs` flag. If you're not sure what version control system to use, we recommend Git. Run `cargo new --help` to see the available options.

Open the `Cargo.toml` file in your text editor. It should look like this:

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

This file is the TOML (Tom's Obvious, Minimal Language) format, which is Cargo's configuration format.  
The first line, `[package]`, is a section heading that indicates that the following statements are configuring a package.  
Each of the next three lines is a key-value pair that has a statement and a value, like `name = "hello_cargo"`. Those three lines are informations that Cargo needs to compile your project: name, version and editoin of Rust to use. We'll talk later about the `edition` key.  
The last line, `[dependencies]`, is the start of a section for you to list any of your project's dependencies. If your project doesn't have any dependencies at all, the `[dependencies]` section will be empty, as it is in this example. 

Now open the `src/main.rs` file in your text editor. It should look like this:

```rust
fn main() {
    println!("Hello, world!");
}
```

This is the same code we entered in the previous section. Cargo has generated a "Hello, World!" program for us that is ready to build and run. So far, the only difference between this code and the code in the previous section is that Cargo placed the code in the `src` directory in a file named `main.rs` instead of in a file named `hello_world.rs`, and Cargo also created a `Cargo.toml` file. Cargo expects all the code to live in the `src` directory. The top-level project directory is just for README files, license information, configuration files, and anything else not related to your code.

## Building and Running a Cargo Project

Now that you've generated a project, let's compile it using Cargo. Make sure you're still in the `hello_cargo` directory, containing the `Cargo.toml` file and the `src` directory. Then run this command:

```bash
$ cargo build
   Compiling hello_cargo v0.1.0 (/home/you/projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.31s
```

This command creates an executable file in `target/debug/hello_cargo` (or `target\debug\hello_cargo.exe` on Windows) rather than in your current directory. The `target/debug` directory is where Cargo puts the executable files for projects that it builds.  
Becouse the default build is a debug build, Cargo puts the binaries in a `target/debug` directory. The debug build takes longer to compile, but includes helpful tools that make your program easier to debug. When your project is ready for release, you can compile with `--release` to create an optimized version of your binary in `target/release` instead. This makes your Rust code run faster, but it takes longer to compile.

Run the executable file to see the "Hello, World!" output:

```bash
$ ./target/debug/hello_cargo
Hello, world!
```

If all goes well, you should see the output `Hello, world!`. Running `cargo build` for the first time also causes Cargo to create a new file: `Cargo.lock`. This file keeps track of the exact versions of dependencies in your project. This project doesn't have dependencies, so the `Cargo.lock` file will be small:

```bash
$ cat Cargo.lock
# This file is automatically @generated by Cargo.
# It is not intended for manual editing.
[[package]]
name = "hello_cargo"
version = "0.1.0"
dependencies = []
```

We just built a project with Cargo, but we can also use `cargo run` to run a project. Run this command:

```bash
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.31 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

Cargo also provides a command called `cargo check`. This command quickly checks your code to make sure it compiles but doesn't produce an executable:

```bash
$ cargo check
    Checking hello_cargo v0.1.0 (/home/you/projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.16s
```

Why would you not want an executable? Often, `cargo check` is much faster than `cargo build`, because it skips the step of producing an executable. If you're continually checking your work while writing the code, using `cargo check` will speed up the process! As you can see, `cargo check` takes about half the time as `cargo build` does.

Let's recap what we've learned about Cargo so far:
- We can create a new project that uses Cargo with `cargo new`.
- We can build a project using `cargo build`.
- We can build and run a project in one step using `cargo run`.
- We can build a project without producing a binary to check for errors using `cargo check`.
- Instead of saving the result of the build in the same directory as our code, Cargo stores it in the `target/debug` directory.
- The Cargo commands are the same for all operating systems, so all your collaborators will be able to build your package without extra effort on their part.