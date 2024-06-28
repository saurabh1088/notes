#  Privacy


## Source
What’s new in privacy
https://developer.apple.com/videos/play/wwdc2024/10123/


## Apple’s Privacy Pillars
- Data Minimisation
    - Aim for data minimisation and collect only the data which is absolutely required for App's functioning.
- On-device Processing
    - Computations should be preferred to be performed using device’s capabilities instead of server-side processes which involves exposure and could bring potential security risks.
- Transparency & Control
    - Honour user’s preferences and autonomy.
    - One should make transparent what all data app is going to collect.
    - Additionally provide user with control of if and how their data should be used
- Security Protection
    - The technical guarantees for data protection


## What iOS 18 and macOS Sequoia provide in terms of privacy?

- New Pickers : Following are some new pickers introduced this year.
    - FinanceKit
    - Image Playground
    - AccessorySetupKit
- Upgraded platform protection
    - Rotate Wifi address for Mac
    - macOS Extensions : Now system notification when an extension is installed
        - Can be enabled, disabled for Login item and extensions in system settings on macOS
    - App group container protection on macOS
- Permission Changes
    - Contacts
        - When an app request access to share contacts, the access prompt is not a two stage
        - First asks if the contacts should be shared or not
        - If selected to share on first prompt, then a second prompt is presented with option to provide a limited or
        full access
        - iOS 18 onward this will be standard flow and won’t required and API changes from developers on app side.
        - New this year is a Contact Access Button
    - Bluetooth
        - Changes to bluetooth authorisation prompts
        - Access to bluetooth can reveal a lot, hence it needs privacy
        - Updated Bluetooth prompt will now show map with current location of the device
        - Usage string should provide clear explanation on why access is required.
        - Updated prompt on iOS 18 comes without need to adopt any new API
    - Local network
        - Access to local network
        - When app attempts to access data from local network, then a prompt is shown
        - A contextual string is requires from app to show user why access is required.
- New Platform capabilities
    - Locked and hidden apps
        - Sometime one need to hand over device to other person
        - In this situation locking an app with sensitive data can help give a piece of mind.
        - iOS 18 bring in additional layer of privacy which lets people lock and hide any app
        - Locking any app will require authentication before accessing it with FaceID, TouchID, or passcode.
    - Automatic passkey upgrades
    - Private caller ID


## High level pointers for new introduced pickers
- Allow users to share only the data they want without presenting them any permission prompts
- In-context data sharing
- FinanceKit to share transactional data for apps to use and picker to allow user to choose how much to share.
- Image playground API which apps can use with providing just right amount of data, and all image generation happen on
device, with final image shared with app
- AccessorySetupKit combine all permission required for an accessory like bluetooth, camera, microphone etc into one
picker.
