# 🦀 rust

useful code for the crab language

## read from file

```rust
let input = fs::read_to_string("input.txt")?;
```

## read lines from file

```rust
let input: Result<Vec<String>, Error> = (fs::read("input.txt")?).lines().collect();
let input: Vec<String> = input.unwrap();
```

## compile for aws lambda

```rust
cargo build --release --target=x86_64-unknown-linux-musl
```

## compile for aws lambda (graviton)

```rust
cargo build --release --target=arm64
```
