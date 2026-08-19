***机器学习**是一种人工智能技术，旨在通过数据训练模型，使计算机能够自动从数据中学习规律并进行预测或决策，而无需显式编程。机器学习的核心是利用算法从数据中提取特征并优化模型，以解决分类、回归、聚类等问题。*

Class：[Machine Learning by Andrew NG Standford](https://www.bilibili.com/video/BV1Bq421A74G/?spm_id_from=333.337.search-card.all.click)
Comment: This is a course for Knowledge rather than for Test. It has a nice slice design The teahcer illustrate with details and  mini-step explaination which make this knowledge easy to be taken away. Also, it it has a deep knowledge explianation, such as, 'why useing a vector can calculate faster than a loop?' 'How hardware can accelerate this process.' It explain the programming tool **Python** along side its course. And I like his gentle tone.
However, most of them are in theory instead of in practics.

# Intro
机器学习的主要类型有**监督学习**、**无监督学习**、**强化学习**和**半监督学习**
## 监督学习
**监督学习**是指根据现有数据的x跟y之间的关系来找到，x和y的一个映射规律。监督学习有明确的输入和输出标签。目的就是预测什么是**正确的**。
监督学习模型主要有 Regression Model(回归模型)和Classification Model(分类模型)。

**Regression Model** is used to predict number.

## 无监督学习
在无监督模型中，数据集没有明确的标签，算法自动根据输入的数据进行分组。常见的无监督学习有 *Clustering*（聚类）、*Anomaly Detection*(异常检测)和 *Dimensionality Reduction*(降维).

**Clustering** algorithm group the dataset  into different cluster according to the distance (without label).
  
**Anomaly Detection** helps find out some anomaly point.

**Dimensionality Reduction** helps to reduce the volume of data with lossing to much information.

## Terminology
- Training set:
	- Input variable: feature variable (特征值)
	- Output variable: target variable （目标值）
	- m: number of training examples
	- (x, y): single training example
	- $(x^{(i)} , y^{(i)})$: $i^{th}$ training example  
	- $x_j$ : $j^th$ feature
	- n: number of features
	- $\vec{x}^{(i)}$ : features of $i^{th}$ training example
	- $\vec{x}^{(i)}_j$ : value of feature $j$ in $i^{th}$ training example
# Data Preprocessing
## Data Mining
## Data Cleaning
## Data Transformation
### Normalization
### Standardization
## Data Reduction
### Feature Selection(特征选择)
### Feature Extraction(特征提取)
#### PCA(Principal Component Analysis, 主成分分析)
_**PCA** is a technique used to reduce the dimensionality of a dataset while preserving as much variance as possible. It does this by identifying the directions (principal components) in which the data varies the most and projecting the data onto these directions._

PCA works by computing the covariance matrix of the data, finding its eigenvalues(特征值) and eigenvectors(特征向量), and then selecting the top k eigenvectors (principal components) to form a new feature space.

### Discretization(离散化)

# Surpervised Learning
## Regression Model
### Linear Regression
#### Univariable Linear Regression(单因素变量回归 )
$$f_{w,b}(x) = wx+b$$
Simplfied:
$$f_{w}(x) = wx$$
*We can Standerize  a the dataset to make b = 0 ?*
##### Cost Funciton(成本函数)
 $J(w,b) = MSE/2$
Goal of linear regression : $\min\limits_{w,b} J(w,b)$
Simplified: $\min\limits_{w} J(w)$
##### Gradient Descent Algorithm
**Gradient Descent(梯度下降)** is a tool to find the minimal value of a funciton.

Implementing Gradient Descent: 
$$

w = w - \alpha \frac{\partial}{\partial w}J(w,b), \\
b = b - \alpha \frac{\partial}{\partial b}J(w,b),

$$

where $\alpha$ is the Learning rate(学习率).
> The gradient descent algorithm make sure the $(w , b)$ update toward the direction that decent fast

###### How to choose a learning rate ?
 If $\alpha$ is too small, gradient descent may be **slow**.
 If $\alpha$ is too large, gradient descent may: 
 - not reach the minimum,
 - fail to converge.
 
 >[!SUMMARY] 
 >Combine the linear regression model, the cost function and the gradient decent, the linear regression algorithm is obtian.
 
So machine learning means the math model and a stander to evaluate the model as well as the algorithm that can adjust the model to to its optimal parameter?  
#### Linear Regression with Multiple Variables(多因素变量回归)
$$
\begin{align}
f_{w,b}(x)&=w_1x_1 + w_2x_2 +...+w_{n-1}x_{n-1}+w_nx_n+b \\
\end{align}
$$
#### Vectorization(向量化)
With vector, the calculation can be parallel performed. 

Model:
$$
\begin{align}
f_{w,b}(x)&=w_1x_1 + w_2x_2 +...+w_{n-1}x_{n-1}+w_nx_n+b \\
&= \vec{w} \cdot \vec{x}+b
\end{align}
$$
Gradient decent:
$$
\begin{align}
w_j&= w_j - \alpha \frac{\partial}{\partial w_j}J(\vec{w},b), \\
b&= b - \alpha \frac{\partial}{\partial b}J(\vec{w},b),
\end{align}
$$
#### Normal Equation(正规方程)
**Normal equation** can solve for w, b without iterations.


#### Feature Scaling(特征缩放)
>因为不同参数$w_i$选择的是同一个学习率$\alpha$,所以在使用梯度下降来找到局部最小值时，不同的偏导数大小要相近，才能更快地收敛。因此$w_i$的值要尽量一相近，所以要将不同的特征进行放缩，使得他们的取值范围相近。

##### Mean normalization(均值归一化)
$$x_1 = \frac{x_1-\mu_1 }{{x_1}_{max}-{x_1}_{min}}$$
##### Z-score normalization(Z-score 归一化)
$$x_1 = \frac{x_1-\mu_1 }{\sigma_1}$$
归一化为标准正太分布

>[!Eaxample] Acceptable ranges:
>$-1 <= x_j <=1$
>$-3 <= x_j <=3$
>$-0.3 <= x_j <=0.3$

#### Checking Gradient Decent for Covergence
##### Learning curve
 Learning curve: the valus of cost function vs the iterations of gradient decent.
 ![[Pasted image 20250829072040.png|300]]
 - Cost function should decrease after every iteration.
##### Choose proper $\alpha$
*Note: With a small enough $\alpha$, $J(\vec{w},b)$ shoudle decrease on every iteration.*

Run the gradiwnt decent with a range of $\alpha$ and pick the biggest $\alpha$ that can asure the convergence of the $J(\vec{w},b)$.
### Feature Engineering(特征工程)
***Feature engineering** is to use intution to design new features, by transforming or combining original features. The goal is to make sure the algorithm work well.*

### Polynomial Regression(多项式回归)
Combine the Linear Regression with Multiple Variables with Feature Engineering.
## Classification Model 
### Logistic Regression(逻辑回归)
 
#### Sigmoid Function(Logistic Function)
$$
g(z) = \frac{1}{1+e^{-z}}, 0<g(z)<1 \tag{1}
$$
$$z = \vec{w}\cdot\vec{x}+b \tag{2}$$
![[Pasted image 20250830134038.png|400]]
fig.1the sigmoid fucntion

Combine the sigmoid function (1) and linear regression with multiple variable (2), the logistic regression can be obtian，
$$f_{\vec{w},b}(\vec{x}) = g(\vec{w}\cdot\vec{x}+b) = \frac{1}{1+e^{-(\vec{w}\cdot\vec{x}+b)}}\tag{3}$$
The output of the logistic function is the *probablity* that calss is 1.
#### Decision Boundary(决策边界)
When $z = \vec{w}\cdot\vec{x}+b > 0$ the output of the logistic regression is greater than 0.5, and the prediction is class 1.
So the decision bounary is, $z = \vec{w}\cdot\vec{x}+b = 0$

For example, when the linear regression for the data set below is $z = x_1 + x_2 - 3$，the decision boudary is $x_1 + x_2 - 3 = 0$.
![[Pasted image 20250830134556.png|300]]
Fig. 2 Example 1.

#### Cost Function for Logistic Regression(代价函数)
##### Loss Function

$$L\left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right), y^{(i)} \right) = 
\begin{cases}
-\log\left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right) \right) & \text{if } y^{(i)} = 1 \\
-\log\left( 1 - f_{\vec{w},b}\left( \vec{x}^{(i)} \right) \right) & \text{if } y^{(i)} = 0
\end{cases}$$
The difference between the prediction and the true value in a single dataset.
*Note: The difference between [Cost Function]([[Machine Learning#Cost Funciton 成本函数]])*

![[Pasted image 20250830143301.png|300]]
Fig. 3 Log fucntion.

Fig. 4 is the loss function when $y^{(i)} = 1$, we can learn  that the prediction close to 0 will be severly penalized. 
![[Pasted image 20250830143415.png|400]]
Fig. 4 Log function if $y^{(i))} = 1$. 


Fig. 5 is the loss function when $y^{(i)} = 0$, we can learn that the prediction close to 1 will be severly penalized. 
![[Pasted image 20250830143641.png|400]]
Fig. 5 Log function if $y^{(i))} = 0$.

##### Cost Funciton of Logistic Regression
$$J(\vec{w},b) = \frac{1}{m}\sum \limits_{i=1}^m L\left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right), y^{(i)} \right)$$
>训练的计算量与数据集的大小成线性关系，与特征值的数量也是呈线性关系。

##### Simplified Cost Funciton
$$\begin{aligned}
J(\vec{w}, b) &= \frac{1}{m} \sum_{i=1}^{m} \left[ L\left( f_{\vec{w}, b}\left( \vec{x}^{(i)} \right), y^{(i)} \right) \right] \\
&= -\frac{1}{m} \sum_{i=1}^{m} \left[ y^{(i)} \log\left( f_{\vec{w}, b}\left( \vec{x}^{(i)} \right) \right) + \left( 1 - y^{(i)} \right) \log\left( 1 - f_{\vec{w}, b}\left( \vec{x}^{(i)} \right) \right) \right]
\end{aligned}$$
#### Gradient Decent for Logistic Regression
Recall [[Machine Learning#Gradient Descent Algorithm]]
- Learning curve
- Vectorized
- Feature scaling
### Maximum Entropy Model(最大熵模型)
_**Maximum Entropy Model** is a generalization of Logistic Regression, which can be used in multiclass classification problems. It is based on the principle of maximizing the entropy of the predicted distribution, subject to the constraints imposed by the training data._

**The principle of maximum entropy**: when selecting a probability distribution to model a given set of data, one should choose the distribution that has the highest entropy among all distributions that satisfy the known constraints. This ensures that no additional assumptions or biases are introduced beyond what is supported by the data.

Why maximum entropy? Because it provides a principled way to incorporate prior knowledge into the model while still allowing for flexibility in the learned distribution. By maximizing entropy, the model is encouraged to explore a wider range of possible distributions, which can lead to better generalization on unseen data.
（熵越大，概率分布越均匀，这意味着模型不会对某些特征产生过度的偏好）


## Regularization to Reduce Overfiting(过拟合)
### Overfiting  
***Overfiting** is used to describe a model that can fit the training data very well and almost too well. The model lacks generality to new example .* (High Variance)

The reason of overfiting is because the model is trying very hard to fit all the data in the training set. 
>It's stricted by too many rules to be flexiable. And too many rules means too many features, some of which is made in the feature engineering.

#### Generalization(泛化)
 ***Generalization** is to make the model generalize well which can make good predictions even on brands new examples.*
#### Underfiting(欠拟合)
***Underfiting** means that the model does not fit the training set well*. (High bias)

One of the reason for underfit is that ther is not enough feature when training the model. 
>The model don't have enough information to understanding the target object well, which is the reason for bias.

![[Pasted image 20250830154916.png|500]]
Fig. 1 Eaxmple of unerfiting, just right fiting and overfiting(from left to right). 

### Addresing Overfiting
Method to address overfiting:
1. **Collect more training data.(Data mining)**
2. **Feature Selection**: wisely select features to include/exclude.
3. **Regulariaztion**: Adjust the weight of some feature to prevent some feature have overly large effect on the model.
#### Regularization(正则化)
**Regularization** is to penalize the model when a big parameter of features is chosen, so that the model will tends to select more small parameter $\vec{w},$ and result in a more smooth model.

Motivation: with a small value for the parameter, the model tends to be more simpler, which is simillar to reduce the number of features. This can reduce the overfiting.

>Even the model can  not fit all data as well as the global minimum, but it obtain more generalization. 

$$J(\vec{w},b) = \frac{1}{2m}\sum \limits_{i=1}^m \left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right)^2, y^{(i)} \right) + \frac{\lambda}{2m}\sum\limits_{j=1}^n w_j^2,$$
where the $\lambda (\lambda > 0)$ refer to regularization parameter, the second term is called regularisation term. ^r73dno

By adding the regularization term to the cost function, the goal of traning became finding the best trade-off between fiting the data well and generalization.

*Note: Regulaize the offset b always has trivial influence on the model.*

Influce of the $\lambda$ to the model:
- With a too small regularisation parameter, the fucntion of regularisation is trivial, and the model will overfiting as before.
- With a too large the algorithm will set all parameter $\vec{w}$ to a very small value, the model is overly simplified and tends to underfiting.

❓But why what is the different with delete the feature directly? (let the algorithm choose the weight of different feature instead of delete it by intuition)

#### Regularized Linear Regression
Recall
![[Machine Learning#^r73dno]]

Gradient decent algorithm for regularizaed linear regression:
$$
\begin{align}
w_j &= w_j - \alpha \frac{\partial}{\partial w}J(w,b) = w_j - \alpha \left[ \frac{1}{m}\sum \limits_{i=1}^m \left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right) - y^{(i)} \right)x^{(i)}_i + \frac{\lambda}{m}w_j\right]\\
b &= b - \alpha \frac{\partial}{\partial b}J(w,b) = b - \alpha \frac{1}{m}\sum \limits_{i=1}^m \left( f_{\vec{w},b}\left( \vec{x}^{(i)} \right) - y^{(i)} \right),
\end{align}
$$

> [!NOTE]
> $w_j - \alpha \frac{\lambda}{m}w_j = w_j(1-\alpha\frac{\lambda}{m})$
> 
> The effect of the regularization is to shrinking  the $w_j$ a little bit in every iteration of the gradient decent algorithm.

#### Regularized Logistic Regression
Updated Cost Function:
$$J(\vec{w}, b) = -\frac{1}{m} \sum_{i=1}^{m} \left[ y^{(i)} \log\left( f_{\vec{w}, b}\left( \vec{x}^{(i)} \right) \right) + \left( 1 - y^{(i)} \right) \log\left( 1 - f_{\vec{w}, b}\left( \vec{x}^{(i)} \right) \right) \right] + \frac{\lambda}{2m} \sum_{j=1}^{n} w_{j}^{2}$$

The Gradient descent is the same as that for Linear regression.

## Decision Tree(决策树)
**决策树**通过构建一个树状结构来模拟决策过程，每个节点代表一个特征（或属性），每个分支代表该特征的一个可能取值，叶节点代表最终的决策结果（类别标签）。决策树通过递归地选择最优特征进行划分，直到满足停止条件（如达到最大深度或叶节点纯度足够高）。
![[Pasted image 20250923155950.png|500]]

**Root node:** The top node of the tree, representing the entire dataset before any splits.
**Decision node**: A node that splits the data based on a feature, leading to further branches.
**Leaf node**: The final node of the tree, representing a specific class label or decision outcome.

#### Learning Process
-  Choose the feature that maximizes node purity (e.g., using information gain or Gini impurity) to split at each node.
- Decide when to stop splitting
	- When a node is 100% one class(0 Entropy)
	- When splitting a node will result in the tree exceeding a pre-defined maximum depth
    - When improvement in node purity (or information gain) is below a certain threshold
    -   When the number of samples in a node is below a certain threshold

##### Measure of Impurity
The Impurity can be masured by entropy:
![[信息论#^xox1l3]]

##### Information Gain
**Information Gain** measures the reduction in entropy after a dataset is split on a particular feature. It quantifies how much information is gained about the target variable by knowing the value of the feature.

$$
Information\ Gain(S,A) = H(P(S)) - \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(P(S_v))
$$
> Note: $H$ denotes the entropy of the probability distribution. $S$ is the original dataset, $A$ is the feature being considered for the split, $Values(A)$ are the possible values of feature $A$, $S_v$ is the subset of $S$ where feature $A$ has value $v$, and $|S|$ and $|S_v|$ are the sizes of these datasets.


#### Regression Tree(回归树)
_**Regression Tree** is a type of decision tree that is used for predicting continuous numerical values rather than categorical labels. It works by recursively partitioning the feature space into smaller regions based on the input features, and then fitting a simple model (usually a constant value) to each region._  

#### Tree Ensembles(树集成)
**Tree Ensembles** combine multiple decision trees to improve predictive performance and reduce overfitting. The final predictions are made by aggregating the predictions of individual trees. The two most common types of tree ensembles are **Random Forests** and **Gradient Boosting Machines (GBM)**.

#### Random Forest(随机森林)
**Random Forest** is an ensemble learning method that constructs multiple decision trees during training and outputs the mode of the classes (classification) or mean prediction (regression) of the individual trees. It introduces randomness in two main ways: by bootstrapping(自助采样) the training data (sampling with replacement) and by selecting a random subset of features for each split in the trees. This randomness helps to reduce overfitting and improve generalization.

#### XGBoost(Extreme Gradient Boosting)
_**XGBoost** is an optimized implementation of gradient boosting that is designed for speed and performance. It builds decision trees sequentially, where each new tree attempts to correct the errors made by the previous trees. XGBoost incorporates several advanced features, such as regularization to prevent overfitting, parallel processing for faster training, and handling of missing values. It is widely used in machine learning competitions and real-world applications due to its effectiveness and efficiency._
## Nerual Networks(Deep Learning)
### Intro 
**Application:**
- Speech Recognition 
- Image Recognition 
- Text (Natural Language Preocessing, NLP)
Advertising, Recommendation...

**Basic of Nerual Networks: Big Data**

**How Neural Network work?**
**The function of one neuron:** 
Take an input and generate an output (can be a logistic regression unit).

**A Simple Neural Network:**

![[Pasted image 20250901221344.png|400]]
- **Layer**: Nurons that take the same activations as input consist of a layer.
- **Activation(激活值)**: The output of the neuron, which is the combination of the input features, and which can stand for some higher level of 'feature'.
- **Input Layer(输入层)**：A vector consist of features.
- **Output Layer(输出层)**: the last layer.
- **Hidden Layer(隐藏层)**: the middle layer.
### Neural Network Layer
#### Terminology:
\[i\]: Denote the output of layer one.
The input layer is denoted as layer \[0\].
$\vec{w}^{[i]}_j,b^{[i]}_j$: Denote the $j^{th}$ parameter in the $i$ layer.
The number of layer does not include the input layer.

$g_{\vec{w},b}(\vec{x})$ (Sigmoid function in this case) in a neural network also called the **Activation Function(激活函数)**.

#### More Complex neural networks

 $g_{\vec{w},b}(\vec{x})$ (Sigmoid function in this case) in a neural network also called the **Activation Function(激活函数)**.

The activation of layers $l$, given the activation of layer $l-1$:
$$a_j^{[{l}]} = g(\vec{w}_j^{[l]}\cdot\vec{a}^{[l-1]}+b_j^{[l]})\tag{1}$$
### Inference
**Inference**(prediction,推理): Use a trained Nerual Network for prediction.

**Forward Propagation**: calculating the activation of neuron from the right to the left.
**Backward Propagation**: used for learning.

#### TensorFolw
**TensorFlow** is a frameworks for implementing deep learning algorithm  .

**Syntax**:
``` python
layer_1 = Dense(units = 3, activation = 'sigmoid')
s1 = layer_1(x) #the return value 's1' is a tensor
```
**Dense**: another name for layer, which is an object for layer in TensorFlow.
**Units**: The number of neuron in this layer.

##### Data in TensorFlow
**Data in numpy**:
```python
x1 = np.array([[200,17]]) # Create a 1x2 matrix
x2 = np.array([200,17]) # Create a 1D vector
```

**Data in TensorFlow:**
TensorFlow use matrix `np.array([[200,17]])` to represent data to accerlate computation. (Tensor, 张量)

#### Build a Neural Network in TensorFlow
**Sequential layers**:
```python
model = Sequential([layer_1,layer_2])
```

Compile the the sequensed layers into a model:
```python
model.compile(...)
```
**Train** this model:
```python
model.fit(x,y)
```

**Inference using the trained model**(推理):
``` python
model.predict(new)
```

#### Forward Propogation in Numpy
```python
def dense(a_in, W, b, g):
    units = W.shape[1]          # 获取权重矩阵W的列数（即本层神经元数量）
    a_out = np.zeros(units)     # 初始化输出数组
    for j in range(units):
        w = W[:, j]             # 提取第j个神经元的权重向量
        z = np.dot(w, a_in) + b[j]  # 计算加权和：z = w·a_in + b
        a_out[j] = g(z)         # 应用激活函数g，得到第j个神经元的输出
    return a_out
```

```python
def sequential(x):
    a1 = dense(x, W1, b1, g)   # 第一层全连接
    a2 = dense(a1, W2, b2, g)  # 第二层（输入为a1）
    a3 = dense(a2, W3, b3, g)  # 第三层（输入为a2）
    a4 = dense(a3, W4, b4, g)  # 第四层（输入为a3）
    f_x = a4                    # 最终输出
    return f_x
```

#### Vectorized implementation of NN
Matrix multiplication in Numpy:
```python
Z = np.matmul(AT,W) # AT @ W也是矩阵乘法
```
### Training
```python
import tensorflow as tf
from tensorfolw.keras import Sequential
from tensorflow.keras.layers import Dense

# ===============step 1. Create the model============
model = Sequential(
[Dense(units=25,activation ='sigmoid')
Dense(units=15,activation ='sigmoid')
Dense(units=1,activation ='sigmoid')]) 
# Sequence all the layers

# ================step 2. Loss and cost functions
from tensorflow.keras.losses import BinaryCrossentropy

model.compile(loss=BinaryCrossentropy())# Use a specific loss function BinaryCrossentropy, which commenly used in for classification model TensorFlow.
# MeanSquareError() can be used for regression model.

# Gradient descent
model.fit(X,Y,epochs = 100)# Fit the tranning data (Train the model). Epochs specify the number of steps in gradient descent.
```

**BinaryCrossentropy** is refer to the [[Machine Learning#Cost Funciton of Logistic Regression|cost function for Logistic Regression]]. Because 
this function is called corss-entropy loss function in Statistic.

Basic multiple layer nerual network also called a multiple layer perceptron(多层感知机).
### Activation Function
**Activation Function** take the $z = \vec{w}\cdot\vec{x}+b$, and output the activation $g(z)$.
 
If no activation function is used, the whole nerual network will be the same as a linear regression. Since *the linear fucntion of a linear fucntion is a linear function*.
#### Sigmoid Funciton
![[Machine Learning#Sigmoid Function(Logistic Function)]]
Sigmoid function is widely used in binary classification model, which can be used to some hidden feature with binary attributes.
#### ReLU
**ReLU** stand for Rectified Linear Unit.
$$g(z) = \max(0,z)$$
ReLU is suit for some feature that have different degree but from zero to inf. 
This is also the most common choice for **hidden layer**.
**Advantages:** 
- More efficient in calculation than sigmoid.
- Not as flat as sigmoid, which make the model learn more faster in gradient decent.
![[Pasted image 20250906001408.png|200]]
Fig 1. A flat gradient decent will slow down the gradient decent.
**Implementaiton:**
```python
Dense(units=25,activation='relu')
```
#### Leaky ReLU
$$
f(x) = x (if x > 0), f(x) = \alpha x (if x <=0 ,\alpha > 0)
$$
**Advantages：**
- 负半轴保持小梯度，环节ReLU死亡问题。
**Application:**
- 代替ReLU，常用于计算机视觉模型。

#### Parametric ReLU (PReLU)
**Advantages：** $\alpha$ 可学习，适应性更强。
#### Linear Activation Function
$$g(z) = z$$
Can be used for regression that can be negative or positive.
#### Tanh（双曲正切函数）
$$
g(z) = tanh(z)
$$
![[Pasted image 20250915054702.png|300]]
**Advantages:**
- Zero mean
- 有利于梯度传播
**Application：**
- RNN、LSTM等循环神经网络的隐藏层。
#### ELU (Exponential Linear Unit)
$$
g(z) = x (x>=0) ,g(z) = \alpha(e^x-1) (x<0)
$$
![[Pasted image 20250915060329.png|200]]
**Application:**
- 对稳定性要求高的深度网络
#### Swich
$$
g(z) = z\cdot sigmoid(z)
$$
![[Pasted image 20250915060702.png|400]]
**Propotities:**
- 平滑、非单调、优于ReLU.
### Multiclass Classification: Softmax Regression
**Multiclass classification**(多类别分类) problem is a classification problem that target $y$ can take on more than two possible values.
Remark: The difference between [[|multi-label classification.
#### Softmax
**Softmax** regression algorithm is a generation of logistic regression  which can work in multiclass classification context.
$$z_j = \vec{w}_j\cdot\vec{x}+b_j \quad j = 1,...,N $$
$$
a_j= \frac{e^{z_j}}{\sum\limits^N_{k=1}e^{z_k}} = P(y = j|\vec{x})$$
#### Cost Function
 $$Loss(a_1,\dots,a_N,y)= 
\begin{cases}
-\log\left( a_1 \right) & \text{if } y = 1 \\
-\log\left( a_2 \right) & \text{if } y = 2 \\
&\vdots \\
-\log\left( a_N \right) & \text{if } y = N \\
\end{cases}$$

#### Neural Network with Softmax Output
 Implementation Softmax in Tensorflow with more numerically accurate:
```python
# ============model===============
import tensorflow as tf
from tensorflow.keras import Sequential
form tendorflow.keras.layers import Dense
model = Sequential([
	Dense(units=25, activation='relu')
	Dense(units=15, activation='relu')
	Dense(units=10, activation='linear') # modified from activation='softmax'
]) 
# ==============loss=================
from tensorflow.keras.losses import SparaseCategoricalCrossentropy
model.compile(...,loss = SparaseCategoricalCrossentropy(from_logits=True))
# ==============fit==================
model.fit(X,Y,epochs=100)
# ==============predict==============
logits = model(X) # output z_1 to Z_10
f_x = tf.nn.softmax(logits)# Calculate the probabilty according to z_1 to z_10.
```   
#### Multiclass Classification vs Multi-Label Classification
**Multi-label Classificaition**(多标签分类) is the combination of binary classification, where the output layer have several sigmoid funtion as the activation functions, and there will be more than one true value. That means several label exist in the input sample.

![[Pasted image 20250912010240.png|500]]
### Practical Advice
#### AGI
- AI Catogary
	- ANI
	- AGI

### Adam Algorithm
**Adam**(**Ada**ptive **M**oment estimation) **Algorithm** is an algorithm that can adjust the learning rate $\alpha$ of the GD, so that it can reach the optimization point faster.
```python
# ============complie=============
model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate = 1e-3)) # learning_rate: the default global learning.
```
### Additional Layer Types
#### Convolutional Layer(卷积层)
Convolutional Layer is a type of layer that each neuron in the hidden layer only looks at part of the previous layer's input.
![[Pasted image 20250912012235.png|200]]
Benefit:
- Faster computation
- Need less training data and thus less prone to overfitting
#### Convolutional Neural Network
**Convolutional Neural Network** is a network that have several hidden convolutional layer.

### Evaluating a Model
#### Test set
Spliting the data set into traning set and test set
#### Linear Regression 
1. Compute the test error (squared error of test set) and the training error (squared error of training set) 
#### Logistic Regression
1. Computs the logistic loss of the training set and the test set.
2. Compute the fraction that the model has misclassified in the training set and data set. 
#### Model Selection
1. split the data set into three part: **training set,** **corss validation set**(validation set/ development set/ dev set, 交叉验证或验证集/开发集), and **test set**.   
2. Compute traning error, dev error and test error.
3. Evaluate the **parameter**  in the same model using training set, and evaluate **different model** using the test set and evaluate **the final best model** with optimal parameter using the validation set.
#### Bias and Variance
**High Bias**: The model do not even fit the traning set(too simple).
**High Varience**: The model fit the cross-validation set wrose than the trainig set (lack of generalization).

##### The Degree of Polynomial and Bias/Variance 
![[Pasted image 20250918223917.png|400]]
Fig. 1. The influence of the degree of polynomial on the bias and variance.
As the degree of polynomial increase, the $J_{train}(\vec{w},b)$ will decrease which means the Bias is decrease. 
>As the degree of the polynomial increase, the model twist itself to fit the taining data.

As the degree of polynomial increase, the $J_{cv}(\vec{w},b)$ will first decrease and then increase.
>As the degree of the polynomial increase, the model first generalize better and then overfit the training data.
##### Regularization and Bias/Variance
![[Pasted image 20250918231740.png|400]]
Fig. 2. The influence of the regulatization factor on the bias and variance.
 - With the c increase, the $J_{train}(\vec{w},b)$ will decrease, which means it underfit the training set.
 - With the regularization factor increase $J_{cv}(\vec{w},b)$ will first increase and then decrease, which means the model first overfit the traning data and then underfit the data.
##### Baseline Level of Performance
The **bias** of a model can be  evaluate by the gap between the training error and baseline performance.
The **variance** of a model can be evaluate by the gap between cross validation error and training error.

Common Baseline Performance:
- Human perforamnce
- Competing algorithms performance
- Guess base on experience

##### Learning Curve
**Learning curve** describe the relationship between error and the number of training sample.
### Adding data
- **Data augmentation(数据增强):** modifying an existing training example to create more new training example in order to increase the generalization of the model.
- **Data synthesis(数据合成)：** creating new training example from scratch.
### Transfer Learning(迁移学习)
_**Transfer learning** is a technique where a model trained on one task is repurposed on a second related task. It leverages the knowledge gained from the first task to improve performance on the second task, especially when the second task has limited training data._

>The reason transfer learning works is that the features learned by the model on the first task can be useful for the second task, even if the tasks are not identical. For example, a model trained to recognize objects like cats, dogs, Cars and so on... in images may learn features such as edges, textures, and shapes that are also relevant for recognizing the number.
>
![[Pasted image 20250922181727.png|600]]

**Supervised pretraining**: train a model on a large labeled dataset for a related task.
**Fine-tuning**: use the pretrained model as a starting point and further train it on the smaller labeled dataset for the target task.




# Machine Learning Development Process
The full cycle of machine learning project includes defining the project, collecting and preparing data, choosing and training a model, evaluating and tuning the model, and deploying the model into production.
![[Pasted image 20250923144813.png|600]]

# Skewed Datasets(偏斜数据集)
***Skewed datasets** are datasets where the distribution of classes is imbalanced, meaning that one class has significantly more samples than the other class(es). This can lead to biased models that perform poorly on the minority class.*
## Error metrics for Skewed Datasets
The common error metrics such as accuracy can be misleading when evaluating models on skewed datasets. For example, in a dataset where 99.5% of the samples belong to one class, a model that always predicts the majority class will achieve 99.5% accuracy, but it will fail to identify any instances of the minority class.

### Confusion Matrix(混淆矩阵)
*A **confusion matrix** is a table that summarizes the performance of a classification model by comparing the predicted labels with the true labels. It provides a detailed breakdown of the model's predictions, allowing for the calculation of various performance metrics.*
![[Pasted image 20250923151029.png|400]]
Based on the confusion matrix, we can calculate the following metrics:
- **Precision(准确率)**: The proportion of true positive predictions among all positive predictions made by the model.
$$
\text{Precision} = \frac{TP}{TP + FP}
$$
where TP is the number of true positives and FP is the number of false positives.
- **Recall(召回率)**: The proportion of true positive predictions among all actual positive instances in the dataset.
$$
\text{Recall} = \frac{TP}{TP + FN}
$$
where FN is the number of false negatives.
### Receiver Operating Characteristic Curve（ROC）
**ROC 曲线**（Receiver Operating Characteristic Curve）：横轴是 **False Positive Rate (FPR)**，纵轴是 **True Positive Rate (TPR, Recall)**。
- **TPR (召回率 / 灵敏度)** = TP / (TP + FN)        
- **FPR (假阳性率)** = FP / (FP + TN)
        
**AUC** 全称是 **Area Under the Curve**，指的是 **ROC 曲线下的面积**。取值范围 **[0, 1]**。
AUC 可以看作 **模型区分正负样本的能力**。
> - AUC = 0.5 → 模型没有区分能力，相当于随机猜测>     
> - AUC = 1 → 模型完美区分正负样本>     
> - AUC < 0.5 → 模型预测方向可能反了
## Trading off Precision and Recall
In many applications, there is a **trade-off between precision and recall**. For example, in medical diagnosis, a high recall is often prioritized to ensure that as many positive cases as possible are identified, even if it means accepting a lower precision. Conversely, in spam detection, a high precision may be prioritized to avoid misclassifying legitimate emails as spam.

By changing the decision threshold of the model, we can adjust the balance between precision and recall. A lower threshold will increase recall but may decrease precision, while a higher threshold will increase precision but may decrease recall.
![[Pasted image 20250923152142.png|300]]
Fig. 1 Trade-off between precision and recall.

To obtain a single metric that balances precision and recall, we can use the **F1 score**. which is the harmonic mean of precision and recall:
$$
\text{F1 Score} = \frac{1}{\frac{1}{2} \cdot \left( \frac{1}{\text{Precision}} + \frac{1}{\text{Recall}} \right)} = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$


# Unsupervised Learning
## Clustering
_**Clustering** is an unsupervised learning method that discovers approximate structure in unlabeled data by assigning each data point to a cluster based on a similarity (distance, density, or probabilistic) criterion; the result is a partition (or sometimes overlapping / hierarchical organization) plus optional outliers._
### K-Means
_**K-Means** alternates assigning points to the nearest centroid and updating centroids to the mean of their assigned points to minimize within-cluster squared error._

**Note**: K-Means is sensitive to the initial placement of centroids and may converge to local minima. To mitigate this, it is common to run the algorithm multiple times with different initializations and select the best result based on the lowest within-cluster variance.

**Terminology:** 
- Cluster centroids(簇质心)：the center of the  cluster.

**K-Means Algorithm:**
1. Randomly initialize $K$ cluster centroids $\mu_1,\mu_2,\ldots,\mu_K$.
2. Repeat until convergence:
   - **Assignment step**: Assign each data point $x_i$ to the nearest centroid:
     $$c^{(i)} := \arg\min_k \|x^{(i)} - \mu_k\|^2$$
   - **Update step**: Recalculate the centroids as the mean of the assigned points:
     $$
     \mu_k := \frac{1}{N_k} \sum_{i:c^{(i)}=k} x^{(i)}
     $$
     where $N_k$ is the number of points assigned to centroid $k$.
1. After addignment step, if not data point asssigned to a centroid, it usually will delete this centroid. And some time will re-initialize the process.
#### Optimization objective
The objective of the  K-means is to minimize the distortion function(失真函数) with is the average distance of sample and its coressponding centroid. This is also called the cost function of K-means.

$$
J(c^{(1)}，\ldots,c^{(m)},\mu_1,\ldots,\mu_K) = \frac{1}{m}\sum_{i=1}^m \|x^{(i)} - \mu_{c^{(i)}}\|^2
$$

**Note:** Every step of k-means is trying to
1. reduce the cost funciton by  re-assigning point to cluster,  (the point is re-assigned only if the new centroid is closer) 
2. update the centroid of a cluster(the point that minimize ∫_R ||x − p||² dx is the centroid.)
The cost will only reduce or stay unchange in each step, which means the K-means algorithm will always converge.
#### Initializing K-means
First, randomly pick K training examples.
Set $\mu_1,\mu_2,\dots,\mu_k$ equal to these $K$ examples. 
Since K-means compute the local optimal instead of the global optimal, it's is a better off **run this algorithm with different initializtion** and pick the optimal result.

Note:
- The common run time for K-means is 50-1000.
##### Choosing the Number of Clusters
**ELBO**:
Choose the number of clusters where the curve have a bend and trend of decreasing the vanishing.（Like an ELBOw）
![[Pasted image 20250928151010.png|400]]
**According to the Downstream Procedure**
Evaluate K-means based on a metric for how well it performs for that later purpose.
#### Silhouette Coefficient(轮廓系数)
_**Silhouette Coefficient** is a metric that quantifies how well each data point is clustered by measuring how similar it is to its own cluster compared to other clusters._
For each data point $i$:
1. Calculate $a(i)$: the average distance between $i$ and all other points in the same cluster (intra-cluster distance).
2. Calculate $b(i)$: the minimum average distance between $i$ and all points in any other cluster (nearest-cluster distance).
3. The Silhouette Coefficient for point $i$ is then given by:
   $$
   s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}
   $$
   This value indicates how well the point is clustered: 
	- A value close to 1 indicates that the data point is well clustered.(Distance to the closet point in the other cluster is very large)
	- A value close to 0 indicates that the data point is on or very close to the decision boundary between two neighboring clusters.
	- A value close to -1 indicates that the data point may have been assigned to the wrong cluster.
## Anomaly Detection(异常检测)
# Recommender Systems
_**Recommender system** is a system that can predict the user's favour to an object according to the user's previous voting and the feature of the object._

**With the objects' feature provided:**
To predict the users' favour to an object,  we can build regression model for a user and input the feature of an object and predict the target user's rating to that object. 

_Waht  if we don't have the feature of the objects?_
## Collaborative Filtering(协同过滤)
Collaborative filtering algorithms learn user preferences from previous data and infer object features based on user ratings. 'Collaborative' means that data from different users work together to help the model learn object features.
### Regression Model
1. The feature of object $x^{(i)}$ is given, we can build a regression model to predict the rating of user $j$ to object $i$:
$$y^{(i,j)} = (w^{(j)}) \cdot x^{(i)} + b^{(j)}$$
where $x^{(i)}$ is the feature of object $i$, and $w^{(j)}$,$b^{(j)}$ is the parameter of user $j$'s regression model.
The cost funtion of user $j$'s regression model is:
$$
\begin{align}
J(w^{(j)}, b^{(j)}) =& \frac{1}{2m^{(j)}}\sum \limits_{i:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(j)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \left( \|w^{(j)}\|^2 \right)\\
=&\frac{1}{2}\sum \limits_{i:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(j)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \left( \|w^{(j)}\|^2 \right)
\end{align}
$$

The cost function for all the users is:
$$J(w^{(1)},w^{(2)},\ldots,w^{(n)}, b^{(1)},b^{(2)},\ldots,b^{(n)}) = \sum \limits_{j=1}^n J(w^{(j)}, b^{(j)}) = \sum \limits_{j=1}^n \frac{1}{2}\sum \limits_{i:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(j)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \sum \limits_{j=1}^n\left( \|w^{(j)}\|^2 \right)$$
where $m^{(j)}$ is the number of objects rated by user $j$, and $c(i,j)=1$ if user $j$ rated object $i$, otherwise $c(i,j)=0$.

2. The parameter of user $j$ is given, we can build a regression model to predict the feature of object $i$:
$$y^{(i)} = (w^{(i)}) \cdot x^{(i)}+b^{(i)}$$
where $w^{(i)}$, $b^{(i)}$ is the parameter of user $j$'s regression model, and $x^{(i)}$ is the feature of object $i$.
The cost funtion of object $i$'s regression model is:
$$
\begin{align}
J(x^{(i)}, b^{(i)}) =& \frac{1}{2m^{(i)}}\sum \limits_{j:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(i)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \left( \|x^{(i)}\|^2 \right)\\
=&\frac{1}{2}\sum \limits_{j:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(i)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \left( \|x^{(i)}\|^2 \right)
\end{align}
$$
The cost function for all the objects is:
$$J(x^{(1)},x^{(2)},\ldots,x^{(m)}, b^{(1)},b^{(2)},\ldots,b^{(m)}) = \sum \limits_{i=1}^m J(x^{(i)}, b^{(i)}) = \sum \limits_{i=1}^m \frac{1}{2}\sum \limits_{j:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(i)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \sum \limits_{i=1}^m\left( \|x^{(i)}\|^2 \right)$$
where $m^{(i)}$ is the number of users rated object $i$, and $c(i,j)=1$ if user $j$ rated object $i$, otherwise $c(i,j)=0$.

3. Combine the two models above, we can get the following cost function:
$$
\begin{align}
J(&x^{(1)},x^{(2)},\ldots,x^{(m)}, w^{(1)},w^{(2)},\ldots,w^{(n)}, b^{(1)},b^{(2)},\ldots,b^{(n)}) \\       =& \sum \limits_{i=1}^m J(x^{(i)}, b^{(i)}) + \sum \limits_{j=1}^n J(w^{(j)}, b^{(j)})\\
=& \sum \limits_{i=1}^m \frac{1}{2}\sum \limits_{j:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(i)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \sum \limits_{i=1}^m\left( \|x^{(i)}\|^2 \right) + \sum \limits_{j=1}^n \frac{1}{2}\sum \limits_{i:c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(j)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \sum \limits_{j=1}^n\left( \|w^{(j)}\|^2 \right)\\
=& \frac{1}{2}\sum \limits_{(i,j):c(i,j)=1} \left( (w^{(j)}) \cdot x^{(i)} + b^{(i)} - y^{(i,j)} \right)^2 + \frac{\lambda}{2} \left( \sum \limits_{i=1}^m\left( \|x^{(i)}\|^2 \right) +  \sum \limits_{j=1}^n\left( \|w^{(j)}\|^2 \right) \right)
\end{align}
$$
### Gradient Descent
We can use gradient descent to minimize the cost function above. 
In each step, we update the parameters as follows:
$$
\begin{align}
x^{(i)} &:= x^{(i)} - \alpha \frac{\partial}{\partial x^{(i)}}J(w,b,x)\\
w^{(j)} &:= w^{(j)} - \alpha \frac{\partial}{\partial w^{(j)}}J(w,b,x)\\
b^{(i)} &:= b^{(i)} - \alpha \frac{\partial}{\partial b^{(i)}}J(w,b,x)
\end{align}
$$
### Collaborative Filtering base on Binary Labels
In practice, most user behavior data are binary labels, such as whether a user clicked an ad or not, whether a user watched a video or not and whether a user liked a post or not. In this case, we can use logistic regression to build the model.

#### Meaning of the Label
- label = 1:
    - The user purchased the object.
    - The user has seen the object and liked it.
    - The user spend at least 30 seconds watching the video.
- label = 0:
    - The user do not purchase the object.
    - The user has seen the object and disliked it.
    - The user has seen the video but only watched for a few seconds.
- label = '?':
    - The user has not seen the object.
    - The user has not seen the video.
#### Binary classification model
$$y^{(i,j)}: f_{(w,b,x)}(x) = g(w^{(j)} \cdot x^{(i)} + b^{(j)})$$
where $g(z)$ is the sigmoid function.

##### Cost function
$$
\begin{align}
J(w,b,x) 
= \sum \limits_{(i,j):r(i,j)=1}L(f_{(w,b,x)}(x),y^{(i,j)})
\end{align}
$$
## Mean normalization
To speed up the learning, we can use **mean normalization** to normalize the rating of each object.
## Finding Relating Items
# Reinforcement Learning(强化学习)
 
# Different Network Architectures
 
#### Recurrent Neural Network (RNN，循环神经网络)
**Recurrent Neural Network (RNN)** is a type of neural network where the output at each time step is influenced not only by the current input but also by the hidden state from the previous time step. This hidden state acts as memory, allowing the network to retain contextual information, which makes RNNs suitable for modeling sequential data such as text, speech, and time series.

**Advantages:**
- 序列建模能力    
    - 能处理变长序列数据（文本、语音、时间序列）。        
    - 当前时刻的输出与历史状态相关，能够捕捉上下文依赖。
        
- 参数共享：每个时间步共享相同的权重矩阵，参数量不随输入长度增加，便于训练和泛化。
        
- 适用广泛    
    - 自然语言处理（语言建模、机器翻译、文本生成）        
    - 语音识别、时间序列预测、视频理解等

**Disadvantages:**
- Vanishing Gradient(梯度消失)/Exploding Gradient(爆炸问题)：在长序列中，误差反向传播会导致梯度逐渐衰减或爆炸，难以捕捉长期依赖。        
- 难以建模长程依赖：对超过几十甚至上百步的依赖关系，普通 RNN 表现较差。        
- 训练效率低：由于时间步的依赖，RNN 计算难以并行化（和 Transformer 对比尤其明显）。        
- 记忆有限：隐藏状态容量有限，容易遗忘远处的重要信息。        
- 容易过拟合：在小数据集或长序列任务中，模型可能难以泛化。
##### Exploding Gradient
**Exploding Gradient** is 

**Solution**: Gradient Cliping

#### Gated Recurrent Units (GRU, 门控循环单元)
**Motivation:** The RNN have the vanishing gradient problem when dealing with the long time series.

#### Long Short Term Memory Unit（LSTM, 长短期记忆单元）

#### Transformer
**Transformer** is a neural network architecture built on the Self-Attention and Multi-Head Attention mechanisms. These mechanisms allow the model to capture dependencies between all elements of a sequence in parallel, enabling efficient training and effective modeling of long-range relationships.

**Motivation:** Traditional sequence models such as RNNs, GRUs, and LSTMs process data step by step, making them computationally inefficient and prone to gradient issues when handling long sequences.

##### Self-Attention Mechanism(自注意力机制)
##### Multi-Head Attention Mechanism

# Question

#### Model is a funtion which is build upon the existing data and can be used to predict?

#### What is the difference between Cost function and Loss funciton? 
Cost function is the MSE of the whole training set.
Loss function if the MES of one data set.
The minimal cost function  is the goal of gradien decent.  

#### 能不能用分类模型去判断测序数据能否恢复？是否被污染？
怎么用分类模型去判断金融诈骗？能否借鉴类似的思路？

#### Waht is convex funcion? 凹函数是什么？向上凹？

#### How to calculate the variance of a model?

#### What is the feedback for the Neural Network if there is no validate set? Since deep learning is an unsupervised learning.

#### In K-means, if the final number of clustering is determined by the data set?
# Appendix
- Scikit-learn a python library for machine learning.
- When we use a matrix for great amount of calcualtion, try to define the matrix first and assign a value to it using by index.