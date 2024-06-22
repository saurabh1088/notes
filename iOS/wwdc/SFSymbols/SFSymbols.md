#  SF Symbols


## WWDC 2019
Introducing SF Symbols
https://developer.apple.com/videos/play/wwdc2019/206

- SF Symbols are in Vector form, which means these are highly scalable. 
- These comes with weights which match system fonts.
- SF Symbols can be localised.
- `SymbolConfiguration` : For example if one wants to change scale.
- `UIImageView` has new property `preferredSymbolConfiguration`

_Symbol point sizes are not equal to Screen point sizes._

- With SF Symbols one need to use symbols point size instead of dimensions.
- What this means is the while using SF Symbols, one should not put constraints on it using frames, width and height. Doing
so will not give good results. Instead one should use as appropriate point size. Using point size will size the symbol with
best outcome and also results in better performance.

- New API, One can create a UIKit system button with any SF Symbol.

SF Symbols have default rendering mode as alwaysTemplate

- Prefer horizontal and vertical centering over x and y coordinates
- Build layout from smallest to largest
- Caching images rarely helps performance
- Avoid rasterizing : Try to avoid rasterising images specially SF symbol images.


## WWDC 2020
SF Symbols 2
https://developer.apple.com/videos/play/wwdc2020/10207/

### Higlights
- Multicoloured symbols are introduced this year

### There are three scales SF Symbol can use, small, medium and large, what is the default one?
The default scale used for SF Symbols is medium

### How does the scales compare within themselves
Small < ~ 20% Medium < ~30% Large

Small scale is approximately 20% less than the medium one and large one is approximately 30% larger than the medium one.


## WWDC 2021
What’s new in SF Symbols
https://developer.apple.com/videos/play/wwdc2021/10097


### Learnings
- Scales small, medium and large, maintain the point size, so same point size can be used with all these three scales.
- Symbol Variants
    - Following are few variants one can use for SF Symbols
        - outlined
        - slash
        - circle
        - square
        - rectangle
        - fill
    - The default variant of SF symbol is the outlined variant.


- Rendering Modes
    - New rendering modes added
        - Hierarchical (New)
            - Uses single color with varying opacity, creating depth and emphasis
        - Palette (New)
            - Gives possibility to use two or more contrasting colours
            - Each color can be controlled independently
        - Multicolor (Existing)
        - Monochrome (Existing)


## WWDC 2022
What's new in SF Symbols 4
https://developer.apple.com/videos/play/wwdc2022/10157

- SF Symbols are designed with typography in mind.
- SF Symbols have some awesome features like 
    - different weight, 
    - scales, 
    - outlined and filled variants, 
    - encapsulated shapes,
    - alignments.

### Automatic Rendering
Monochrome used to be the default rendering mode, but now rendering mode will be automatically adjusted to choose the
best symbol as per symbol’s unique characteristics. This is due the symbols having a preferred rendering mode.
This behaviour is called as Automatic Rendering.

### Variable Color
Different layers, with some layers participating in variable color feature to represent some variable values for example
a volume, signal strength etc.
Variable color is opacity based and is available for all rendering modes.

## WWDC 2023
What’s new in SF Symbols 5
https://developer.apple.com/videos/play/wwdc2023/10197

### Animation : New Feature
One can choose from a collection of different configurable animation presets, each with its own unique characteristics.
These work on all symbols, in all scales, and all rendering modes, making symbols even more customizable than before.

Each symbol in library has a unified layer structure that defines it. These layer play important role in the way color
is applied to a symbol. Similarly layers play important role in the way symbol animate as well.

By default symbol will animate by layer, which implicates animation happens one layer at a time. One can however choose 
to animate whole symbol at once if that makes sense for the app and use case.

Animation Presets :
- Appear
- Disappear
- Bounce
- Scale
- Pulse
- Variable Color
- Replace


## WWDC 2023
Animate symbols in your app
https://developer.apple.com/videos/play/wwdc2023/10258


Symbols Framework
- Symbols Framework is home to all symbol animations.
- One need not to import this framework as it's included by default while working with SwiftUI, UIKit and AppKit.
- Each effect has a simple dot separated name.
    - For example for bounce effect one should write .bounce
- Effect names are real Swift code and not strings.
- SF Symbols app has a new animations tab where one can learn about animation configuration options and copy a effect configuration as well


Behaviours of animation
- Discrete (For eg. bounce)
- Indefinite (For eg. scale)
- Transition (For eg. appear/dissappear)
- Content Transition (For eg. replace)


In Symbols Frameworks, each of above mentioned animation behaviours correspond to protocols
- DiscreteSymbolEffect
- IndefiniteSymbolEffect
- TransitionSymbolEffect
- ContentTransitionSymbolEffect

Adding animations to SwiftUI
- New view modifier symbolEffect()

Adding animations to UIKit
- Call addSymbolEffect() on UIImageView

Discreet
One can use repeat with count to discreet animations if required to repeat animations n number of times.

Appear/Dissappear
One can have both behaviour where symbols only disappears or appears without any changes to surrounding view OR with
changes to surrounding views.