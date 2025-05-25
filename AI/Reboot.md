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


## Retrieval Augmented Generation (RAG)