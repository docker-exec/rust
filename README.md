# Docker Exec Image: Rust

A Dockerfile describing an container capable of executing Rust source files.

# Build

```sh
git clone https://github.com/docker-exec/rust.git
docker build -t dexec/lang-rust .
```

# Usage

In a directory containing a script e.g. foo.rs, run:

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.rs:/tmp/dexec/build/foo.rs \
    dexec/lang-rust foo.rs
```

## Passing arguments to the script

Arguments can be passed to the script using any of the following forms:

```
-a argument
--arg argument
--arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.rs:/tmp/dexec/build/foo.rs \
    dexec/lang-rust foo.rs \
    --arg='hello world' \
    --arg=foo \
    --arg=bar
```

## Passing arguments to the compiler

Arguments can be passed to the compiler using any of the following forms:

```
-b argument
--build-arg argument
--build-arg=argument
```

Each argument passed must be prefixed in this way, e.g.

```sh
docker run -t --rm \
    -v $(pwd -P)/foo.rs:/tmp/dexec/build/foo.rs \
    dexec/lang-rust foo.rs \
    --build-arg=-some-compiler-option \
    --build-arg=some-compiler-option-value
```
