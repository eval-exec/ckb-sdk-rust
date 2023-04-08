
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
use ckb_sdk::rpc::CkbRpcClient;

let mut ckb_client = CkbRpcClient::new("https://testnet.ckb.dev");
let block = ckb_client.get_block_by_number(0.into()).unwrap();
println!("block: {}", serde_json::to_string_pretty(&block).unwrap());
```

For more details about CKB RPC APIs, please refer to the [CKB RPC doc](https://github.com/nervosnetwork/ckb/blob/master/rpc/README.md).

### Build transaction by manual

```rust

```

### Sign and send transaction

```rust

```

### Generate a new address

```rust
use ckb_sdk::types::{Address, AddressPayload, NetworkType};
use rand::Rng;

let mut rng = rand::thread_rng();
let privkey_bytes: [u8; 32] = rng.gen();
let secp_secret_key = secp256k1::SecretKey::from_slice(&privkey_bytes).unwrap();
let pubkey =
    secp256k1::PublicKey::from_secret_key(&ckb_crypto::secp::SECP256K1, &secp_secret_key);
let payload = AddressPayload::from_pubkey(&pubkey);
let address = Address::new(NetworkType::Mainnet, payload, true);
println!("address: {}", address.to_string());
```

For more details please about CKB address refer to [CKB rfc 0021](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0021-ckb-address-format/0021-ckb-address-format.md).


## Examples

* [`transfer_from_sighash.rs`](examples/transfer_from_sighash.rs) Transfer capacity from a sighash address
* [`transfer_from_multisig.rs`](examples/transfer_from_multisig.rs) Transfer capacity from a multisig address (main logic is less than 60 lines of code)

For more use cases of building transactions with CKB node, please refer to [these examples](./examples/).

## License

The SDK is available as open source under the terms of the [MIT License](./LICENSE).

## ChangeLog

See [CHANGELOG](CHANGELOG.md) for more details.


[ckb]: https://github.com/nervosnetwork/ckb
