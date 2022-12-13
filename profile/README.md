# Black Lager
Black Lager is a text messaging application with digital signatures built on top of [Meshtastic](https://github.com/meshtastic) that runs without cell service or internet connection. Data is sent over a radiomesh network of small, power-efficient, long-range radio devices. Black Lager offers additional security features such as digital signature for authentication.

## Website
More information about the project can be found on [our website](https://black-lager.github.io/). The code for the website is in [this repo](https://github.com/black-lager/black-lager.github.io).

## Firmware
Radio devices must be flashed with the Black Lager software. The firmware, information on supported hardware, and flashing instructions can be found in [the firmware repo](https://github.com/black-lager/firmware).

## Python application
The Black Lager text messaging client is a Python application which runs a computer connected to a flashed radio device via USB cable. To install the application run the command:

```bash
pip3 install blacklager
```

More information about the app can be found in [the python repo](https://github.com/black-lager/python).

## Security
### Digital Signature
[Ed25519](https://ed25519.cr.yp.to/) supports digital signatures. It is a 
a digital signature scheme using a variant of the Schnorr signature based on twisted Edwards curves. Ed25519 is immune to cache-timing attacks, hyper-threading attacks, and other side-channel attacks that rely on the leakage of addresses through the CPU cache. Ed25519 never performs conditional branches based on secret data; the pattern of jumps is completely predictable. Which makes it immune to side-channel attacks that rely on the leakage of information through the branch-prediction unit. Lastly, It does not use a randomly generated nonce but instead computes signature nonces from a combination of a hash of the signing key’s “seed” and the message to be signed. This avoids using an entropy source for nonces, which can be a potential attack vector if the entropy source is not generating good random numbers. 
### Public Key Encryption
[Curve25519](https://www.iacr.org/cryptodb/archive/2006/PKC/3351/3351.pdf) supports public key encryption. Curve25519 encrypts a package/data to prevent attacks such as man-in-the-middle attacks and eavesdropping. Hackers need a large amount of computing power to crack an encrypted package. Every known attack is more expensive than performing a brute-force search on a typical 128-bit secret-key cipher. 
### Diffie-Hellman
[Diffie-Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) key exchange is a mathematical method for securely exchanging cryptography keys over a public channel. Each person generates a public/private key pair and then broadcasts their public key.
Given a user's 32-byte secret key, Curve25519 computes the user's 32-byte public key. Given the user's 32-byte secret key and another user's 32-byte public key, Curve25519 computes a 32-byte secret shared by the two users. This secret can then be used to authenticate and encrypt messages between the two users.
Each set of two Curve25519 users has a 32-byte shared secret used to authenticate and encrypt messages between the two users. The following picture shows the data flow from secret keys through public keys to a shared secret. 


## Open Source Contribution
Our entire project is open-source and we built on top of Meshtastic open-source software. In addition to bug fixes we contributed to the Meshtastic project, our contribution to the project was our security assessment and setting up protocol buffer messages for public keys.
Defined a Persona and Wallet protobuf message to build a foundation to support strong device and client identity core value. More security information can be found [here](https://meshtastic.org/docs/overview/encryption). The protocol buffer messages are currently in the process of being merged into the [Meshtastic protobuf repository](https://github.com/meshtastic/protobufs). [Here is a link to the pull request](https://github.com/meshtastic/protobufs/pull/251). 
