# Mobile App Security

Here are some important aspects one needs to take into considerations or have implement in a mobile application to have
a secure mobile application.

## 1. Secure Communication Protocol
App should use a secure communication protocol i.e. HTTPS/TLS. 

### App Transport Security
On Apple platforms there is a networking feature known as *App Transport Security*. Security checks imposed by ATS.
- ATS mandates that all HTTP connections using URL Loading System MUST use HTTPS.
- ATS mandates use of Transport Layer Security (TLS) version 1.2 or later.
- ATS mandates default server trust evaluation
- ATS mandates that the server with which app is connecting to, should meet certain requirements.

There are several other requirements which are discussed on Apple's documentation : https://developer.apple.com/documentation/security/preventing_insecure_network_connections

ATS will block network connections if they fail to meet the security specifications.
ATS operates by default and there is no setting to turn it on. System will enforce ATS by default when one uses URL loading
system.

One can add exceptions to ATS checks by adding key NSAppTransportSecurity to Info.plist

### SSL Pinning
One should implement SSL Pinning so as to prevent MITM attacks. Discussed in details here:

https://github.com/saurabh1088/notes/blob/main/iOS/Security/SSLPinning.md


## 2. Authentication & Authorization
App should implement way to authenticate and authorize user to prevent fraudulent access. One can implement oAuth2.0 as
discussed here:

https://github.com/saurabh1088/notes/blob/main/iOS/Auth/oAuth2PointO.md


## 3. Encryption
Any sensitive data handled by mobile app, should be encrypted with string encryption algorithms. If requirement is to store
any sensitive data then keychain must be used instead of storing it in no secure options like user defaults.
Logging is necessary for debugging issues later on, however one must take proper care to make sure not to log any sensitive
data. Any sensitive data present should be made sure to be masked before logging.


## Data Storage
App, if stores data, then effective measures must be taken to ensure data security. One aspect is to make sure to encrypt
any sensitive data if getting stored. Use keychain for sensitive data storage.

### Encrypting App’s Files
Often one saves files in app's directory, while saving files, one should use built-in data protection API features which
allow to specify the level of protection for a file.


## 4. Check for Jailbreaking
Jailbreaking an iOS device gives unauthorized privileges and root access to malicious applications. On iOS Platforms, App
store is the only way to distribute and install apps. This means every app available on App store has went through Apple's
inspection and reduces the risk of user installing malicious apps.
Jailbreaking allows a user to install non approved apps. So a jailbroken app can hack into other apps installed on the device
and could be potential security issue.

So one can consider having app check for device jailbreaking. Note, there is no foolproof method existing to detect it though.


## 5. Check OWASP Top 10
OWASP also releases top security vulnerabilities identified for mobile applications and this list is regularly updated.
One should take a look at this list and check if the mentioned vulnerabilities also applied to their own apps.

https://owasp.org/www-project-mobile-top-10/

## Notes Dump
## TODO: Refine this

App Sandbox

All iOS, iPad apps are only available via App store. All apps are sandboxed.
Sandboxing helps in protecting user data from any unauthorised access.
Sandboxing is designed to prevent apps from getting or modifying stored information about other apps.
With sandboxing each app gets a unique directory for its files. This directory gets randomly assigned when app is installed.
System files and resources are also shielded from user’s apps, access to those are only through if required via services provided by platform. For example an app might want to use camera roll for photos.

Mandatory Code Sign

All executable code need to be code signed using an Apple issued certificate

Entitlements

Several features such as iCloud are controlled using declaring entitlements. Entitlements are key-value pairs and are signed into app, since digitally signed, entitlements can’t be changed. Basically entitlements enable to run some privileged operation which otherwise may have required to sign as root.

Address Space Layout Randomisation (ASLR)

ASLR is a security mitigation which is basically found in most of systems today. It’s not exclusive to apple platforms.
Protection against exploitation of memory corruption bugs. Built-in apps use ASLR and randomise all memory regions upon app launch.
ASLR will also randomise memory addresses of executable codes , system libraries etc reducing the security risks associated with memory exploits. Xcode supports iOS, iPad apps to automatically compile with ASLR support turned on.

https://bellis1000.medium.com/aslr-the-ios-kernel-how-virtual-address-spaces-are-randomised-d76d14dc7ebb

Execute Never feature

Execute Never (XN) feature marks memory pages as non-executable preventing unwanted modifications. Memory pages which are marked both writable and executable can only be used by apps under tightly controlled conditions.


Data Protection API

Secures App files and prevent unauthorised access to them. It’s enabled as soon as a user sets a passcode on his/her device.


