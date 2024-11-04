
npx @react-native-community/cli@latest init hello-world-using-cli
- Need to install the following packages:
- @react-native-community/cli@14.0.0
- Ok to proceed? (y) y
- error "hello-world-using-cli" is not a valid name for a project. Please use a valid identifier name (alphanumeric).
- info Run CLI with --verbose flag for more details.

npx @react-native-community/cli@latest init HelloWorldCLI        
- error Project name shouldn't contain "HelloWorld" name in it, because it is CLI's default placeholder name.
- info Run CLI with --verbose flag for more details.

npx @react-native-community/cli@latest init ReactNativeKickOffCLI

                                                          
               ######                ######               
             ###     ####        ####     ###             
            ##          ###    ###          ##            
            ##             ####             ##            
            ##             ####             ##            
            ##           ##    ##           ##            
            ##         ###      ###         ##            
             ##  ########################  ##             
          ######    ###            ###    ######          
      ###     ##    ##              ##    ##     ###      
   ###         ## ###      ####      ### ##         ###   
  ##           ####      ########      ####           ##  
 ##             ###     ##########     ###             ## 
  ##           ####      ########      ####           ##  
   ###         ## ###      ####      ### ##         ###   
      ###     ##    ##              ##    ##     ###      
          ######    ###            ###    ######          
             ##  ########################  ##             
            ##         ###      ###         ##            
            ##           ##    ##           ##            
            ##             ####             ##            
            ##             ####             ##            
            ##          ###    ###          ##            
             ###     ####        ####     ###             
               ######                ######               
                                                          

              Welcome to React Native 0.74.5!                
                 Learn once, write anywhere               

✔ Downloading template
✔ Copying template
✔ Processing template
✔ Installing dependencies
✔ Do you want to install CocoaPods now? Only needed if you run your project in Xcode directly … no
info 💡 To enable automatic CocoaPods installation when building for iOS you can create react-native.config.js with automaticPodsInstallation field. 
For more details, see https://github.com/react-native-community/cli/blob/main/docs/projects.md#projectiosautomaticpodsinstallation
            
✔ Initializing Git repository

  
  Run instructions for Android:
    • Have an Android emulator running (quickest way to get started), or a device connected.
    • cd "/Users/saurabhverma/DevBox/Hybrid/react-native/ReactNativeKickOffCLI" && npx react-native run-android
  
  Run instructions for iOS:
    • cd "/Users/saurabhverma/DevBox/Hybrid/react-native/ReactNativeKickOffCLI/ios"
    
    • Install Cocoapods
      • bundle install # you need to run this only once in your project.
      • bundle exec pod install
      • cd ..
    
    • npx react-native run-ios
    - or -
    • Open ReactNativeKickOffCLI/ios/ReactNativeKickOffCLI.xcodeproj in Xcode or run "xed -b ios"
    • Hit the Run button
    
  Run instructions for macOS:
    • See https://aka.ms/ReactNativeGuideMacOS for the latest up-to-date instructions.
    

## Run project on a particular iOS simulator

```
npx react-native run-ios --simulator='iPhone 16 Pro Max'
```

Note : Check list of booted iOS simulators and devices list using below command

```
xcrun simctl list | grep 'Booted'
```