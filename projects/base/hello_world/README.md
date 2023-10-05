# Hello World!

It is time to write yoyr first Rust program. It's traditional when learning a new language to write a program that prints the text `Hello World!` to the screen, so we'll do the same here!

## Creating a new project directory

You'll start by making a directory to store your Rust code. It doesn't matter to Rust where your code lives, but for the exercises and the projects in this repository, I'll suggest making a _projects_ directory in your home directory.  
The following command list will create the directory and moves the terminal into it.

On Linux, macOS and PowerShell on Windows:
```
$ mkdir -p ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

On Windows Command Prompt:
```
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

## Writing and running your first program

Next, make a new source file and call it `main.rs`. Rust files always end with the `.rs` extension.  
__Note__: If you're using more than one word in your file name, use an underscore to separate them. For example, :white_check_mark:  `hello_world.rs` is a good name for a file, but :x: `hello world.rs` is not.

Now, open the file in your text editor and type the following code into it:
```rust
fn main() {
    println!("Hello, world!");
}
```

Save the file, and go back to your terminal window, in the same directory as the `main.rs` file. 

On Linux and macOS, use this command to compile and run the program:
```
$ rustc main.rs
$ ./main
Hello, world!
```
On Windows, enter the command .\main.exe instead of ./main:
```
> rustc main.rs
> .\main.exe
Hello, world!
```

Regardless of the operating system you use, you should see the output `Hello, world!` printed to your terminal. Congratulations! You've written and run your first Rust program.

## Anatomy of a Rust program

Let's take a closer look at the code you wrote.  
Here is the first piece of the puzzle:

```rust
fn main() {

}
```

This lines define a function named `main`. The main function is special: it is always the first code that runs in every executable Rust program. Here, the first line declares a function named `main` that has no parameters and returns nothing. If there were parameters, they would go inside the parentheses `()`. We'll talk about return values in a later part of the repository.  
The curly brackets `{}` tell the compiler where the function body begins and ends. Rust requires curly brackets around function bodies, and many other places, to make your code less ambiguous.

__Note__: If you want to stick to a standard style across Rust projects, you can use an automatic formatter tool called `rustfmt` to format your code in a particular style. You can run `rustfmt` on your code by running `rustfmt main.rs` in your terminal.

The body of the `main` function holds the following code:

```rust
println!("Hello, world!");
```

This line does all the work in this little program: it prints text to the screen. There are four important details to notice here:
- Rust style is to indent with four spaces, not a tab.
- The `println!` calls a Rust macro. If it called a function instead, it would be entered as `println` (without the !). We will discuss about macros later. For now, you just need to know that using `!` means you're calling a macro instead of a normal function and that macros don't always follow the same rules as functions.
- the string `"Hello, world!"` is passed as an argument to `println!`, and the string is printed to the screen.
- we end the line with a semicolon (`;`), which indicates that this expression is over and the next one is ready to begin. Most lines of Rust code end with a semicolon. 

If you forget to put the semicolon at the end of a line, Rust will give you an error and won't compile. In Rust, the semicolon tells the compiler to expect more code, but if there isn't any more code, Rust reports an error. Let's see what happens if you remove the semicolon from the `println!` line:

```rust
fn main() {
    println!("Hello, world!")
}
```

If you try compiling this program, you'll get this error:

```rust
$ rustc main.rs
error: expected `;`, found `}`
    --> main.rs:3:1
    |
    3 | }
    |  ^
    |
    = note: If you intended to return on the last line of the function body, you can
    remove the semicolon.
```

