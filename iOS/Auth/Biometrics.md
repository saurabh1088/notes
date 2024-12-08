# Face-ID/Touch-ID and Auth


## 1. oAuth2.0 with Face-ID

### 1.1 User logs in for the first time
- Regular oAuth2.0 flow.
- Post successfull authentication, app can display alert or screen prompting user to opt for Face-ID/Touch-ID for future
login attemps.

### 1.2 User enables Face-ID
- User enables Face-ID for future login.
- Encrypt a unique identifier and store it in keychain.
- Keychain storage policy for this identifier should be Face-ID authentication for access.
- Update user preferences for the app to register that user has enabled Face-ID for login.
