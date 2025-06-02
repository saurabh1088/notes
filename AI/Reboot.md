# AI/ML/GenAI - Reboot


## Computer Vision
Computer Vision (CV) is a field of Artificial Intelligence (AI) that enables computers to understand and interpret visual
data from the world — such as images, videos, or live camera feeds.
Just like humans use eyes and the brain to see and understand the world, computer vision allows machines to “see” and
“understand” images using algorithms and models.


## Neural Networks
A neural network is a core concept in machine learning (ML) and deep learning (DL), modeled loosely on the way the human
brain processes information.

One can think of a neural network as a function approximator built using layers of mathematical operations, where each
layer transforms the data to learn patterns and relationships.

Neural networks are computational models composed of layers of interconnected processing units called “neurons”, which are
designed to learn patterns from data. Each neuron performs a simple computation, and together they form a layered structure
capable of approximating complex functions. These models are trained by adjusting internal weights based on how well the
network performs on a given task, using backpropagation and optimization algorithms like gradient descent.

### Activation functions
- Activation function
    - Activation functions introduce non-linearity into the network, allowing it to learn complex patterns.
        - Sigmoid
            - Maps input values to a range between 0 and 1.
            - Useful for binary classification, but can suffer from vanishing gradients.
        - Tanh (Hyperbolic Tangent)
            - Outputs values between -1 and 1.
            - Similar to sigmoid but centered at zero, which can help optimization.
        - ReLU (Rectified Linear Unit)
            - Outputs zero for negative inputs and raw input for positive values.
            - Most commonly used due to its simplicity and efficiency in deep networks.
        - Binary Step function
            - Outputs either 0 or 1 based on a threshold.
            - Not used in practice for training neural networks due to its non-differentiable nature.

### Hidden layers
- Hidden layers take weighted inputs
    - Hidden layers are intermediate layers between the input and output.
    - Each neuron in a hidden layer receives a weighted sum of inputs from the previous layer and applies an activation function.
    - These layers are responsible for feature extraction and transformation in the learning process.

### Vectors and Matrices
- Vectors and Matrices in Neural Networks 
    - Fundamental operating units of neural networks is vector
    - What are vectors?
        - A vector is an ordered set of numbers.
        - For example columns in a spreadsheets are vectors
        - Columns and columns of vectors in arrays form matrices
        - When vectors are stacked together, they form matrices, which allow parallel processing of multiple inputs.
        - Matrix multiplication is used to compute outputs at each layer efficiently.


### Loss functions
- Loss functions
    - Loss functions measure the difference between predicted output and actual target values, guiding the learning process
    through backpropagation.
    - The goal of training is to minimize the loss function.
    - Different tasks require different loss functions.
    - For example a trading system loss function should consider loss when one looses money not when one gains, it should
    penalize losses (financial loss) more heavily than gains.


## Keras
- Keras is a high-level neural networks API written in Python.
- It runs on top of TensorFlow (and previously supported Theano and CNTK).
- Keras provides a simplified interface for building, training, and evaluating deep learning models.
- It is known for being:
    - User-friendly
    - Modular (you can easily plug in different components)
    - Extensible (easy to create custom layers, losses, etc.)

```
Example
from keras.models import Sequential
from keras.layers import Dense

model = Sequential([
    Dense(64, activation='relu', input_shape=(10,)),
    Dense(1, activation='sigmoid')
])
```

## TensorFlow
- TensorFlow is an open-source machine learning framework developed by Google.
- It supports a wide range of ML tasks, especially deep learning.
- TensorFlow provides both:
    - Low-level APIs (for flexibility and customization)
    - High-level APIs (like tf.keras for ease of use)
- Uses computational graphs to represent operations, making it efficient for GPU/TPU execution.
- Scalable across CPUs, GPUs, and TPUs
- Production-ready with deployment tools (TensorFlow Serving, Lite, JS)
- Rich ecosystem (e.g., TensorBoard for visualization)

```
import tensorflow as tf

x = tf.constant([[1.0, 2.0]])
w = tf.constant([[3.0], [4.0]])
y = tf.matmul(x, w)
print(y)  # Output: [[11.]]
```

## PIL - Python Imaging Library
- PIL was the original Python Imaging Library for opening, manipulating, and saving image files.
- The original PIL is no longer maintained.
- Its fork, Pillow, is the actively maintained version and is used in its place.
- It was used to
    - Open and save images in many formats (JPEG, PNG, GIF, etc.)
    - Resize, crop, rotate, and filter images
    - Draw text, shapes, and lines
    - Convert between color modes (e.g., RGB, grayscale)

## Image Convolution

### What is image convolution?
- Image convolution is a mathematical operation used in image processing and computer vision to extract features such as
    - edges, 
    - textures, 
    - or patterns. 
- It involves applying a small matrix, called a filter or kernel, across an image to produce a feature map (also called 
an activation map).

### Filter (Kernel)
- Also referred to as Kernel
- It is used to process an input image and transform that image to something that might be useful to downstream for processing.
- Filter is a small matrix (usually 3x3, 5x5, or 7x7) containing weights.
- This filter slides over the input image, and at each location, performs an element-wise multiplication followed by a sum (called a dot product).
- The result is a single number, which is placed in the output feature map.
- This operation helps highlight specific features like edges, corners, or textures.
- Examples
    - A Sobel filter detects edges.
    - A Gaussian filter blurs an image to reduce noise.

### Padding
- When applying a filter near the edges of an image, one might run out of pixels.
- Padding adds extra pixels (usually zeros) around the border of the image.
- Padding helps preserve spatial dimensions and avoid losing important edge information.
- Types of padding:
    - Valid padding
        - No padding, the output is smaller than the input.
    - Same padding
        - Pads the image so that the output size remains the same as the input.

### Stride
- Stride defines how many pixels the filter moves at each step.
    - A stride of 1 means the filter moves one pixel at a time (high overlap).
    - A stride of 2 means the filter skips every other pixel (reduces spatial size).
- Larger strides lead to smaller output feature maps and faster computation but may miss fine details.

### Pooling
- Pooling is a downsampling operation used to reduce the dimensions of feature maps while retaining important information.
- Types of pooling
    - Max Pooling
        - Takes the maximum value in each region.
    - Average Pooling
        - Takes the average value in each region.
- Pooling makes the representation more compact and reduces overfitting by introducing spatial invariance.


### Convonutional Neural Network (CNN)
- A Convolutional Neural Network is a class of deep learning models particularly effective for image processing tasks 
like classification, detection, and segmentation.
- Help to extract features from images leading to better learning for image classification.



## Transfer Learning

## ImageNet
- ILSVRC


## Natural Language Processing

While working with text data in natural language processing, there comes various challenges like syntactic errors, spelling
mistakes, incorrect words etc. This demands that input body of text to NLP should be processed. For this purpose there
are certain libraries, some of which are

#### Natural Language Toolkit NLTK
#### spaCy
#### Gensim
#### TextBlob

### NLP Conceptual Terminologies

#### Documents
- A text body is referred to as document.

#### Corpus
- Corpus is a large set of text data that all NLP tasks depend upon.
- Corpus can be a single document or a bunch of documents.
- Can be multiple languages.

#### Vocabulary
- Set of distinct words used in the corpus.

#### Out-of-vocabulary
- Any word in a document which is not found in the relevant corpus vocabulary is considered out-of-vocabulary.

#### Word sense disambiguation
- The ability to computationally identify the meaning of words in context.

#### Tokenization
- Tokenization is a step in NLP process which breaks longer strings of text into smaller pieces or tokens.
- Tokens can be sentences, words or individual characters.

#### Word embeddings

#### N-grams

#### POS Tagging

#### NER

#### Stop words

### Vectorization
- Vector is a data structure similar to an array
- Process of converting text data into vector format is referred to as Vectorization
- Machines can't understand text as input.
- So to perform machine learning on text one need to convert text into a numerical format.
- This converted numerical format then machines can understand to find patterns and make prediction on it.

#### Why can't one-hot encoding be used for vectorization?
- Consumes lot of memory
- Computationally very expensive

#### Vectorization techniques

##### Bag of words
- Similar to one-hot encoding
- Instead of registering presence and absence, it registers count/frequency of each words

##### Term Frequency - Inverse Document Frequency (TF-IDF)


word2vec
- Converts words to vectors
- It is a two layer neural network-based method for efficiently creating word embeddings
- Takes a text corpus as input and returns a set of vectors known as feature vectors
- Has two models
    - Continuous bag of words
    - Skip gram model

GloVe - Global Vectors
- GloVe attempts to generate word vectors by using the global co-occurence relationship.


### Recurrent Neural Networks (RNNs)

### LSTMs - Long Short-Term Memory
- A type of Recurrent Neural Network, widely used for sequential data prediction.

### Applications of NLP

- Sentiment analysis
- Machine translation
- Speech recognition
- Document summarization
- Chatbots
- Text classification (e.g., spam detection)
- Named entity recognition (NER)
- Part-of-speech tagging
- Question answering systems
- Text-to-speech synthesis
- Language modeling and text generation
- Information retrieval (e.g., search engines)
- Automatic keyword extraction
- Optical Character Recognition (OCR) with NLP post-processing
- Voice assistants (e.g., Siri, Alexa)
- Grammar and spell checking
- Plagiarism detection
- Topic modeling (e.g., LDA)
- Semantic search
- Emotion detection
- Legal and medical document analysis
- Fake news and misinformation detection
- Social media monitoring and analysis
- Customer feedback and review analysis
- Dialogue systems for virtual assistants or support


## Retrieval Augmented Generation (RAG)


