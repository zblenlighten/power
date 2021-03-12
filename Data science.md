# Knowledge Memo

[Kaggle blog](https://medium.com/kaggle-blog)  
[state-of-the-art model](https://paperswithcode.com/sota)  
[state-of-the-art 模型](http://www.jiqizhixin.com/sota)  
[格物钛 open dataset](https://www.graviti.cn/open-datasets)  

## Contents

- [Project Preparation](#project-preparation)
- [Deep Learning](#deep-learning)
- [Machine Learning](#machine-learning)
- [ML Applications](#ml-applications)
- [Data Analysis](#data-analysis)
- [Statistics](#statistics)
- [Deployment](#deployment)

## Data science

### Project Preparation

- Data
  - Univariate data
    - Categorical data
      - Nominal (conveys identity)
      - Ordinal (conveys rank)
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
  - Natural Language
    - Tokenization: word segmentation, convert characters to lowercase
    - Remove useless characters, remove stop/rare words
    - Stemming & Lemmatization: extract roots, spell correction, stem extraction, punctuation encoding, pos tagging
    - Named-entity recognition: entity insertion and extraction
  - Image
    - [Image augmentation](http://imgaug.readthedocs.io): Crop, Symmetry, Rotation, Scale, Noise, Hue, Obstruction, Blur
    - OpenCV: resize (INTER_CUBIC, INTER_LINEAR, INTER_AREA)
  - Data quality
    - Completeness: whole picture
    - Accuracy
    - Age: how often is data updated
    - Consistency: rules and naming convention
    - Usage

- Data processing
  - Data collection
    - API / ETL
      - Data aggregating (e.g. Funnel.io)
    - Web beacon
      - Invisible tracking script (e.g. Google Analytics)
      - Javascript code snippet ([comparison](https://data36.com/build-data-tools-google-analytics-vs-sql/))
    - Web crawler
      - Selenium
  - Dimensionality reduction
    - Principal Component Analysis (PCA)
    - Linear Discriminant Analysis (LDA)
    - Singular Value Decomposition (SVD)
    - Locality Sensitive Hashing
      - Fuzzy Search
  - Feature learning
  - Data masking

- Project Checklist: Obtain → Scrub → Explore → Model → Interpret
  - Frame the problem and look at the big picture
  - Get the data (automate)
  - Explore the data to gain insights (field expert)
  - Prepare the data to better expose the underlying data patterns
    1. data clean/data analysis
    2. **feature engineering**
        - variable characteristics
        - missing data imputation
        - categorical encoding
        - variable transformation
        - discretization
        - ourliers
        - dates
        - feature scaling
    3. feature selection
  - Explore many different models and short-list the promising ones
  - Fine-tune
  - Present your solution
  - Launch, monitor and maintain your system

- Applications
  - Similarity measure ([scipy distance](https://docs.scipy.org/doc/scipy/reference/spatial.distance.html))
    - Euclidean distance
    - Jaccard index
    - Cosine similarity
    - Hamming distance
    - Pearson correlation coefficient
    - Information entropy
  - Ranking (MLR: machine learned ranking)
    - Information retrieval
      - Page Rank (Markov Model)
    - Case: [Hacker News ranking](http://www.ruanyifeng.com/blog/2012/02/ranking_algorithm_hacker_news.html), [Reddit](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_reddit.html), [Stack Overflow](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_stack_overflow.html), [Newton's Law of Cooling](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_newton_s_law_of_cooling.html), [Wilson score interval](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_wilson_score_interval.html), [Bayesian average](http://www.ruanyifeng.com/blog/2012/03/ranking_algorithm_bayesian_average.html)
    - [Metrics](http://queirozf.com/entries/evaluation-metrics-for-ranking-problems-introduction-and-examples)
    - Approaches
      - Pointwise
      - Pairwise
  - Natural Language Processing
    - Tasks
      - Text classification
      - Semantic similarity
      - Sentiment analysis
    - Models
      - Bag of Words & N-gram: term frequency — inverse document frequency (tf–idf)
        - Article vector (each dimension is the tf–idf of the word) → Cosine distance
      - Topic model
        - Probabilistic Latent Semantic Analysis (pLSA)
        - Latent Dirichlet Allocation (LDA)
      - Embedding
        - Word2Vec (Continues bag of words: CBOW vs Skip-gram)
          - Word vector → article vector (对词向量方差归一化：因为一些常出现的词反而特征更不明显，需要突显较少出现词的向量特征) → Word Mover's distance (WMD) / Cosine distance / Euclidean distance
          - Out-of-vocabulary (OOV)
          - Negative sampling
        - Item2vec
        - Graph Embedding
      - Transformer (Attention)
        - BERT ([Simple Transformers](https://towardsdatascience.com/simple-transformers-introducing-the-easiest-bert-roberta-xlnet-and-xlm-library-58bf8c59b2a3))
  - Computer Vision
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

- Neural Network
  - Convolutional Neural Network (CNN)
    - Pooling: max pooling & average pooling
  - Recurrent Neural Network (RNN)
    - Long short-term memory (LSTM)
      - Cell state: forget gate → input gate → output gate
  - Training
    - Feed forward
    - Gradient descent (vs: gradient ascent)
    - Global minimum
    - Back propagation (reverse topological order)

- Fine-tune
  - Random initialization
  - Optimization
    - Non-iterative vs iterative: Least squares (OLS) vs Gradient descent
    - Loss function: the measures on a single training example
    - Cost function: a sum of the loss function applied to each of the training examples
    - Objective function: general term for any optimize function during training
      - Maximum likelihood estimation (MLE)
        - Expectation maximization (EM)
  - [Activation function](https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6)
    - Softmax: multiclass
    - Sigmoid: binary
    - Linear: regression
    - ReLU: hidden layer
    - Tanh: RNN
  - Learning rate
  - Prevent over-fitting
    - L2 & L1 Regularization
    - Dropout
    - Data augmentation
    - Early stopping
  - Gradient descent optimization
    - Adam: Momentum + RMSprop / AdaGrad
  - Residual block & [Batch normalization](https://towardsdatascience.com/batch-normalization-theory-and-how-to-use-it-with-tensorflow-1892ca0173ad)
    - Normalization vs Standardization
  - Hyperparameter optimization

- Models
  - Image classification
    - [Keras Models](https://keras.io/applications/)
  - Object detection
    - Backbone + detection head
    - YOLO
      - Intersection over Union: IoU
      - Anchor Boxes
  - Text recognition  
    - CRNN ([ctc](https://github.com/tensorflow/tensorflow/blob/679f95e9d8d538c3c02c0da45606bab22a71420e/tensorflow/python/kernel_tests/ctc_loss_op_test.py))

- Further topic
  - Generative Adversarial Network (GAN)
  - [Feature engineer](https://www.quora.com/Does-deep-learning-reduce-the-importance-of-feature-engineering): Deep Feature Synthesis
  - Complexity: Roofline model ([VGG16和MobileNet实例分析](https://zhuanlan.zhihu.com/p/34204282))

- Applications
  - Alpha Go
    - Monte Carlo Tree Search
  - Self-driving car (AV: Autonomous Vehicle): SAE's automation level
    - Lane departure warning system

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

- Bagging
  - Random forest

- Boosting
  - Adaboost

- Basic topics
  - Overfitting vs Underfitting
    - Overfitting: too small training data ratio to overall data, too complex model, uneven sampling, no regularization, no outlier handling
    - Underfitting: too large training data ratio to overall data, too simple model, too concentrated data 
  - Lazy learning vs Eager learning
    - Lazy: k Nearest Neighbor
    - Eager: Decision tree, Naive Bayes, Neural Network

- Further topics
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

#### Unsupervised learning

- kMeans
- Affinity propagation
- FP-growth, Apriori

#### Few-shot learning

#### Reinforcement learning

- Multi-armed bandit

#### Evaluation

- Metrics ([sklearn metrics and scoring](https://scikit-learn.org/stable/modules/model_evaluation.html))

- Cross Validation

- Confusion Matrix
- F1 Score
  - Precision = TP / (TP + FP)
  - Recall = TP / (TP + FN)
- Receiver Operating Characteristic (AUC: Area Under the ROC Curve)
  - [ROC](http://mlwiki.org/index.php/ROC_Analysis)
  - True Positive Rate = TP / (TP + FN)
  - False Positive Rate = FP / (FP + TN)
- Precision-Recall (PR) curve
- Loss function
  - RMSE: Root Mean Squared Error (MSE: Mean squared error)
  - MAPE: Mean Absolute Percent Error (MAE: Mean absolute error)
- Others
  - Log Loss
  - Gain and Lift Charts
  - Kolmogorov Smirnov Chart
  - Concordant – Discordant Ratio

- Multi-classification: F1 score, Average Accuracy, Log-loss

### ML Applications

#### Recommender System

- Framework
  - Online serving
  - Distributed computing
  - Stream computing
  - Data highway

- Match / Retrieval
  - Content-based
  - CF: Collaborative filtering (NCF: Neural Collaborative Filtering)
    - Item based
    - User based
      - Demographic characteristic
      - User behavior / User profile
      - Personalized topic model
    - Problems: Lack of diversity, Cold start (new community, new item, new user)
    - SVD (Matrix Factorization)

- Ranking ([CTR](https://zhuanlan.zhihu.com/p/61154299): Click Through Rate): depends on business needs and development stage
  - XGBoost (GBM、GBRT、GBDT)
  - Factorization Machine (FM), FFM, DeepFM ([说明](https://blog.csdn.net/john_xyz/article/details/78933253))
  - [DNN](https://zhuanlan.zhihu.com/p/35484389): FNN, PNN, AFM, ect

- Evaluation
  - Spot check
  - Ground truth
  - Metrics
    - CTR
  - Offline vs Online
    - A/B test

- Case
  - YouTube
    - Candidate Generation
    - Ranking ([Youtube 排序系统](https://zhuanlan.zhihu.com/p/82584437))

#### Computational Advertising

- Programmatic Advertising
  - Real time bidding (**RTB**)
  - Private marketplace (PMP)
  - Preferred deals
  - Programmatic guaranteed

- Online Advertising Platforms
  - Supply side platform (**SSP**): publisher, ad network
  - Audience
  - Demand side platform (**DSP**): advertiser → target audience
  - Ad exchange platform (ADX): publisher / ad network - advertiser
    - RTB: second-price auction
    - DSP buys ad space as cheaply as possible from publisher, SSP sells ad space for the highest possible price
  - Data management platform (DMP): DSP
  - Types of programmatic media buying: Open auction/RTB, Private auction, Preferred deal, Programmatic guaranteed, Direct deal

- Google's display advertising stack
  - Google Ads: advertisers (a type of DSP only limited to Google’s inventory)
    - [Campaign](https://support.google.com/google-ads/answer/7450050)
    - Quality score: expected clickthrough rate (CTRs), ad relevance, landing page experience
    - Automation in media
      - Creative assets
      - Inventory (product feeds)
      - Bidding
      - Targeting
      - Placements
      - Measurement and attribution (automated bidding requires automated measurement)
      - Reporting (dashboards, intelligent reports in Analytics)
    - Measurement
      - Clearly define your measurement owner.
      - Keep business impact in mind.
      - Be relentlessly curious and passionate about the customer journey.
      - Focus on objective-driven KPIs.
      - Master multiple tools.
      - Develop strong data interpretation skills.
      - Make measurement lead to action.
      - Have a learning mindset.
      - Make measurement a habit.
  - Google Marketing Platform (GMP)
    - Google Analytics
    - Data Studio
    - Campaign Manager
    - Search Ads (search management platform)
    - Display & Video (DSP)
    - Google Tag Manager
    - Optimize

### Data analysis

- Business analytics
  - Big Data Maturity Model
  - Solution deployment: technical implementation, data collection, data transformation (ETL)
  - Business as usual: data presentation, tactical reporting
  - Analytics consulting: driving vision and strategy, change management
  - Tools: Tableau, Power BI, QlikView, KNIME ([cheat sheet](https://www.knime.com/cheat-sheets))
  - Models
    - Customer Experience (CX)
    - Customer Lifetime Value: [lifetimes](https://lifetimes.readthedocs.io/en/latest/index.html)
    - Marketing mix modeling (MMM)
    - Survival regression (survival analysis): duration in Churn analysis
    - Revenue Management and Pricing (RMP)
    - RFM: Recency, Frequency, Monetary & RFV: Recency, Frequency, Volume
  - References
    - [Digital Marketing by Kaushik](https://www.kaushik.net/avinash/sitemap/)

- Data visualization
  - Tools
    - [D3.js](https://observablehq.com/@d3/gallery)
    - [Tableau Public](https://public.tableau.com/en-us/gallery)
    - [R Shiny](https://shiny.rstudio.com/gallery)
    - [Story Telling with Data](http://www.storytellingwithdata.com/blog)
    - [Seeing Theory](https://seeing-theory.brown.edu/)
    - [Travel Visa Inequalities](https://projects.christianlaesser.com/travel-visa-inequality/)
  - Design
    - [Misleading graph](https://en.wikipedia.org/wiki/Misleading_graph)
    - [Color](http://www.ruanyifeng.com/blog/2019/03/coloring-scheme.html)

- Pirate Funnel

| Element  | Function  | Relevant metrics  |
|---|---|---|
| Acquisition  | Generate attention through a variety of means, both organic and inorganic  | Traffic, mentions, cost per click, search results, cost of acquisition, open rate  |
| Activation  | Turn the resulting drive-by visitors into users who are somehow enrolled  | Enrollments, signups, completed onboarding process, used the service at least once, subscriptions  |
| Retention  | Convince users to come back repeatedly, exhibiting sticky behavior  | Engagement, time since last visit, daily and monthly active use, churns  |
| Revenue  | Business outcomes (which vary by your business model: purchases, ad clicks, content creation, subscriptions, etc.)  | Customer lifetime value, conversion rate, shopping cart size, click-through revenue  |
| Referral  | Viral and word-of-mouth invitations to other potential users  | Invites sent, viral coefficient, viral cycle time  |

- Acquisition mediums: Organic, Cost Per Click / Cost Per Mille (CPC / CPM), Referreal, Email, None

### Statistics

[Tutorial](https://stattrek.com/tutorials/ap-statistics-tutorial.aspx)

- Statistical significance
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
  - [Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors#Examples)
    - Type I error: occurs when you reject a **null hypothesis** that is actually true（False Positive → FP / (FP + TN), 拒真错误, 错杀好人）
    - Type II error: non-rejection of a false **null hypothesis**（False Negative → FN / (FN + TP), 取伪错误, 放走坏人）
  - Examples
    - Student's t-test
    - Chi-squared test
    - F-test (Analysis of variance: ANOVA)

- Case
  - [Lady tasting tea](https://en.wikipedia.org/wiki/Lady_tasting_tea)
  - Simpson's paradox
  - St. Petersburg paradox
  - Monty Hall problem

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

- Incremental learning

- Online learning

- ML Design Patterns

- Potential ML system architecture approaches

|   | REST API  | Shared DB  | Streaming  | Mobile App  |
|---|---|---|---|---|
| Training  | Batch  | Batch  | Streaming  | Streaming  |
| Prediction  |   | Batch  | Streaming  |   |
| Prediction result delivery  | Via REST API  | Though the shared DB  | Streaming via message queue  | Via in-process API on mobile  |
| Latency for prediction  | So so  | High  | Very low  | Low  |
| System management difficulty  | So so  | Easy  | Very hard  | So so  |

- References
  - [Best practices for performance and cost optimization for machine learning](https://cloud.google.com/solutions/machine-learning/best-practices-for-ml-performance-cost)
