# App Startup

## AppDelegate vs SceneDelegate

### New freshly baked project choosing Storyboard as UI interface

![Xcode new project](resources/xcode-new-project-storyboard-swift.png "Xcode new project")


![Default files](resources/xcode-created-new-project-storyboard-default-files.png "Default files")


- Created project has `AppDelegate` and `SceneDelegate` both.
- When app is installed and launched first time, following sequence of delegate methods are called

```
AppDelegate : application didFinishLaunchingWithOptions
AppDelegate : application configurationForConnecting
SceneDelegate : scene willConnectTo session with options
SceneDelegate : scene sceneWillEnterForeground
SceneDelegate : scene sceneDidBecomeActive
```

- Once app is installed and it is terminated and launched again without re-install following sequence is observed

```
AppDelegate : application didFinishLaunchingWithOptions
SceneDelegate : scene willConnectTo session with options
SceneDelegate : scene sceneWillEnterForeground
SceneDelegate : scene sceneDidBecomeActive
```