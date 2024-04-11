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

Keychain data persists even when app gets deleted. The only way to delete completely is to wipe out the device. Other apps
however won't be able to access the data.

On simulator one need to reset content settings, after which the keychain saved data will be wiped out.

Apple Developer thread on this : https://forums.developer.apple.com/forums/thread/36442


## Where is keychain data stored on in an iOS device?
Keychain stores data in SQLite database.


## Keychain vs Secure Enclave


## Can one access keychain data if the iOS device is locked?
NO, by default, keychain items are only accessible when the device is unlocked. Point to note here is that if the device
in question is not protected via Touch ID/Face ID and passcode then it is always unlocked.


## How to control access to a keychain item based on device state?
One can specify *kSecAttrAccessible* while creating query when item is added to keychain and provide applicable value as
per usecase.
