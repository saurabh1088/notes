# Keychain

Keychain provide secure storage and is used to securely store small amount of data.
Keychain is used as persistence solution for data which is small and requires secure storage.

One can store
- passwords
- cryptographic keys
- certificates
etc in the keychain.

Any item stored in keychain is packaged as a keychain item. This packaging means that the keychain item stored is composed
of the data itself as well as some publicly visible attributes.