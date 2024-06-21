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
