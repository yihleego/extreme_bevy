# README

## Native

```
cargo run
```

## Web

First, make sure you have a rust wasm toolchain installed. With rustup, it's simply:

```
rustup target install wasm32-unknown-unknown
```

That's enough to build the project for the web.

```
cargo build --target wasm32-unknown-unknown
```

However, that will just leave us with a wasm file in the target directory. In order to easily test our project while developing, we'll install wasm-server-runner:

```
cargo install wasm-server-runner
```

And configure our project to use it by adding a new file, .cargo/config.toml inside our repo:

```
[target.wasm32-unknown-unknown]
runner = "wasm-server-runner"
```

Now, when we run the project for the wasm target, it will start a local web server and log the link in the terminal:

```
cargo run --target wasm32-unknown-unknown
```

Before we go on, I have one more tip that will make things easier: Install cargo-watch as well:

```
cargo install cargo-watch
```

With it, you can detect changes in the project directory, and automatically rebuild and relaunch the server:

```
cargo watch -cx "run --target wasm32-unknown-unknown"
```

Now, when you want to test a change, you simply have to save and refresh your browser.

If you find it tiresome to type wasm32-unknown-unknown all the time, you can set it as your default target in .cargo/config.toml:

```
[build]
target = "wasm32-unknown-unknown"
```

And start developing with:

```
cargo watch -cx run
```
