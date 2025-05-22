# AI/ML/GenAI - Reboot

## Computer Vision
- Convolution Layer
- Pulling

## Neural Networks
- Activation function
    - Sigmoid
    - Tanh
    - ReLU Restricted Linear Units
    - Binary Step function
- Hidden layers take weighted inputs
- Fundamental operating units of neural networks is vector
    - What are vectors?
        - For example columns in a spreadsheets are vectors
        - Columns and columns of vectors in arrays form matrices
- Loss functions
    - For example a trading system loss function should consider loss when one looses money not when one gains


## Keras
## TensorFlow
## PIL - Python Imaging Library

## Image Convolution

### What is image convolution?
- Image convolution is a mathematical operation used in image processing and computer vision to extract features such as
    - edges, 
    - textures, 
    - or patterns. 
- It involves applying a small matrix, called a filter or kernel, across an image to produce a feature map (also called 
an activation map).

### Filter (Kernel)
- Filter is a small matrix (usually 3x3, 5x5, or 7x7) containing weights.
- This filter slides over the input image, and at each location, performs an element-wise multiplication followed by a sum (called a dot product).
- The result is a single number, which is placed in the output feature map.
- This operation helps highlight specific features like edges, corners, or textures.
- Examples
    - A Sobel filter detects edges.
    - A Gaussian filter blurs an image to reduce noise.


- Convolution on Images - What is image convolution operation?
    - Filter - Also referred to as kernel, usually 3x3 or 5x5
        - It is used to process an input image and transform that image to something that might be useful to downstream
        for processing.
    - Padding
    - Stride
    - Pooling

- Convonutional Neural Network (CNN)
    - Help to extract features from images leading to better learning for image classification.