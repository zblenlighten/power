# Knowledge Memo

## Blogs

- [Deepmind](https://deepmind.com/blog)
- [Kaggle](https://medium.com/kaggle-blog)
- [state-of-the-art model](https://paperswithcode.com/sota)
- [state-of-the-art 模型](https://sota.jiqizhixin.com/)
- [格物钛公开数据集](https://gas.graviti.cn/open-datasets)

## Contents

- [Project Preparation](#project-preparation)
- [Deep Learning](#deep-learning)
- [Machine Learning](#machine-learning)
- [Statistics](#statistics)
- [ML Applications](#ml-applications)
- [Data Analysis](#data-analysis)
- [Deployment](#deployment)

## Data science

### Project Preparation

- Project Checklist
  - Clarifying requirements
    - Business objective
    - Feature the system needs to support
    - Data
    - Constraints
    - Scale of the system
    - Performance
  - Framing the problem
    - ML objective
    - Specify the system's input and output
    - Choosing the ML category
  - Data preparation
    - Data engineering (automation)
    - [**Feature engineering**](https://trainindata.medium.com/feature-engineering-for-machine-learning-a-comprehensive-overview-a7ad04c896f8) ([feature engine](https://feature-engine.readthedocs.io/en/latest/index.html))
    - [Feature selection](https://trainindata.medium.com/feature-selection-for-machine-learning-a-comprehensive-overview-bd571db5dd2d)
  - Data exploration (field expert)
  - Model development
  - Evaluation
  - Development and serving
    - Project structure: [Cookiecutter Data Science](http://drivendata.github.io/cookiecutter-data-science/)
  - Monitoring and infrastructure

- Data
  - Univariate data
    - Categorical data
      - Nominal (identity)
      - Ordinal (rank)
    - Numerical data
      - Discrete (counted)
      - Continuous (measured)
        - Interval (no true zero)
        - Ratio (there is a true zero and ratios make sense)
  - Multivariate data
    - Scaler
    - Vector
    - Matrix (image)
    - Tensor
  - Spatiotemporal data
    - Time series data
    - Geographic data
  - Data provenance
    - Structured data vs Unstructured data
    - Raw data vs Processed data
    - Primary data vs [Inherited data](https://towardsdatascience.com/how-to-work-with-someone-elses-data-f33485d79ed4)
  - Data type in computer science
    - String
    - Character
    - Integer
    - Float
    - Boolean

- Data Management Body of Knowledge (DMBOK)
  - Data Architecture & Data Development
    - Data collection
      - ETL / API
        - KNIME ([cheat sheet](https://www.knime.com/cheat-sheets)), Funnel.io (data aggregating)
      - Click stream / Web analytical data (Web beacon / JavaScript Tag)
        - Invisible tracking script ([list of analytics tools](https://github.com/0xnr/awesome-analytics))
        - Javascript code snippet ([comparison](https://data36.com/build-data-tools-google-analytics-vs-sql/))
      - Data scraping / crawling
        - Selenium
      - Devices: Laser radar, 3D human pose machine
    - Data cleaning: OpenRefine
    - Data labeling / Data generating
      - Tools: LabelImg, LabelMe
      - Image augmentation
      - [Active learning](https://en.wikipedia.org/wiki/Active_learning_(machine_learning))
      - GAN (Generative Adversarial Network)
      - Data security, privacy, and compliance requirements
    - Data transformation
      - Categorical variable encoding ([Category Encoders](https://contrib.scikit-learn.org/category_encoders/))
      - Variable transformation
        - Power transform
          - Box–Cox transformation
          - Yeo–Johnson transformation
    - Dimensionality reduction
      - Principal Component Analysis (PCA)
      - Linear Discriminant Analysis (LDA)
      - Singular Value Decomposition (SVD)
      - Locality Sensitive Hashing
        - Fuzzy Search
    - Data modeling
  - Data Operations ([DataOps](https://towardsdatascience.com/the-rise-of-dataops-2788958034ee))
  - Data Governance: Governance, Risk, Security, and Compliance
  - Data Security
    - Access control (RBAC, PBAC, centralized vs decentralized)
      - Identity and Access Management (IAM)
      - Privileged Access Management (PAM)
    - Encryption (data at rest & data in transit), Data masking, Data erasure
    - Data loss prevention (DLP)
    - Data integrity monitoring
      - File integrity monitoring
    - Regulatory and Compliance
      - General Data Protection Regulation (GDPR), Anti-Money Laundering (AML)
      - [What is the difference between personally identifiable information (PII) and personal data?](https://techgdpr.com/blog/difference-between-pii-and-personal-data/)
    - FTC fair information practice principles: Notice, Choice, Access, Security and Enforcement
    - Payment Card Industry Data Security Standard (PCI DSS)
    - Data Privacy and Data Protection
      - Anonymization vs Pseudonymization
  - Data Warehouse
  - Business Intelligence
    - [Tableau Public](https://public.tableau.com/en-us/gallery)
    - [Power BI Community](https://community.powerbi.com/t5/Data-Stories-Gallery/bd-p/DataStoriesGallery)
  - Reference and Master Data
  - Document and Content
  - Metadata
  - Data Quality
    - Completeness: whole picture
    - Accuracy
    - Age: how often is data updated
    - Consistency: rules and naming convention
    - Usage
    - Big Data Maturity Model

- Applications
  - Data visualization
    - Examples
      - [D3.js](https://observablehq.com/@d3/gallery)
      - [R Shiny](https://shiny.rstudio.com/gallery)
      - [Story Telling with Data](http://www.storytellingwithdata.com/blog)
      - [Seeing Theory](https://seeing-theory.brown.edu/)
      - [Travel Visa Inequalities](https://projects.christianlaesser.com/travel-visa-inequality/)
      - [Tupper's self-referential formula](https://en.wikipedia.org/wiki/Tupper%27s_self-referential_formula)
    - Design
      - [Misleading graph](https://en.wikipedia.org/wiki/Misleading_graph)
      - [Color](http://www.ruanyifeng.com/blog/2019/03/coloring-scheme.html)
  - Similarity measure ([scipy distance](https://docs.scipy.org/doc/scipy/reference/spatial.distance.html))
    - Euclidean distance
    - Jaccard index
    - Cosine similarity
    - Hamming distance
    - Pearson correlation coefficient
    - Information entropy
  - Ranking (LTR: learning to rank)
    - Approaches
      - Pointwise
      - Pairwise
      - Listwise
    - [Hacker News ranking](http://www.ruanyifeng.com/blog/2012/02/ranking_algorithm_hacker_news.html), [Reddit](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_reddit.html), [Stack Overflow](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_stack_overflow.html), [Newton's Law of Cooling](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_newton_s_law_of_cooling.html), [Wilson score interval](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_wilson_score_interval.html), [Bayesian average](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_bayesian_average.html)
  - Natural Language Processing
    - Data processing
      - Tokenization: word segmentation, lowercasing
      - Remove useless characters, remove stop/rare words
      - Stemming & Lemmatization: extract roots, spell correction, stem extraction, punctuation encoding, pos tagging
      - Named-entity recognition: entity insertion and extraction
    - Tasks
      - Text classification
      - Semantic similarity
      - Sentiment analysis
    - Models
      - Statistical text encoder
        - Bag of Words(BoW) & N-gram: term frequency — inverse document frequency (TF-IDF)
          - Article vector (each dimension is the TF-IDF of the word) -> Cosine distance
      - ML based text encoder
        - Embedding
          - Word2Vec (Continues bag of words: CBOW vs Skip-gram)
            - Word Mover's distance (WMD) / Cosine distance / Euclidean distance
            - Out-of-vocabulary (OOV)
            - Negative sampling
            - Visualization: t-SNE
          - Item2vec
          - Graph Embedding
            - DeepWalk
            - Node2vec
        - Transformer (Attention)
          - BERT ([Simple Transformers](https://towardsdatascience.com/simple-transformers-introducing-the-easiest-bert-roberta-xlnet-and-xlm-library-58bf8c59b2a3))
      - Topic models
        - pLSA (Probabilistic Latent Semantic Analysis)
        - LDA (Latent Dirichlet Allocation)
  - Computer Vision
    - Data processing (OpenCV)
      - Crop, Resize, Padding, Normalize, Equalization, Balance
      - Visual descriptor
        - HOG (Histogram of oriented gradients)
        - LBP (Local binary patterns)
        - Haar-like features
      - Filters & Convolutions
        - [Kernel](https://en.wikipedia.org/wiki/Kernel_(image_processing))
        - Blind watermark (frequency domain)
    - Tasks
      - Classification
      - Detection
      - Segmentation: Sematic / Instance / Panoptic
      - Tracking (Video)
    - Similar picture search
      - Perceptual hashing: pHash, SIFT
      - [Color histogram](https://en.wikipedia.org/wiki/Color_histogram)
      - [Otsu's method](https://en.wikipedia.org/wiki/Otsu%27s_method)
  - Speech Recognition
    - Kaldi

### Deep learning

- Neural Network
  - CNN (Convolutional Neural Network)
    - Shape of the convolution kernel = in_channels (3) * kernel_size (h * w) * out_channels (+ padding & stride)
    - Convolutional layer
    - Pooling layer
      - Pooling: max pooling & average pooling
    - Fully connected layer
    - Upsampling: uppooling, interpolation, transposed convolution
  - RNN (Recurrent Neural Network)
    - LSTM (Long short-term memory)
      - Cell state: forget gate -> input gate -> output gate
  - Training (one epoch = batch size * iteration)
    - Feed forward
    - Gradient descent (vs: gradient ascent)
    - Global minimum
    - Back propagation (reverse topological order)
  - Transfer learning
    - Add new layers
    - Fine-tune

- Fine-tune
  - Random initialization
  - Optimization
    - Non-iterative vs iterative: Least squares (OLS) vs Gradient descent
    - Loss function: the measures on a single training example
      - Cross entropy, MSE, MAE, Huber loss
    - Cost function: a sum of the loss function applied to each of the training examples
    - Objective function: general term for any optimize function during training
      - Maximum likelihood estimation (MLE)
        - Expectation maximization (EM)
  - Activation functions
    - ReLU, LeakyRelu, ELU: hidden layer
    - Sigmoid: binary
    - Softmax, Softmin: multiclass
    - Tanh: RNN
  - Learning rate ([how to adjust learning rate](https://pytorch.org/docs/stable/optim.html#how-to-adjust-learning-rate))
  - Prevent over-fitting
    - L1 & L2 Regularization (Lasso regression & Ridge regression -> Linear regression)
      - Regularization significantly reduces variance without substantial increase in bias
    - Dropout
    - Data augmentation
    - Early stopping
  - Gradient descent optimization
    - Adam: Momentum + RMSprop / AdaGrad
  - Residual block & Batch normalization (Normalization vs Standardization)
  - Hyperparameter optimization

- Models
  - Image classification
    - LeNet-5
    - AlexNet
    - VGG
    - Inception / GoogleNet
    - ResNet
    - MobileNet
  - Object detection
    - Backbone (feature extractor): Inception, ResNet, MobileNet
    - Detection head (output layer): Groundtruth
    - Two stage: R-CNN
      - RoI pooling
      - RPN (Region Proposal Network)
    - One stage: YOLO
      - Anchor boxes (a set of predefined bounding boxes) + Loss
      - IoU (Intersection over Union) = area of overlap / area of union
      - **NMS** (Non-Maximal Suppression): select the most appropriate bounding boxes
      - FPN (Feature Pyramid Networks)
    - Anchor free
    - CRNN + ctc (text recognition)
  - Semantic segmentation / Lane detection
    - Backbone (feature extractor): ResNet
    - U-Net
    - DeepLab (vs: FCN)
      - Encoder (Backbone + ASPP: atrous spatial pyramid pooling) - Decoder
  - Object Tracking
  - [Keras Models](https://keras.io/applications/)

### Machine learning

#### Supervised learning

| Name  | Advantage  | Disadvantage  | Application  |
|---|---|---|---|
| k Nearest Neighbor  | High accuracy, insensitive to outliers, no assumptions about data  | Computationally expensive, requires a lot of memory  | Improving matches from a dating site，handwriting recognition  |
| Linear regression  | Easy to interpret results, computationally inexpensive  | Poorly models nonlinear data  | Predicting the age of an abalone, forecasting the price of LEGO sets  |
| Logistic regression  | Computationally inexpensive, easy to implement, knowledge representation easy to interpret  | Prone to underfitting, may have low accuracy  | Estimating horse fatalities from colic  |
| Decision tree  | Computationally cheap to use, easy for humans to understand learned results, missing values OK, can deal with irrelevant features  | Prone to overfitting  | Predicting contact lens type  |
| Support Vector Machine  | Low generalization error, computationally inexpensive, easy to interpret results  | Sensitive to tuning parameters and kernel choice, natively only handles binary classification  | Handwriting classification (keep the same performance with less memory used)  |
| Naive Bayes  | Works with a small amount of data, handles multiple classes  | Sensitive to how the input data is prepared  | Filtering spam email / malicious posts, revealing local attitudes from personal ads  |

- Bagging: Random forest

- Boosting: Adaboost, XGBoost, Gradient boost

- Basic topics
  - Overfitting vs Underfitting
    - Overfitting (high variance): too small training data ratio to overall data, too complex model, uneven sampling, no regularization, no outlier handling
    - Underfitting (high bias): too large training data ratio to overall data, too simple model, too concentrated data
  - Lazy learning vs Eager learning
    - Lazy: k Nearest Neighbor
    - Eager: Decision tree, Naive Bayes, Neural Network

- Further topics
  - [Computational Complexity of Machine Learning Algorithms](https://medium.com/mlearning-ai/computational-complexity-of-machine-learning-algorithms-254c275de84)
  - Multiple regression
  - Bayesian decision theory
  - Probabilistic graphical model
    - Bayesian Network (directed graph)
      - Hidden Markov Model (HMM): transition matrix
    - Markov Network (undirected graph)
      - Markov random filed (MRF)
      - Conditional random field (CRF)
    - Sampling
      - Markov chain Monte Carlo (MCMC)
    - Stan
  - Latent variable vs Observable variable
    - Latent Variable Modeling
  - [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/index.html)

#### Unsupervised learning

- kMeans
- Affinity propagation
- Association rule learning: FP-growth, Apriori
- Information retrieval: PageRank (Markov Model)

#### Few-shot learning

#### Reinforcement learning

- [Gym](https://github.com/openai/gym)
- Q-learning / DQN
  - Input: system state
  - Output: Q(s, a) for all possible actions
- Multi-armed bandit
  - Explore-exploit tradeoff (Information Cocoon)
  - Epsilon-Greedy Algorithm
  - Upper confidence bound (UCB) -> Monte Carlo tree search (MCTS)

#### Evaluation

- Offline Metrics
  - Basic topics
    - Error = Bias + Variance
    - Metrics ([sklearn metrics and scoring](https://scikit-learn.org/stable/modules/model_evaluation.html))
    - Cross Validation
  - Classification
    - F1 Score
      - Precision = TP / (TP + FP)
      - Recall = TP / (TP + FN)
    - Receiver Operating Characteristic (AUC: Area Under the ROC Curve)
      - [ROC](http://mlwiki.org/index.php/ROC_Analysis)
      - True Positive Rate = TP / (TP + FN)
      - False Positive Rate = FP / (FP + TN)
    - Precision-Recall (PR) curve
    - Confusion Matrix
    - Multiclass: F1 Score, Average Accuracy, Log Loss
  - Regression
    - RMSE: Root Mean Squared Error (MSE: Mean squared error)
    - MAPE: Mean Absolute Percent Error (MAE: Mean absolute error)
  - [Ranking](http://queirozf.com/entries/evaluation-metrics-for-ranking-problems-introduction-and-examples)
  - Others
    - [Data Leakage in Machine Learning](https://machinelearningmastery.com/data-leakage-machine-learning/)
    - Gain and Lift Charts
    - Kolmogorov Smirnov Chart
    - Concordant – Discordant Ratio
  - NLP: BLEU, METEOR, ROUGE, CIDEr, SPICE
  - CV: FID, Inception Score
- Online Metrics
  - Ad click prediction: Click-through rate (CTR), revenue lift, etc.
  - Harmful content detection: Prevalence, valid appeals, etc.
  - Video recommendation: CTR, total watch time, number of completed videos, etc.
  - Friend recommendation: Number of requests sent per day, number, number pf requests accepted per day, etc.
- Fairness and Bias
- Operation related metrics
  - Resource usage: average serving times, throughput, number of prediction requests, memory / GPU / CPU utilization, etc.
  - Roofline model ([VGG16和MobileNet实例分析](https://zhuanlan.zhihu.com/p/34204282))

### Statistics

- Basic topics
  - [Normality test](https://en.wikipedia.org/wiki/Normality_test)
  - [Tutorial](https://stattrek.com/tutorials/ap-statistics-tutorial.aspx)

- Statistical significance
  - [Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors#Examples)
    - Type I error: occurs when you reject a **null hypothesis** that is actually true（False Positive = FP / (FP + TN), convict an innocent defendant)
    - Type II error: non-rejection of a false **null hypothesis**（False Negative = FN / (FN + TP), acquit a criminal)
  - Confidence levels & Confidence intervals
  - Statistical power
  - Steps in Hypothesis Testing
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

- A/B test (experimental test)
  - Confidence intervals
    - Problem: overlapping confidence intervals mean that the samples are likely to have the same population-level conversion rate
  - Chi-squared test
    - Telling if the two conditions are associated with conversions
  - Simulate sample size and plan timeline -> Time series analysis -> Chi-squared p-value
  - Conditional tests
  - Multi-Armed Bandit test

- Anomaly detection
  - Z-score
  - Local outlier factor (LOF)
  - Isolation forest
  - References
    - [Simple Anomaly Detection Using Plain SQL](https://hakibenita.com/sql-anomaly-detection)
    - Python: [package-outlier](https://pypi.org/project/package-outlier/), [pyod](https://pypi.org/project/pyod/)

- Cases
  - [Lady tasting tea](https://en.wikipedia.org/wiki/Lady_tasting_tea)
  - Simpson's paradox
  - St. Petersburg paradox
  - Monty Hall problem
  - [Spurious correlations](http://tylervigen.com/spurious-correlations)

- References
  - [Best Practices for ML Engineering](https://developers.google.com/machine-learning/guides/rules-of-ml)

### ML Applications

#### Recommender System

- Models
  - Content-based Filtering
    - Pros: ability to recommend new items, ability to capture the unique interests of each user
    - Cons: difficult to discover a user's new interests, requires domain knowledge
  - Collaborative Filtering
    - ItemCF
      - CF doesn't rely on item features but only upon users' historical interactions
    - UserCF
      - Demographic characteristic
      - User behavior / User profile
      - Personalized topic model
    - Pros: no domain knowledge needed, easy to discover users' new areas of interest, efficient
    - Cons: Exploration-exploitation (lack of diversity, can't handle niche interests), Cold start (new community, new item, new user)
  - Hybrid filtering
  - Matrix Factorization
    - Optimization
      - Stochastic Gradient Descent (SGD)
      - Weighted Alternating Least Squares (WALS)
    - Pros: training speed, serving speed
    - Cons: only relies on user-item interactions, handling new users is difficult
  - Two-tower neural network
    - Pros: utilizes user features, handles new users
    - Cons: slower serving, training is compute-intensive
  - References
    - [CTR预估模型的演化之路](https://zhuanlan.zhihu.com/p/61154299)
    - [深度学习在CTR预估中的应用](https://zhuanlan.zhihu.com/p/35484389)
    - [RecBole](https://recbole.io/)

- Evaluation
  - Spot check
  - Ground truth
  - Metrics
    - Precision@N, Recall@N, PR curve, ROC curve, mAP
    - CTR, CVR, GPM (GMV per mille: Gross merchandise volume / impression * 1000)
    - Top N Hit Rate
  - A/B test
    - [Innovating Faster on Personalization Algorithms at Netflix Using Interleaving](https://netflixtechblog.com/interleaving-in-online-experiments-at-netflix-a04ee392ec55)

#### Digital Advertising

- Programmatic Advertising
  - **RTB**: Real time bidding
  - PMP: Private marketplace
  - Preferred deals
  - Programmatic guaranteed

- Online Advertising Platforms
  - **SSP** (Supply side platform): publisher, ad network
  - Audience
  - **DSP** (Demand side platform): advertiser -> target audience
  - ADX (Ad exchange platform): publisher / ad network - advertiser
    - RTB: second-price auction
    - DSP buys ad space as cheaply as possible from publisher, SSP sells ad space for the highest possible price
  - DMP (Data management platform): DSP
  - Types of programmatic media buying: Open auction/RTB, Private auction, Preferred deal, Programmatic guaranteed, Direct deal

- Google's display advertising stack
  - Google Ads: advertisers (a type of DSP only limited to Google’s inventory)
    - [Campaign](https://support.google.com/google-ads/answer/7450050)
    - Quality score: expected CTR, ad relevance, landing page experience
    - Automation in media
      - Creative assets
      - Inventory (product feeds)
      - Bidding
      - Targeting
      - Placements
      - Measurement and attribution (automated bidding requires automated measurement)
      - Reporting (dashboards, intelligent reports in Analytics)
    - Measurement
      - Clearly define your measurement owner
      - Keep business impact in mind
      - Be relentlessly curious and passionate about the customer journey
      - Focus on objective-driven KPIs
      - Master multiple tools
      - Develop strong data interpretation skills
      - Make measurement lead to action
      - Have a learning mindset
      - Make measurement a habit

#### Harmful Content Detection

- Basic topics
  - Harmful content: violence, nudity, hate speech, misinformation, etc.
  - Categories
    - Harmful content (modality: text, image, video, audio, or any combination of these)
      - [How to build a message moderation system](https://hackernoon.com/message-moderation-system-ac9472962bf)
    - Bad actors

### Data analysis

- Business analytics
  - Solution deployment: technical implementation, data collection, data transformation (ETL)
  - Business as usual: data presentation, tactical reporting
  - Analytics consulting: driving vision and strategy, change management
  - Topics
    - Account based marketing (ABM)
    - Customer Lifetime Value: [lifetimes](https://lifetimes.readthedocs.io/en/latest/index.html)
    - Marketing mix modeling (MMM)
    - Survival regression (survival analysis): duration in Churn analysis
    - Revenue Management and Pricing (RMP)
    - RFM: Recency, Frequency, Monetary & RFV: Recency, Frequency, Volume
    - Price Elasticity of Demand
  - References
    - [Digital Marketing by Kaushik](https://www.kaushik.net/avinash/sitemap/)
    - [Design your data strategy in six steps](https://www.ibm.com/resources/the-data-differentiator/data-strategy)

- Pirate Funnel

| Element  | Function  | Relevant metrics  |
|---|---|---|
| Acquisition  | Generate attention through a variety of means, both organic and inorganic  | Traffic, mentions, cost per click, search results, cost of acquisition, open rate  |
| Activation  | Turn the resulting drive-by visitors into users who are somehow enrolled  | Enrollments, signups, completed onboarding process, used the service at least once, subscriptions  |
| Retention  | Convince users to come back repeatedly, exhibiting sticky behavior  | Engagement, time since last visit, daily and monthly active use, churns  |
| Revenue  | Business outcomes (which vary by your business model: purchases, ad clicks, content creation, subscriptions, etc.)  | Customer lifetime value, conversion rate, shopping cart size, click-through revenue  |
| Referral  | Viral and word-of-mouth invitations to other potential users  | Invites sent, viral coefficient, viral cycle time  |

- Acquisition mediums: Organic, CPC / CPM (Cost Per Click / Cost Per Mille), Referreal, Email, None

- References
  - [Good Data Analysis](https://developers.google.com/machine-learning/guides/good-data-analysis)

### Deployment

- Data Science Infrastructure
  - Model development
    - CUDA (Compute Unified Device Architecture) programming
      - Host / CPU (Kernel) -> Device / GPU (Grid - Block - Thread)
    - TensorFlow
      - Computational graph: static -> dynamical
      - More [data types](https://www.tensorflow.org/api_docs/python/tf/dtypes)
      - model.save vs model.save_weights
      - TensorBoard
    - PyTorch (a PyTorch Tensor is basically the same as a NumPy array)
      - Computational graph: dynamical
      - Less [data types](https://pytorch.org/docs/stable/tensors.html)
    - Horovod
    - JAX
    - Others
      - TensorFlow Serving
      - Parameter Server
        - [TensorFlow](https://www.tensorflow.org/tutorials/distribute/parameter_server_training)
        - [PyTorch](https://pytorch.org/tutorials/intermediate/rpc_param_server_tutorial.html)
      - TensorRT
      - TensorFlow.js
      - TensorFlow Lite
      - [ONNX](https://onnx.ai/)
      - [MLeap](https://combust.github.io/mleap-docs/)
      - [Oryx 2](http://oryx.io/)
  - Feature engineering
  - Model operations
    - Kubeflow
    - [Metaflow](https://outerbounds.com/)
    - MLflow
  - Architecture
  - Versioning
  - Job scheduler
  - Compute resources
  - Data warehouse

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

- Further topics
  - **Continual Learning**
  - Model compression
    - Knowledge distillation
    - Pruning
    - Quantization
  - Monitoring
    - Drifts: concept drift, data drift, upstream data changes
    - Model's inputs / outputs
    - Model accuracy
    - Model versions
    - Operation related metrics
  - Predictive Model Markup Language (PMML)

- References
  - [LF AI & Data Foundation Interactive Landscape](https://landscape.lfai.foundation/)
  - [Best practices for implementing machine learning on Google Cloud](https://cloud.google.com/architecture/ml-on-gcp-best-practices)
  - [Best practices for performance and cost optimization for machine learning](https://cloud.google.com/architecture/best-practices-for-ml-performance-cost)
