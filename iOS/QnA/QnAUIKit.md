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