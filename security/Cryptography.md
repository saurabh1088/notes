# Cryptography

*Greek words: kryptós, "hidden", and gráphein, "to write"*

Cryptography is the study of information hiding and verification. It includes the
protocols, algorithms and strategies to securely and consistently prevent or delay
unauthorized access to sensitive information and enable verifiability of every
component in a communication.

Cryptography in software engineering deals with securing sensitive information
and communications. It aims to

- Confidentiality
- Integrity
- Authentication
- Non-repudiation


## Types of Cryptography

- Symmetric
- Asymmetric
- Hash

### Symmetric Cryptography

*Symmetric Cryptography, which is also called private-key cryptography, uses a
key (which may be a password or digital certificate) to encode the message into
ciphertext, and the recipient uses the same key to decrypt it.*

Called symmetric as same key is used for encryption and decryption.

- Same key is used for both encryption and decryption.
- Algorithm is inexpensive
- Between the two parties sharing encrypted data, it can maintain a degree of authentication
as encryption and decryption uses same key so an encrypted data with a key can't
be decrypted by using any other key. This with assumption the key is secured by both
parties.
