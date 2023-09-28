# Rust
Public repository on witch you can find various source code and algorithms to learn the Rust programming lanaugage and the libraries.

Inside the various directories you can find a README and other Markdown files on witch all the functions and the concepts are explained

Make sure to use Rust 1.62.0 (released on 30/06/2022) or later versions, along with

    ```
    edition = "2021" 
    ```
    
in the Cargo.toml file of all projects to configure them to use Rust 2021 edition idioms.

The 2021 edition of the Rust Programming Language includes a number of improvements that make Rust more ergonomic and correct some inconsistencies.

The Rust 2021 edition is backwards compatible with the Rust 2018 edition, so all your existing Rust code will continue to compile with the Rust 2021 edition.

## Introduction

Welcome to the Rust Programming Language, a PL that helps you write faster, more reliable software. High-level ergonomics and low-level control are often at odds in programming language design; Rust challenges that conflict. Through balancing powerful technical capacity and a great developer experience, Rust gives you the option to control low-level details (such as memory usage) without all the hassle traditionally associated with such control.

## Getting Started

In this part, we will discuss how to install Rust on your system.

### Installation
The first step is to install Rust. We'll download Rust through _rustup_ , a command line tool for managing Rust versions and associated tools.  
__Note__: If you prefer to not use _rustup_ , plese see the Other Rust Insyallation Methods page [here](https://forge.rust-lang.org/infra/other-installation-methods.html) for more options.

The following steps install the latest stable version of the Rust compiler. Rust's stability guarantees ensure that all examples in this repository that compile will continue to compile with future versions of Rust.  
__The output might differ slightly between versions__ becouse Rust often improves error messages and warnings. 

#### Installing rustup on Linux or macOS
If you are using Linux or macOS, open a terminal and enter the following command:
```
$ curl --proto '=https' --tlsv1.3 -sSf https://sh.rustup.rs | sh
```
The command downloads a script and starts the installation of the _rustup_ tool, which installs the latest stable version of Rust. Follow the on-screen instructions to complete the installation. If the installation is successful, you'll see the following output:
```
Rust is installed now. Great!
```
You will also need a linker, which is a program that Rust uses to join its compiled outputs into one file. The linker is included in the GNU Compiler Collection (GCC). Most systems already have GCC installed, but if you don't have it, you can install it with your package manager. On Ubuntu and Debian, run the following command:
```
$ sudo apt install build-essential
```
On macOS, you'll need to install the Xcode Command Line Tools. You can do this by running the following command:
```
$ xcode-select --install
```

#### Installing rustup on Windows
If you are using Windows, from [here](https://www.rust-lang.org/tools/install) you can download and install the latest version of rust. At some point of the installation, you'll receive a message explaining that you will also need the MSVC build tool for Visual Studio 2013 or later.  
To acquire the build tools, you'll need to install Visual Studio 2022 Community. You can download it from [here](https://visualstudio.microsoft.com/downloads/). When asked which workloads to install, make sure to select
- the "Desktop development with C++" workload
- the Windows 10 or 11 SDK (10.0.19041.0 or later)
- the English language pack for Visual Studio, along with any other languages you'd like to use.

### Troubleshooting
To check whether Rust is installed correctly, run the following command:
```
$ rustc --version
```
You should see the version number, commit hash, and commit date for the latest stable version of Rust, in the following format:
```
rustc x.y.z (abcabcabc yyyy-mm-dd)
```
If you see this output, you've installed Rust successfully and are ready to move on. If not, check that Rust is in your PATH variable. If you're using Linux or macOS, run the following command:
```
$ echo $PATH
```
In PowerShell on Windows, run the following command:
```
$ echo $env:PATH
```
In Windows Command Prompt, run the following command:
```
$ echo %PATH%
```
If that's all correct and you still don't see the output above, thare are a number of places you can get help.

### Updating and Uninstalling
If you already have Rust installed, you can update it by running the following command:
```
$ rustup update
```
To uninstall Rust, run the following command:
```
$ rustup self uninstall
```

### Local Documentation
The installation of Rust also includes a local copy of the documentation so that you can read it offline. To open the documentation in your browser, run the following command:
```
$ rustup doc
```
Any time a type of function is provided by the standard library, and you are not sure what it does or how it works, you can use this command to read the documentation locally.  
For example, if you want to know what the _let_ keyword does, you can run the following command:
```
$ rustup doc let
```