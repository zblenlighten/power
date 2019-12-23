# Knowledge Memo

[state-of-the-art model](https://paperswithcode.com/sota)  
[state-of-the-art 模型](http://www.jiqizhixin.com/sota)  

## Contents

- [Project Checklist](#project-checklist)
- [Data processing](#data-processing)
- [Deep learning](#deep-learning)
- [Machine learning](#machine-learning)
- [Statistics](#statistics)
- [Deployment](#deployment)
- [Data visualization](#data-visualization)

## Data science

### Project Checklist

- Frame the problem and look at the big picture
- Get the data (automate)
- Explore the data to gain insights (field expert)
- Prepare the data to better expose the underlying data patterns
  1. data clean
  2. feature selection
  3. [feature engineering](https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114#83e6)
  4. feature scaling
- Explore many different models and short-list the promising ones
- Fine-tune
- Present your solution
- Launch, monitor and maintain your system

### Data processing

- Structured data
  - Nominal, Ordinal, Interval, Ratio
  - Dimensionality reduction
    - Principal Component Analysis (PCA)
    - Linear Discriminant Analysis (LDA)
    - Singular Value Decomposition (SVD)

- Geodata

- Natural Language
  - Bag of Words & N-gram: Term Frequency — Inverse Document Frequency (tf–idf)
    - Tokenization: word segmentation, convert characters to lowercase
    - Remove useless characters, remove stop/rare words
    - Stemming & Lemmatization: extract roots, spell correction, stem extraction, punctuation encoding
    - Named-entity recognition: entity insertion and extraction
  - Topic model
    - Probabilistic Latent Semantic Analysis (pLSA)
    - Latent Dirichlet Allocation (LDA)
  - Word embedding
    - Word2Vec
      - Continues bag of words (CBOW)
      - Skip-gram
  - Transformer models
    - [Simple Transformers](https://towardsdatascience.com/simple-transformers-introducing-the-easiest-bert-roberta-xlnet-and-xlm-library-58bf8c59b2a3)

- Image
  - [Image augmentation](http://imgaug.readthedocs.io): Crop, Symmetry, Rotation, Scale, Noise, Hue, Obstruction, Blur
  - Label

- More knowledge
  - Similarity measure
    - Euclidean distance
    - Jaccard index
    - Cosine similarity
    - Hamming distance
    - Pearson correlation coefficient
    - Information entropy
  - Ranking
    - [Hacker News ranking](http://www.ruanyifeng.com/blog/2012/02/ranking_algorithm_hacker_news.html)
    - [Reddit](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_reddit.html)
    - [Stack Overflow](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_stack_overflow.html)
    - [Newton's Law of Cooling](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_newton_s_law_of_cooling.html)
    - [Wilson score interval](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_wilson_score_interval.html)
    - [Bayesian average](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_bayesian_average.html)
  - Natural Language Processing
    - Bag of Words & N-gram: article vector (each dimension is the tf–idf of the word) → Cosine distance
    - Word2Vec: word vector → article vector (对词向量方差归一化：因为一些常出现的词反而特征更不明显，需要突显较少出现词的向量特征) → Cosine distance / Euclidean distance (WMD: Word Mover's Distance)
    - ...
  - Computer vision
    - Tasks
      - Image classification
      - Object localization
      - Object detection
      - Object recognition
      - Instance segmentation
      - Video tracking
    - Similar picture search
      - Perceptual hashing: pHash, SIFT
      - [Color histogram](https://en.wikipedia.org/wiki/Color_histogram)
      - [Otsu's method](https://en.wikipedia.org/wiki/Otsu%27s_method)

### Deep learning

- Neural network
  - Feed forward
  - Gradient descent (vs: gradient ascent)
  - Global minimum
  - Back propagation

- Fine-tune
  - Random initialization
  - [Activation function](https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6)
    - Softmax: multiclass
    - Sigmoid: binary
    - Linear: regression
    - Relu: hidden layer
    - Tanh: RNN
  - Learning rate
  - Prevent over-fitting
    - L2 & L1 Regularization
    - Dropout
    - Data augmentation
    - Early stopping
  - Gradient descent optimization
    - Adam: Momentum + RMSprop
  - Residual block & [Batch normalization](https://towardsdatascience.com/batch-normalization-theory-and-how-to-use-it-with-tensorflow-1892ca0173ad)
  - Hyperparameter optimization

- Models
  - [Keras](https://keras.io/applications/) (VGG16)
  - [YOLO](https://medium.com/@jonathan_hui/real-time-object-detection-with-yolo-yolov2-28b1b93e2088) (IoU: Intersection over Union)
  - CRNN ([ctc](https://github.com/tensorflow/tensorflow/blob/679f95e9d8d538c3c02c0da45606bab22a71420e/tensorflow/python/kernel_tests/ctc_loss_op_test.py))
  - ...

- [Feature engineer](https://www.quora.com/Does-deep-learning-reduce-the-importance-of-feature-engineering): Deep Feature Synthesis

- Generative adversarial network (GAN)

- Application
  - Alpha Go
    - Monte Carlo Tree Search
  - Self-driving car (AV: Autonomous Vehicle): SAE's automation level
    - Lane departure warning system

### Machine learning

#### Classification

| Name  | Advantage  | Disadvantage  | Application  |
|---|---|---|---|
| kNN  | 精度高，对异常值不敏感，无数据输入假定  | 计算复杂度高，空间复杂度高  | 改进配对效果，识别手写数字  |
| Decision tree  | 计算复杂度不高，输出结果易于理解，对中间值的缺失不敏感，可以处理不相关特征数据  | 可能过拟合  | 预测隐形眼镜类型  |
| Naive bayesian  | 在数据较少的情况下仍然有效，可以处理多类别问题  | 对于输入数据的准备方式较为敏感  | 过滤垃圾邮件/恶意留言，从个人广告用词中获取区域倾向  |
| Logistic regression  | 计算代价不高，易于理解和实现  | 容易欠拟合，分类精度可能不高  | 从疝气病症预测病马的死亡率  |
| Support Vector Machine  | 泛化错误率低，计算开销不大，结果易解释  | 对参数调节和核函数的选择敏感，原始分类器仅适用于二分类问题  | 识别手写数字（更少的内存）  |

- Bagging
  - Random forest

- Boosting
  - Adaboost

#### Regression

// TODO

#### Few-shot learning

// TODO

#### Unsupervised learning

- kMeans
- FP-growth, Apriori

#### Recommender system

- Match
  - Content-based
  - CF: Collaborative filtering (NCF: Neural Collaborative Filtering)
    - Item based
    - User based
    - Cold start: new community, new item, new user)

- Ranking ([CTR](https://zhuanlan.zhihu.com/p/61154299)): depends on business needs and development stage
  - XGBoost
  - FM, FFM, DeepFM ([说明](https://blog.csdn.net/john_xyz/article/details/78933253))
  - [DNN](https://zhuanlan.zhihu.com/p/35484389): FNN, PNN, AFM, ect
  - Wide&Deep

- Evaluation
  - Offline
  - Online: A/B test

#### Evaluation

- Confusion Matrix
- F1 Score
  - Precision = TP / (TP + FP)
  - Recall = TP / (TP + FN)
- Area Under the Receiver Operating Characteristic Curve (ROC-AUC Score)
  - Sensitivity: True Positive Rate = TP / (TP + FN)
  - Specificity: False Positive Rate = FP / (FP + TN)

- Root Mean Squared Error (RMSE)
- Mean absolute error (MAE)

- Others
  - Log Loss
  - Gain and Lift Charts
  - Kolmogorov Smirnov Chart
  - Concordant – Discordant Ratio

- Multi-classification: F1 score, Average Accuracy, Log-loss

- Cross Validation

### Statistics

[Tutorial](https://stattrek.com/tutorials/ap-statistics-tutorial.aspx)

- Hypothesis Testing
  - [Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors#Examples)
    - Type I error: occurs when you reject a **null hypothesis** that is actually true（False Positive → FP / (FP + TN), 拒真错误, 错杀好人）
    - Type II error: non-rejection of a false **null hypothesis**（False Negative → FN / (FN + TP), 取伪错误, 放走坏人）
  - Steps
    1. Specify the **null hypothesis** and **alternative hypothesis**
    2. Set the Significance Level (common values are 0.05 and 0.01)
        - Significance Level: the probability of rejecting the **null hypothesis** when it is true (probability of making a Type I error)
    3. Compute from the observations the observed value of the test statistic
        - one-tail test
        - two-tail test
    4. Calculate the **[p-value](https://statisticsbyjim.com/glossary/p-value/)** based on the test statistic
    5. If **p-value** <= Significance Level, then **null hypothesis** is rejected
    6. Draw a conclusion
  - Examples
    - Student's t-test
    - Chi-squared test
    - F-test (Analysis of variance: ANOVA)

- Case
  - [Lady tasting tea](https://en.wikipedia.org/wiki/Lady_tasting_tea)
  - [Simpson's paradox](https://en.wikipedia.org/wiki/Simpson%27s_paradox)
  - [St. Petersburg paradox](https://en.wikipedia.org/wiki/St._Petersburg_paradox)
  - [三个反直觉的概率问题](https://www.itcodemonkey.com/article/15500.html)

### Deployment

- Questions of note
  - Do you need to be able to serve predictions in real time (and if so, do you mean like, within a dozen milliseconds or after a second or two), or will delivery of predictions 30 minutes or a day after the input data is received suffice?
  - How often do you expect to update your models?
  - What will the demand for predictions be (i.e. traffic)?
  - What size of data are you dealing with?
  - What sort(s) of algorithms do you expect to use (and do you really need them)
  - Are you in a regulated environment where the ability to audit your system is important?
  - Does your company have product-market fit? (i.e. do you need to prepare for the system’s original purpose to radically change)
  - Can this task be done without ML?
  - How large and experienced is your team - including data scientists, engineers and DevOps?

- Potential ML system architecture approaches

|   | REST API  | Shared DB  | Streaming  | Mobile App  |
|---|---|---|---|---|
| Training  | Batch  | Batch  | Streaming  | Streaming  |
| Prediction  |   | Batch  | Streaming  |   |
| Prediction result delivery  | Via REST API  | Though the shared DB  | Streaming via message queue  | Via in-process API on mobile  |
| Latency for prediction  | So so  | High  | Very low  | Low  |
| System management difficulty  | So so  | Easy  | Very hard  | So so  |

- References
  - [Architect a ML pipeline](https://towardsdatascience.com/architecting-a-machine-learning-pipeline-a847f094d1c7)
  - Google: [TFX](https://www.tensorflow.org/tfx)
  - Facebook: [FBLearner Flow](https://engineering.fb.com/core-data/introducing-fblearner-flow-facebook-s-ai-backbone/)

### Data visualization

- Design
  - [Color](http://www.ruanyifeng.com/blog/2019/03/coloring-scheme.html)

- Case
  - [Seeing Theory](https://seeing-theory.brown.edu/)
  - [Travel Visa Inequalities](https://projects.christianlaesser.com/travel-visa-inequality/)
