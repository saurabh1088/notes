#  QnA


## 1. How would you design a complex UIView hierarchy to ensure optimal performance?
In order to design a complex UIVIew hierarchy ensuring optimal performance, one requires a blend of
- Thoughtful architecture
- Efficient use of UIKit features
- Performance profiling

Below are some detailed pointers helping achieve a complex UIView hierarchy

### 1.1 Minimize/Flatten the view hierarchy
- Use as few views as possible.
- Avoid deeply nested UIView hierarchies.
    - Pitfall here is that each level adds rendering overhead.
- Use CALayer if interactivity isn't required. CALayer is lighter and faster.

### 1.2 Lazy Loading of Views
- Create and add subviews only when they’re needed, like when they become visible.
- Deallocate or reuse views that move offscreen in scenarios like scroll views or paginated content.
- Conditionally initialize views so that only required views are initialized.

### 1.3 Optimize Auto Layout
- Avoid unnecessary constraints, too many constraints can lead to performance issues.
- Simplify layouts by leveraging intrinsic content sizes and alignment properties.

### 1.4 Reuse views
- Use reusable views, especially in UITableView or UICollectionView as data set could be huge.
- Use reuse identifiers wherever applicable to avoid unecessarily creatinf views.

### 1.5 Optimize Rendering
- If view doesn't needs transparency then keep it opaque.
    - This avoids unecessary calculations required for blending.
- Use backgroundColor and borderWidth instead of custom-drawn backgrounds and borders.
- Avoid overlapping transparent views, as they increase compositing costs.
- Rasterize static layers by using layer.shouldRasterize for views that don’t change often. 
    - NOTE: Be cautious this can increase memory usage.

### 1.6 Efficient Image Handling
- Make sure to use appropriate sized image.
    - This will prevent scaling cost at runtime.
    - If size required is small, using a bigger image incurs more memory cost.
- Images not changing frequently should be cached.
- * Enable UIImageView's contentMode for proper scaling rather than resizing manually.

### 1.7 Optimize Animations
- Limit simultaneous animations to what is visually necessary.
- Use UIView animations for simpler tasks and CoreAnimation (CABasicAnimation, CAKeyframeAnimation) for more complex
animations.
- Avoid creating animations in tight loops or repeatedly triggering them unnecessarily.
- Gracefully handle and close/stop animation once animating view is no longer visible.

### 1.8 Profile and Debug Performance
- Use instruments in Xcode to detect bottlenecks, following in instruments can be used
    - Time Profiler
    - Core Animation FPS
    - Allocations
- Use Xcode’s Debug View Hierarchy to visualize and analyze the hierarchy for inefficiencies.
- Use `Debug > Color Blended Layers` to identify areas with high compositing costs.

### 1.9 Leverage Pre-rendering
- Pre-render static content into a single image (UIImage) and display it in an UIImageView to reduce the number of views
being rendered.
    - This is useful for complex static UI elements like charts or decorative designs.

### 1.10 Manage View Updates
- Perform batch updates
    - For frequent updates, group them together using methods like setNeedsLayout or layoutIfNeeded judiciously to avoid
    redundant recalculations.
- Avoid forced layouts
    - Refrain from calling layoutSubviews or draw(_:) directly. Use system-provided mechanisms to update views.

    