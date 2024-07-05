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

