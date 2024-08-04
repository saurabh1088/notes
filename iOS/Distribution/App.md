# App Distribution

## Why Code Signing?
Code signing process ensures `security` & `integrity` of the app.
The process establishes trust between:-
- The App
- The Device
- The Developer

## iOS App Code Signing
### Signing Certificate
A certificate guarantees that one knows Apple and Apple knows the developer. There is a mutual recognition. Once one gets certificate and adds to keychain, any build signed by Xcode uses this certificate which guarantees the code is coming from authorised person or team.
There are two flavours of signing certificate
- Development Certificate
    - A development certificate identifies one as a developer and contains the developer identifier.
    - Even when one signs up as an apple developer as an individual, one still have both a developer and team identifier.
- Distribution Certificate
    - Belong to the team
    - A distribution certificate contains one’s team identifier and identifies a team.

The signing certificate is a public private pair with
- Private key
    - Resides in keychain
- Public
    - User ID
    - Team ID
    - Public key


### How to create a signing certificate?
- Create a Certificate Signing Request using the keychain Access app from Mac
- This creates the public and private keys that will identify one’s certificate

### Provisioning Profiles
Following are types of provisioning profiles :
1. Development Provisioning Profile
2. Distribution Provisioning Profile - Developer Account
3. Distribution Provisioning Profiles - Enterprise Account

### How to create a development provisioning profile?
- Sign in with developer account on http://developer.apple.com
- Go to Certificate, Identifier and Profiles
- Under profiles there should be a + button to add a new profile.
- Tap + and under Development select appropriate type of profile needed.
- Select the App ID needed for development
- Select all development certificates which are needed
- Select devices which are required
- Enter a profile name, and generate then download


## TODOs
- [x] Move size classes to proper place.


https://www.bounteous.com/insights/2018/08/08/demystifying-ios-app-provisioning-process
