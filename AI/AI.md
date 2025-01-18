# AI/ML/Generative AI


- Transformers for Large Language Models (LLMs)
- Intro to Neural Networks
    - Basics of how neural networks work.
- Intro to Transformers
    - Architecture designed to handle sequential data more efficiently than traditional networks.
- Intro to Large Language Models
    - Models like BERT, GPT, which use transformers to process and generate text.


## Artificial Intelligence (AI)

### Definition:

    AI stands for Artificial Intelligence, which refers to the simulation of human intelligence in machines that are programmed to think, learn, and behave like humans. This includes:
        Problem Solving: Making decisions and solving puzzles or games, like chess or Go.
        Understanding Human Speech: Interpreting and responding to spoken language.
        Visual Perception: Recognizing objects, faces, or scenes from images or videos.
        Learning from Experience: Improving performance over time based on data or feedback.


### Examples:

    Algorithms for Solving Games: AI can master complex games by exploring possible moves, learning from outcomes, and optimizing strategies. Examples include AlphaGo by DeepMind which beat world champions in Go.
    Self-Driving Cars: These use AI to navigate, make decisions based on traffic conditions, recognize road signs, and avoid obstacles. They combine multiple AI techniques like computer vision, natural language processing (for understanding road signs), and decision-making algorithms.
    Predicting Credit Card Defaults: AI analyzes patterns in historical data like credit history, spending habits, and payment regularity to predict the likelihood of a customer defaulting on their credit card payments.
    Diagnosing Cancer Risks: AI models can analyze medical images like X-rays or MRIs to identify patterns associated with cancer, sometimes spotting anomalies that might be missed by human eyes.


    Machine Learning (ML): 
        Learning from historical data to predict outcomes on unseen data. 
        Essentially, recognizing patterns in data.


## Deep Learning

### Overview:

    Deep Learning is a specialized subset of machine learning that uses neural networks with multiple layers (hence "deep"). These layers can learn and make intelligent decisions on their own by processing data in a way that mimics the human brain.


### Key Concepts:

    Neural Networks:
        Structure: Composed of layers of interconnected nodes or "neurons." 
            Input Layer: Takes in data.
            Hidden Layers: Process the data through various transformations. Deep learning uses many of these layers.
            Output Layer: Provides the final result or prediction.
        Neurons: Each neuron receives input from other neurons, processes it (often through a weighted sum followed by an activation function), and passes on the result to neurons in the next layer.
    Complex Algorithms:
        Learning: Deep learning algorithms learn from vast amounts of data by adjusting the weights of connections between neurons. This process, known as backpropagation, involves:
            Forward Pass: Data goes through the network to produce an output.
            Backward Pass: Errors are calculated and used to adjust weights to minimize the error over time.


#### Applications:

    Image Recognition: Deep learning models, especially Convolutional Neural Networks (CNNs), excel at recognizing patterns in images, like identifying objects, faces, or even diseases in medical images.
    Natural Language Processing (NLP): 
        Text Understanding: Models like Recurrent Neural Networks (RNNs) and more recently, Transformers, can understand and generate human language. 
        Language Translation: Systems can translate languages with high accuracy by learning patterns from large bilingual datasets.
    Generative Models: 
        GPTs: Generative Pre-trained Transformers use deep learning to generate text that mimics human writing by predicting subsequent words based on context, trained on extensive text corpora.
        Creative Outputs: From writing stories or poetry to composing music or creating art.


### Why Deep Learning is Complex:

    Data Hunger: Requires large datasets to learn effectively because of the model's complexity.
    Computational Power: Needs significant computing resources, often using GPUs for faster processing.
    Architecture Decisions: Choosing the right network design (number of layers, types of neurons, etc.) is crucial for performance and can be complex.


### Getting Started with Deep Learning:

    Frameworks: Popular libraries like TensorFlow, PyTorch, or Keras offer tools to build and train deep learning models. They abstract much of the complexity but allow for customization.
    Basic Steps:
        Data Preparation: Collecting, cleaning, and formatting data.
        Model Architecture: Designing or selecting a neural network structure.
        Training: Using data to adjust the model's weights, often with techniques like gradient descent.
        Evaluation: Testing the model on unseen data to assess performance.
        Deployment: Using the trained model in real-world scenarios.


