# Containerd Spin Shim

## General Information

Forked from [deislabs/containerd-wasm-shims](https://github.com/deislabs/containerd-wasm-shims).

## Build Information

1. Before building, make sure to do the following customizations to the source code (`src/main.rs`), adjusting it to your environment:

    - Change the following line, replacing the Redis server information:

        ```rust
        let client = redis::Client::open("redis://:password@127.0.0.1:9898?db=0");
        ```

2. Install required packages and Rust:

    ```bash
    apt update
    apt install build-essential
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```

3. Build the shim binary:

    ```bash
    cargo build --release
    ```

4. Copy the built shim binary from `target/release/containerd-shim-spin-v1` to the Kubernetes cluster nodes. More details are available in the [wasm-orchestration/wasm-orchestration-scripts](https://gitlab.com/wasm-orchestration/wasm-orchestration-scripts) repository.