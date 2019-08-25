# Knowledge Memo

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
  - Bag of Words
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
    - Term Frequency — Inverse Document Frequency

### Machine learning

#### Classification

| Name  | Advantage  | Disadvantage  | Application  | Remarks  |
|---|---|---|---|---|
| kNN  | 精度高，对异常值不敏感，无数据输入假定  | 计算复杂度高，空间复杂度高  | 改进配对效果，识别手写数字  |   |
| Decision tree  | 计算复杂度不高，输出结果易于理解，对中间值的缺失不敏感，可以处理不相关特征数据  | 可能过拟合  | 预测隐形眼镜类型  |   |
| Naive bayesian  | 在数据较少的情况下仍然有效，可以处理多类别问题  | 对于输入数据的准备方式较为敏感  | 过滤垃圾邮件/恶意留言，从个人广告用词中获取区域倾向  |   |
| Logistic regression  | 计算代价不高，易于理解和实现  | 容易欠拟合，分类精度可能不高  | 从疝气病症预测病马的死亡率  |   |
| Support Vector Machine  | 泛化错误率低，计算开销不大，结果易解释  | 对参数调节和核函数的选择敏感，原始分类器仅适用于二分类问题  | 识别手写数字（更少的内存）  |   |

- Bagging
  - Random forest
- Boosting
  - Adaboost

#### Regression

// TODO

#### Unsupervised learning

- kMeans
- FP-growth

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
  - Prevent over-fitting
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

- Knowledge
  - [Type I and type II errors](https://en.wikipedia.org/wiki/Type_I_and_type_II_errors#Examples)
    - Type I error: null hypothesis是正确的，却拒绝了null hypothesis（拒真错误，错杀好人, false positive）
    - Type II error: null hypothesis是错误的，却没有拒绝null hypothesis（放走坏人, false negative）
  - 假设检验的步骤
    1. 提出null hypothesis和alternative hypothesis
    2. 指定检验中的level of significance（一般取0.05和0.01）
        - Level of significance: 当作为一个等式的null hypothesis为真时，犯Type I error的概率
    3. 收集样本数据并计算检验统计量的值
        - one-tail test
        - two-tail test
    4. 利用检验统计量的值计算p-value
        - p-value: 一个度量样本所提供的证据对null hypothesis的支持程度的概率值，越小越说明不能得出null hypothesis为真的结论
    5. 如果 p-value <= level of significance，则拒绝null hypothesis
    6. 在应用中解读统计结论
    7. 临界值方法

- Case
  - [Lady tasting tea](https://en.wikipedia.org/wiki/Lady_tasting_tea)
  - [Simpson's paradox](https://en.wikipedia.org/wiki/Simpson%27s_paradox)
  - [St. Petersburg paradox](https://en.wikipedia.org/wiki/St._Petersburg_paradox)

### Data visualization

// TODO