# Memo

## Contents

- [Data processing](#data-processing)
- [Machine learning](#machine-learning)
- [Deep learning](#deep-learning)
- [Statistics](#statistics)
- [Data visualization](#data-visualization)

## Data science

### Data processing

- Structured data
  - Foundation
    - Nominal
    - Ordinal
    - Interval
    - Ratio
  - Dimensionality reduction
    - Principal Component Analysis
- Geodata
- Natural Language
  - Bag of Words (Term Frequency — Inverse Document Frequency)
    - Tokenization: word segmentation, convert characters to lowercase
    - Remove useless characters, remove stop/rare words
    - Stemming & Lemmatization: extract roots, spell correction, stem extraction, punctuation encoding
    - Named-entity recognition: entity insertion and extraction
    - ...
- Image
  - Image augmentation
    - Crop
    - Symmetry
    - Rotation
    - Scale
    - Noise
    - Hue
    - Obstruction
    - Blur
  - Label
- Correlation
  - Distances
  - Ranking
  - Similar picture search
    - Perceptual hashing: pHash, SIFT
    - [Color histogram](https://en.wikipedia.org/wiki/Color_histogram)
    - [Otsu's method](https://en.wikipedia.org/wiki/Otsu%27s_method)
  - NPL
    - TF-IDF

### Machine learning

#### Classification

- kNN
- Decision tree
- Naive bayesian
- Logistic regression
- Support Vector Machine

#### Cluster

- kMeans

#### Feature Engineer

[Some text](https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114#83e6)

#### Evaluation

//TODO

### Deep learning

- Neural network
  - Feed forward
  - Gradient descent
  - Global minimum
  - Back propagation
- Models
  - Computer vision
    - VGG16
    - CRNN
    - YOLO
- Fine-tune
  - Random initialization
  - Activation function
    - Softmax: multiclass
    - Sigmoid: binary
    - Linear: regression
    - Relu: hidden layer
    - Tanh: RNN
  - Learning rate
  - Prevent overfitting
    - L2 & L1 Regularization
    - Dropout
    - Data augmentation
    - Early stopping
  - Gradient descent optimization
    - Adam
  - Residual block & Batch normalization
  - [Hyperparameter optimization](https://en.wikipedia.org/wiki/Hyperparameter_optimization)
- [Feature engineer](https://www.ibm.com/developerworks/community/blogs/jfp/entry/Feature_Engineering_For_Deep_Learning?lang=en)
- Generative adversarial network
- Application
  - Alpha Go
    - Monte Carlo Tree Search

### Statistics

- Case
  - [Lady tasting tea](https://en.wikipedia.org/wiki/Lady_tasting_tea)
  - [Simpson's paradox](https://en.wikipedia.org/wiki/Simpson%27s_paradox)
  - [St. Petersburg paradox](https://en.wikipedia.org/wiki/St._Petersburg_paradox)

### Data visualization

<!-- TODO -->