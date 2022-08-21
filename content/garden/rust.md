---
title: "Rust 🦀"
date: 2022-01-01
lastmod: 2022-08-21
draft: false
garden_tags: ["rust"]
summary: "Code snippets with useful stuff about Rust"
status: "seeding"
---
Code snippets wih useful stuff about Rust

## Read/write files [^1]
```rust
use std::fs;

fn main() {
    let data: String = fs::read_to_string("file-to-read.txt").expect("Unable to read file");
    println!("{}", data);
}
```

#### Read a file as a Vec\<u8>
```rust
use std::fs;
fn main() {
    let data: Vec<u8> = fs::read("file-to-read.txt").expect("Unable to read file");
    println!("{}", data);
}
```

#### Write to a file
```rust
use std::fs;

fn main() {
    let data: String = "Some data!";
    fs::write("/tmp/file-to-write.txt").expect("Unable to write a file");    
}
```

[^1]: <a href="https://stackoverflow.com/questions/31192956/whats-the-de-facto-way-of-reading-and-writing-files-in-rust-1-x" target="_blank">What is the de-facto way of reading and writing files in Rust.</a>

## Insert or replace multiple items in a Vec [^2]
```rust
let mut vec = vec![1, 5];
let slice = &[2, 3, 4];

let index = 1;

vec.splice(index..index, slice.iter().cloned());

println!("{:?}", vec); // [1, 2, 3, 4, 5]
```

[^2]: <a href="https://stackoverflow.com/questions/28678615/efficiently-insert-or-replace-multiple-elements-in-the-middle-or-at-the-beginnin" target="_blank">Efficiently insert or replace multiple elements in the middle or at the beginning of a Vec.</a>