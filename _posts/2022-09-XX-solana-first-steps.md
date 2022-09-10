## Solana: first steps
### Develompment tools installation

> :warning: All instructions are for Linux and MacOS, I'm using Mac with M1 processor.

We need to install Solana and Rust. I assume that on machine npm is already installed.

#### Rust installation
To install Rust locally, run:

``` sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh 
```

On Mac, you can also use homebrew:

``` sh
brew install rust
```

To check if Rust is installed run:
``` sh
 rustc -V
```
You should see installed version. For more details visit official [Rust page](https://www.rust-lang.org/tools/install).

#### Solana installation
Now we want to install Solana.
