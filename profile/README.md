# Black-Lager
![alt text](https://e7.pngegg.com/pngimages/1020/733/png-clipart-pilsner-glass-filled-with-black-liquid-beer-style-stout-guinness-brewery-dark-beer-food-beer-bottle-thumbnail.png)
Black-Lager is a messaging application that doesn't rely on cell service or internet. Data is sent over a mesh network of small, but power-efficient and long-range radio devices. Black-Lager offers additional security features such as digital signature to ensure mutual authentication. 
## Website
We also have a website! Come check [it](https://black-lager.github.io/) out. 


## Encryption
### Digital Signature
[Ed25519](https://ed25519.cr.yp.to/) supports digital signatures. It is a 
a digital signature scheme using a variant of the Schnorr signature based on twisted Edwards curves. Ed25519 is immune to cache-timing attacks, hyper-threading attacks, and other side-channel attacks that rely on the leakage of addresses through the CPU cache. Ed25519 never performs conditional branches based on secret data; the pattern of jumps is completely predictable. Which makes it immune to side-channel attacks that rely on the leakage of information through the branch-prediction unit. Lastly, It does not use a randomly generated nonce but instead computes signature nonces from a combination of a hash of the signing key’s “seed” and the message to be signed. This avoids using an entropy source for nonces, which can be a potential attack vector if the entropy source is not generating good random numbers. 
### Public Key Encryption
[Curve25519](https://www.iacr.org/cryptodb/archive/2006/PKC/3351/3351.pdf) supports public key encryption. Curve25519 encrypts a package/data to prevent attacks such as man-in-the-middle attacks and eavesdropping. Hackers need a large amount of computing power to crack an encrypted package. Every known attack is more expensive than performing a brute-force search on a typical 128-bit secret-key cipher. 
### Diffie-Hellman
[Diffie-Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange) key exchange is a mathematical method for securely exchanging cryptography keys over a public channel. Each person generates a public/private key pair and then broadcasts their public key.
Given a user's 32-byte secret key, Curve25519 computes the user's 32-byte public key. Given the user's 32-byte secret key and another user's 32-byte public key, Curve25519 computes a 32-byte secret shared by the two users. This secret can then be used to authenticate and encrypt messages between the two users.
Each set of two Curve25519 users has a 32-byte shared secret used to authenticate and encrypt messages between the two users. The following picture shows the data flow from secret keys through public keys to a shared secret. 



## Open source contribution
Generated Persona Protobuf definition to build a foundation to implement future phases of security improvement. [Link to PR](https://github.com/meshtastic/protobufs/pull/251). 

