# Crypto From Scratch

A small Python project where I tried to write a few classic crypto algorithms without using a crypto library for the actual algorithms.

The main point of this repo is learning. I wanted to see what is actually happening inside AES, RSA and SHA-256 instead of only calling a library function and moving on.

## What is in here?

- AES-128 block encryption
- AES-128 in CTR mode
- RSA key generation, encryption/decryption, and a simple RSA-style signature demo
- SHA-256
- Some number theory helpers used by RSA
- PKCS#7 padding
- Small utility functions
- Tests for the important parts
- A couple of runnable examples

## Important warning

This is **not** a cryptography library for real applications.

Some parts are deliberately simplified because this is a learning project. In particular, the RSA examples do not implement modern RSA-OAEP or RSA-PSS, and the CTR helper does not authenticate the ciphertext.

For real software, use a reviewed library such as a standard cryptographic package instead of copying code from this repository.

## Requirements

- Python 3.10 or newer
- pytest for running the tests
- No third-party package is needed by the crypto code itself

## Run it

From the project directory:

```bash
python -m pytest
python examples/aes_demo.py
python examples/rsa_demo.py
```

If the package is not installed, the example scripts add `src` to `sys.path` so they can still be run directly.

## Project layout

```text
crypto-from-scratch/
├── README.md
├── LICENSE
├── pyproject.toml
├── src/
│   └── crypto/
│       ├── __init__.py
│       ├── aes.py
│       ├── number_theory.py
│       ├── padding.py
│       ├── rsa.py
│       ├── sha256.py
│       └── utils.py
├── tests/
│   ├── test_aes.py
│   ├── test_rsa.py
│   └── test_sha256.py
├── examples/
│   ├── aes_demo.py
│   └── rsa_demo.py
└── docs/
    └── mathematics.md
```

## Why I made it

I am more interested in understanding the mechanics than having a perfect API here. There are plenty of good crypto libraries already. Rewriting the algorithms is useful for seeing things like finite-field arithmetic, modular exponentiation, message padding, hash compression rounds, and how RSA gets its keys.

The code is intentionally readable instead of being super optimized.
