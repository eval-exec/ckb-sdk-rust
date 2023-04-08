
# CKB SDK Rust

Rust SDK for Nervos [CKB][ckb].

## Install

```toml
# Cargo.toml
[dependencies]

ckb-sdk = "2.5.0"
```

## Build

Build:

```bash
cargo build
```

Run unit tests:

```
make test
```

Please refer to the [Makefile](./Makefile) for more compilation commands.

## Quick start

### Setup

ckb-sdk-rust provides a convenient client that enables you to easily interact with CKB nodes.

```rust
use ckb_rpc::rpc::CkbRpcClient;

let mut ckb_client = CkbRpcClient::new("https://testnet.ckb.dev");
let block = ckb_client.get_block_by_number(0.into()).unwrap();
println!("> block: {}", serde_json::to_string_pretty(&block).unwrap());
```

For more details about CKB RPC APIs, please refer to the [CKB RPC doc](https://github.com/nervosnetwork/ckb/blob/master/rpc/README.md).

### Build transaction by manual

### Sign and send transaction

## Examples

* [`transfer_from_sighash.rs`](examples/transfer_from_sighash.rs) Transfer capacity from a sighash address
* [`transfer_from_multisig.rs`](examples/transfer_from_multisig.rs) Transfer capacity from a multisig address (main logic is less than 60 lines of code)

For more use cases of building transactions with CKB node, please refer to [these examples](./examples/).

## License

The SDK is available as open source under the terms of the [MIT License](./LICENSE).

## ChangeLog

See [CHANGELOG](CHANGELOG.md) for more details.


[ckb]: https://github.com/nervosnetwork/ckb
