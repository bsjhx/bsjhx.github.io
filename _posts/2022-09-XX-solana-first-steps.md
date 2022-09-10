## Solana: first steps
In this quick tutorial I'll show how to install development tools for Solana. After this I'll show how to run "Hello world" project from official Solana repository.

### Develompment tools installation

> :warning: All instructions are for Linux and MacOS, I'm using Mac with M1 processor.

We need to install Solana and Rust. I assume that on machine npm and git is already installed.

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
Now we want to install Solana. We can run script:
``` sh
sh -c "$(curl -sSfL https://release.solana.com/v1.11.10/install)"
```
or use homebrew:
``` sh
brew install solana
```
To check if Solana is installed properly run:
``` sh
solana --version
```
#### IDE
We also need IDE to code. I use Visual Studio Code with installed Rust plugin. There is no plugin for Solana so far.

### Running "Hello world" program
We will use Solana official program. First you have to clone repository, so run anywhere you want:
``` sh
git clone https://github.com/solana-labs/example-helloworld.git
```
Open folder _example_helloworld_ in VSC (or any other IDE). All instructions how to run hello world program are in README.md in main folder. Under _src_ directory are three folders:
- client - here is example client code, which you can use to call deployed Solana programs
- program-rust - example Solana program written in Rust
- program-c - example Solana program written in C

Short desc how to run Solana app:
1. To start Solana: 
```sh 
solana-test-validator
```
(you can add _-r_ (reset) flag to reset Solana.
2. To install dependencies:
``` sh
npm install
```
3. To build and deploy Rust program:
``` sh
npm run build:program-rust
solana program deploy dist/program/helloworld.so
```
4. Now run client to call Solana program:
``` sh
npm run start
```

You should see:
``` sh
michalrakoczy@Michas-MacBook-Pro example-helloworld % npm run start

> helloworld@0.0.1 start
> ts-node src/client/main.ts

Let's say hello to a Solana account...
Connection to cluster established: http://localhost:8899 { 'feature-set': 4253057308, 'solana-core': '1.11.10' }
Using account AmZjorjiTSKkjmuJUaC2LkNvzeYB4wZwtwEuRHhJXJ4b containing 499999998.02896285 SOL to pay for fees
Using program 5BuiArRjkZGn13GaPtcQTJrvWRHwau7Z1SKQuod3ZKso
Creating account GXTdafsatrkCXy8Vnbqr6RsuRvWcePWVo49yAZ6quNGn to say hello to
Saying hello to GXTdafsatrkCXy8Vnbqr6RsuRvWcePWVo49yAZ6quNGn
GXTdafsatrkCXy8Vnbqr6RsuRvWcePWVo49yAZ6quNGn has been greeted 1 time(s)
Success
```

I encountered problem with bpf while building Rust program. In console I saw:
``` sh
$ npm run build:program-rust

> helloworld@0.0.1 build:program-rust
> cargo build-bpf --manifest-path=./src/program-rust/Cargo.toml --bpf-out-dir=dist/program

BPF SDK: /Users/michalrakoczy/.local/share/solana/install/releases/1.8.6/solana-release/bin/sdk/bpf
cargo-build-bpf child: rustup toolchain list -v
cargo-build-bpf child: cargo +bpf build --target bpfel-unknown-unknown --release
error: no such subcommand: `+bpf`

	Did you mean `b`?
 ```
 To fix this I followed [this post](https://mattmazur.com/2021/12/07/dealing-with-no-such-subcommand-bpf/).
 
 ### Summary
 In this short post I showed how easily you can run Solana program.
