# Computer Vision


## 1. What is Computer Vision?
- Computer Vision (CV) is a field of Artificial Intelligence (AI) that enables computers to understand and interpret visual
data from the world such as
    - images,
    - videos, or
    - live camera feeds.
- Just like humans use eyes and the brain to see and understand the world,
    - computer vision allows machines to “see” and “understand” images using algorithms and models.
- Computer vision is accomplished by using large numbers of images to train a model.
- One can say that at its core, Computer Vision is a field of Artificial Intelligence that enables computers to "see" and "understand" digital images and videos in the same way humans do.
- It's about teaching machines to interpret and make sense of the visual world.


## 2. Tensors & Computer Vision

### 2.1 What is a Tensor?
- Tensors are simply mathematical objects that can be used to describe physical properties, just like scalars and vectors.
- In fact tensors are merely a generalisation of scalars and vectors, 
    - a scalar is a zero rank tensor,
    - and a vector is a first rank tensor.
- A tensor is a multi-dimensional array that generalizes scalars, vectors, and matrices to higher dimensions.
- It’s the fundamental building block for representing numerical data (e.g., pixel values) that neural networks operate on.

### 2.2 Tensors in Computer Vision
- In computer vision, a tensor is the core data structure used to represent
    - images,
    - videos, and
    - features
    within machine learning models—especially
        - deep learning frameworks like TensorFlow, PyTorch, or Core ML.

| **Tensor Rank (Order)** | **Example**                            | **Computer Vision Use Case**         |
|-------------------------|----------------------------------------|--------------------------------------|
| **0D Tensor (Scalar)**  | `5`                                    | Single pixel intensity or parameter  |
| **1D Tensor (Vector)**  | `[255, 128, 64]`                       | Pixel values of one color channel    |
| **2D Tensor (Matrix)**  | `[[255, 128], [64, 0]]`                | Grayscale image (Height x Width)     |
| **3D Tensor**           | `[[[R,G,B], [R,G,B]], [[R,G,B], ...]]` | RGB image (Height x Width x Channels)|
| **4D Tensor**           | `Batch of images N x H x W x C`        | Used in CNNs for batch training      |
| **5D Tensor**           | `Video N x T x H x W x C`              | Time series of image frames          |


## 3. Fundamental Computer Vision Techniques (The "How" of Seeing)
- All CV tasks start with understanding how images are represented and processed.

### Image Representation & Preprocessing
