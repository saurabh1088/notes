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

### 1.3 User logs in using Face-ID
- App launches and detects Face-ID is enabled for the app.
- Using Local Authentication Framework user is prompted for Face-ID authentication.
- If Face-ID authentication succeeds then proceed to retrieve stored identifier from keychain.
- If Face-ID fails, proceed for manual login.

### 1.4 User disables Face-ID for App
- On disable, delete stored unique identifier from keychain.
- Update app preferences to indicate user has disabled Face-ID for app so it shouldn't prompt for the same.

### 1.5 User deletes and re-configures Face-ID on his/her device
- LAContext's canEvaluatePolicy can help determine if Face-ID is unavailable/deleted/reconfigured.
- If Face-ID is deleted, prompt user if Face-ID need to be enabled again.
- Re-store unique identifier in keychain.
