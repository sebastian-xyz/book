# Installing Nu

The best way currently to get Nu up and running is to install either from [crates.io](https://crates.io) or to build it from source. 

## Getting Ready

Before we can install Nu, we need to make sure our system has the necessary requirements. Currently, this means making sure we have the OpenSSL library available so that the commands that work with URLs can work with secure HTTP as well.

### Installing Rust

If we don't already have Rust on our system, the best way to install it via [rustup](https://rustup.rs/). Rustup is a way of managing Rust installations, including managing using different Rust versions. 

Nu currently requires the **nightly** version of Rust. When you first open "rustup" it will ask what version of Rust you wish to install:

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Selection option #2 to customize the installation, 

```
Default host triple?
```

Hit enter here to select the default.

```
Default toolchain? (stable/beta/nightly/none)
```

Make sure to type "nightly" here and press enter. This should give this setup:

```
Modify PATH variable? (y/n)
```

You can optionally update your path. This is generally a good idea, as it makes later steps easier.


```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

You can see that our default toolchain has now changed to the nightly toolchain. If this sounds a bit risky, don't worry. The Rust compiler is run through a full battery of tests. The nightly compiler is often reliable despite being on the cutting edge.

Once we are ready, we press 1 and then enter.  After this point, we can follow the instructions "rustup" gives us and we should have a working Rust compiler on our system.

If you'd rather not install Rust via "rustup", you can also install it via other methods (eg from a package in a Linux distro). Just be sure to install a recent nightly version of the toolchain.

### Installing openssl

Using [homebrew](https://brew.sh/), you will need to install the "openssl" formula:

```
brew install openssl
```

## Installing from [crates.io](https://crates.io)

Once we have the depencies Nu needs, we can install it using the `cargo` command that comes with the Rust compiler.

```
> cargo install nu
```

That's it!  The cargo tool will do the work of downloading Nu and its source dependencies, building it, and installing it into the cargo bin path so that we can run it.

Once installed, we can run Nu using the `nu` command:

```
$ nu
/home/jonathan/Source> 
```

## Building from source

We can build our own Nu from github without downloading the latest release. This gives us immediate access to the latest Nu features and bugfixes.

```
> git clone https://github.com/nushell/nushell.git
```

Git will clone the main nushell repo for us. From there, we can build and run Nu:

```
> cd nushell
nushell> cargo build && cargo run
```

You can also build and run Nu in release mode:

```
nushell> cargo build --release && cargo run --release
```

**Note:** If you are working with both debug and release builds, be sure to run `cargo clean` when you switch between them. Because Nu will look for plugins in both debug and release directories, it may pick up versions of the plugin you don't intend to use.