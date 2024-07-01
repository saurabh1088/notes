# Keychain

- Keychain provide secure storage and is used to securely store small amount of data.
- Keychain is used as persistence solution for data which is small and requires secure storage.

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


## What are some functionalities Keychains provide?
1. Security
    - As mentioned before, keychain provide a secure storage for small amount of data like passowrds, keys or certificates.

2. Synchronization
    - Data can synchronized so that a user can access same across his/her various apple devices using iCloud keychain.

3. Sharing
    - Data can be shared across different apps from same developer accounts using access group.

4. Persistence
    - Data is persisted which is saved in keychain

5. Access Control
    - Keychain in iOS provides robust access control features that allow developers to specify which applications or components can access specific Keychain items. This ensures that sensitive information is protected and only accessible by authorized apps or services


## What are some real world use cases of using keychain?
1. Store user credentials securely to avoid having user login again and again providing a better user experience.
2. In an oAuth2.0 flow, store access token which need to be sent to every API call after successfull authentication and
authorisation.
3. Store user preferences which can be sensitive.