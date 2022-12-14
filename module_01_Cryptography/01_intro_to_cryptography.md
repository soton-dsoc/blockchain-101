# Lecture 1: Introduction to Cryptography

This lecture focuses to cover the basic of cryptographic methods. Introduces to different hashing algorithms and types of encryption

## Context

### Some theory

**Cryptography**

Practice of techniques to ensure secure communication in the presence of adversary behaviour

In modern systems, cryptography is applied within the network and storage context.

Why?

Any medium of communication can be intercepted. Hence, we need to ensure that no sensitive information can be maliciously read.
This leads to the the principle behind closed vs open channels described by Kerckhoff:

Security should not rely on secret methods, but rather on secret information.

Meaning: we should not focus on creating secure/closed channels but instead focus on ensuring the security of data that is transferred through these channels.

### Applications

- End-to-end Encryption
- Storing Data
- Storing Passwords

## Methods

### **Cryptographic** Hash functions

A hash function is a function that converts any arbitrary data into a random, fixed sized data. One can see it as a way to generate a unique fingerprint for any arbitrary data. The output of a hash function, the generated fingerprint, is usually referred to as hash values, hash codes, digests, or simply hashes. 

> show exapmle in online hash tool

### Properties to ensure security

**Determinism:** — A hash algorithm should be deterministic, meaning that it always gives you an output of identical size regardless of the size of the input you started with.

**Pre-image attack resistance:** It should be infeasible to reverse a hash value to recover the original input plaintext message. Hence, the concept of hashes being irreversible, one-way functions.

**Second pre-image resistance:** It should be practically impossible to come up with the data that results in the same hash given that we know the original value and the hash.

**Collision resistance:** It should be infeasible to come up with different data that results in the same hash

*There can be non-cryptographic hash functions* that are not one-way and are suspectable to the attack listed above.

### Other properties

- Accept unbounded size input
- Map to a bounded output
- Be fast to compute

### Applications of hash functions

* Representation of larger data
* Keys in a database
* Digital signatures
* Key derivation
* Psudo-random functions

### Examples
* xxHash (non-cryptographic)
* MD5
* SHA1
* RIPEMD-160
* SHA2-256
* SHA3
* Keccak
* Blake2

> show exapmle in online hash tool and mention diffrences 

## Encryption methods

Encryption is the principal application of cryptography; it makes data incomprehensible in order to ensure its confidentiality.

Encryption uses an algorithm called a <em>cipher</em> and a secret value called the <em>key</em>

<em>plaintext:</em> unencrypted message 

<em>ciphertext:</em> encrypted message

A cipher is therefore composed of two functions: <em>encryption</em> turns a plaintext into a ciphertext, and <em>decryption</em> turns a ciphertext back into a plaintext.

- Symmetric encryption: the key used to decrypt is the same as the key used to encrypt

- Asymmetric encryption: the key used to decrypt is different from the key used to encrypt

### Symmetric encryption

Some functions that, given some data and a key, produces a hash that is 
reversible given the original key.

> briefly explain end demonstrate an exampe of Caesar Cipher

**Example**
```
let key = [Encryption key]
let x = [Some original data]
let y = [Encrypted data from "x"]
let encrypt = [Symmetric encryption function]

// encrypt data
x = encrypt(x, key)
// decrypt data
y = encrypt(y, key)
```
### Common symmetric encryption functions
* ChaCha20
* Twofish
* Serpent
* Blowfish
* AES
* DES,
* XOR

**XOR encryption**

```text
Plain: 1010  -->Cipher: 0110
Key:   1100  |          1100
       ----  |          ----
       0110--^          1010
```

**TODO: Add examples in Rust**

### Asymmetric encryption 

In asymmetric encryption, there are two keys: one to encrypt
and another to decrypt: 

<em>Public Key:</em> Encryption - is generally considered publicly available to anyone who wants to send encrypted messages

<em>Private Key:</em> Decription - must remain secret

* User A (A) generated a pair of key: Public and Private
* Public key is shared with public
* User B (B) wants to sends a secret message to A
* B uses a public key of A to encrypt a message
* Message is sent to A
* A uses their private key to decrypt B's message

### Common asymmetric encryption functions

- RSA, Elgamal, Elliptic Curve (slowest to fastest)
- Elliptic Curve Cryptography (ECC) includes:
  - ECDSA (SECP256k1, SECP256r1)
  - Schnorr
  - EdDSA (Ed25519, Ed448)
  - Schnorr/Ristretto 25519
  - BLS
- ECC requires double the bits to the symmetric AES for the same level of security. E.g. 128 bit security requires a 256 bit ECC key.

## Considerations

* Symmetric cryptography is much faster but requires more setup and trust
* Asymmetric cryptography is slow but maintains relationships such that less trust is required
* Both can be used in different parts of a system in hybrid cryptography
  * Symmetric encryption can provide speed and confidentiality
  * Asymmetric can dictate relations among the participants

Symmetric and Asymmetric encryptions are sometimes used together. For example for HTTPS asymmetric encryptions is used to transfer the symmetric key

## Recap

Cryptography allows us:
- Safely communicate on networks
- Trustlessly ensure security and integrity of transferred data
- Represent large amounts of data
- Access information


## Additional reading
- https://www.geekabyte.io/search/label/Cryptography101
- https://tonybox.net/posts/ecb-penguin/
- https://substrate.stackexchange.com/questions/982/why-does-the-all-0-public-key-have-a-known-private-key-in-sr25519-and-ed25519
