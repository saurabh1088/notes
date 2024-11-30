# Cryptography

*Greek words: kryptós, "hidden", and gráphein, "to write"*

Cryptography is the study of information hiding and verification. It includes the protocols, algorithms and strategies
to securely and consistently prevent or delay unauthorized access to sensitive information and enable verifiability of
every component in a communication.

Cryptography in software engineering deals with securing sensitive information and communications. It aims to

- Confidentiality
- Integrity
- Authentication
- Non-repudiation (a user cannot deny (repudiate) having performed a transaction)


## Types of Cryptography

- Symmetric
- Asymmetric
- Hash

### Symmetric Cryptography

*Symmetric Cryptography, which is also called private-key cryptography, uses a key (which may be a password or digital
certificate) to encode the message into ciphertext, and the recipient uses the same key to decrypt it.*

Called symmetric as same key is used for encryption and decryption.

- Same key is used for both encryption and decryption.
- Algorithm is inexpensive
- Between the two parties sharing encrypted data, it can maintain a degree of authentication as encryption and decryption
uses same key so an encrypted data with a key can't be decrypted by using any other key. This with assumption the key is
secured by both parties.
- The most commonly used symmetric algorithm is the Advanced Encryption Standard (AES)

Usage for Symmetric Cryptography
- Due to better performance and faster speed of symmetric encryption (compared to asymmetric), symmetric cryptography is
typically used for bulk encryption / encrypting large amounts of data, e.g. for database encryption.

Drawbacks
- Weakest aspect of Symmetric Cryptography is key management.


### Asymmetric Cryptography

Uses public and private key pairs. While sending an encrypted message to recipient, the sender uses the public key of
recipient to encrypt the message. As it is public key, it is shared and needs no protection. Now when the recipient receives
the encrypted message, it can decrypt the message using the corresponding private key, which only the recipient has with it.

An algorithm generates these public and private key pairs, these are keys are different but related to each other mathematically.

Each time one visits a website using https, we are dealing with asymmetric cryptography.


## TLS/SSL

TLS : Transport Layer Security
SSL : Secure Socket Layer

TLS and SSL are cryptographic protocols providing secure communication over network.
TLS is an updated version of SSL and was introduced as a successor to SSL. All versions of SSL are now deprecated, however
one finds term SSL describing TLS connection frequently. Terms SSL, SSL/TLS nowadays refers to TLS protocol for most of the
cases.
