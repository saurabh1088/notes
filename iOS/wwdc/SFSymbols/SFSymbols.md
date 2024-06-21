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