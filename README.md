## Abouts

### What is ZKEncrypt FHE

**ZKEncrypt FHE** is a high-performance Rust implementation of Fully Homomorphic Encryption (FHE) for boolean and integer arithmetics over encrypted data, powering the ZKEncrypt AI ecosystem.

It includes:
- a **Rust** API
- a **C** API
- and a **client-side WASM** API

ZKEncrypt FHE is designed for developers building privacy-preserving AI applications who want full control over FHE operations while leveraging production-ready, high-performance cryptographic primitives.

### Main Features

- **Low-level cryptographic library** implementing TFHE with programmable bootstrapping
- **Boolean API** for encrypted boolean operations
- **Short integer API** enabling exact, unbounded FHE integer arithmetics with up to 8 bits of message space
- **Size-efficient public key encryption**
- **Ciphertext and server key compression** for efficient data transfer
- **Full Rust API, C bindings, and client-side JavaScript API using WASM**
- **Optimized for ZKEncrypt AI** ecosystem integration

## Table of Contents
- **[Getting Started](#getting-started)**
   - [Cargo.toml Configuration](#cargotoml-configuration)
   - [A Simple Example](#a-simple-example)
- **[Resources](#resources)**
   - [Documentation](#documentation)
   - [ZKEncrypt AI Ecosystem](#zkencrypt-ai-ecosystem)
- **[Working with ZKEncrypt FHE](#working-with-zkencrypt-fhe)**
   - [Contributing](#contributing)
   - [License](#license)
- **[Support](#support)**

## Getting Started

### Cargo.toml Configuration

To use **ZKEncrypt FHE** in your project, add it as a dependency in your `Cargo.toml`:

```toml
[dependencies]
zkencrypt-fhe = "1.0"
```

### A Simple Example

Here is a simple example of homomorphic addition using ZKEncrypt FHE:

```rust
use zkencrypt_fhe::prelude::*;
use zkencrypt_fhe::{generate_keys, ConfigBuilder, set_server_key};

fn main() {
    // Generate keys
    let config = ConfigBuilder::default().build();
    let (client_key, server_key) = generate_keys(config);
    
    // Set the server key for homomorphic operations
    set_server_key(server_key);
    
    // Encrypt two values
    let a = FheUint8::encrypt(15u8, &client_key);
    let b = FheUint8::encrypt(27u8, &client_key);
    
    // Perform homomorphic addition
    let result = a + b;
    
    // Decrypt the result
    let decrypted: u8 = result.decrypt(&client_key);
    println!("Result: {}", decrypted); // Output: 42
}
```

## Resources

### Documentation

- **[ZKEncrypt AI Documentation](https://zkencrypt-ai.gitbook.io/zkencrypt-ai)** - Complete guide to the ZKEncrypt ecosystem

### ZKEncrypt AI Ecosystem

- **[Website](https://zk-labs.network)** - Official ZKEncrypt AI website
- **[Twitter](https://twitter.com/ZKEncrypt_AI)** - Latest updates and announcements  
- **[GitHub](https://github.com/ZKEncrypt-AI)** - Source code and projects

### Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### License

ZKEncrypt FHE is licensed under the **BSD 3-Clause Clear License**, the same license as the upstream tfhe-rs project.

## Support

- **Issues**: Report bugs and request features via [GitHub Issues](https://github.com/ZKEncrypt-AI/zkencrypt-fhe/issues)
- **Twitter**: Follow [@ZKEncrypt_AI](https://twitter.com/ZKEncrypt_AI) for updates
- **Email**: Contact us at support@zk-labs.network

---

**Built with ❤️ by ZKEncrypt AI**
