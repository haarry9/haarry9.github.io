---
title: Data Preprocessing Techniques
summary: An Extensive deep-dive into the data preprocessing techniques used in the real-world machine learning pipeline.
date: 2024-07-18

#Featured image
image:
    caption: 'Image credit: **Unsplash**'

authors:
    - admin
    # add additional authors if present to the list

tags:
    - Data Science
    - Data Engineering
    - Machine Learning
---


{{< toc mobile_only=true is_open=true >}}
## Introduction

The real world training data is usually not clean and has many issues such as **missing values** for certain features, features on **different scales, non-numeric attributes** etc. Thus, there is a need to **pre-process** the data to make it amenable for training the machine learning model. 

Some of the typical problems that require pre-processing are:
1. **Missing values** in features
2. Numerical features are **not on** the **same scale**.
3. **Categorical attributes** need to be represented with sensible numerical representation.
4. **Too many features**, reduce the number of features.
5. **Extract features** from non-numeric data.

## SKlearn API

 - <mark>Sklearn</mark> provides a rich set of transformers for data pre-processing.
 - Sklearn provides <mark>pipeline</mark> to chain multiple transforms together and apply them uniformly ***across train, eval and test sets***.

{{% callout warning %}}
The **same pre-processing technique** should be applied to both the training and test set. 
{{% /callout %}}

### Sklearn Transformers

Sklearn provide the following ***library of transformers*** for **data preprocessing**.
- Feature Extraction(`sklearn.feature_extraction`)
- Data Cleaning(`sklearn.preprocessing`) such as **standardization, missing value imputation, feature scaling** etc.
- Feature Reduction(`sklearn.decomposition.pca`)
- Feature Expansion(`sklearn.kernel_approximation`)

#### Transformer methods

Each transformer has the following methods:
- `fit()` method learns model parameters from a training set.
- `transform()` method applies the learnt trasformation to the new data.
- `fit_transform()` performs the function of both `fit()` and `transform()`.

## 1. Data Cleaning

### 1.1. Handling Missing Values
Missing values occur due to errors in data capture such as senosr malfunctioning, measurement errors etc.

<mark>```sklearn.impute```</mark> API provides functionality to fill missing values and contains classes: <mark>SimpleImputer</mark> and <mark>KNNImputer</mark>.

<mark>MissingIndicator</mark>  provides indicators for missing values.

#### 1.1.1. SimpleImputer
- Fills **missing values** with one of the following strategies:
'mean', 'median', 'most_frequent', and 'constant'.

Example usage:
Consider original feature matrix $\mathbf{X}$ 
$$
X = \begin{bmatrix}
7 & 1 \\
nan & 8 \\
2 & nan \\
9 & 6 \\
\end{bmatrix}
$$

```
from sklearn.impute import SimpleImputer
si = SimpleImputer(strategy ='mean')
si.fit_transform(X)
```
- 'nan' in 1st column is filled by their mean, $(7+2+9)/3 = 6$.
- 'nan' in 2nd column is filled by their mean, $(1+8+6)/3 = 5$.

Transformed feature matrix $\mathbf{X}'$
$$
X' = \begin{bmatrix}
7 & 1 \\
6 & 8 \\
2 & 5 \\
9 & 6 \\
\end{bmatrix}
$$

#### 1.1.2. KNNImputer
- Uses **k-nearest neighbors** approach to fill missing values in the dataset.
    - The missing value of an attribute in a specific example is filled with the **mean** value of the same attribute of `n_neighbors` **closest neighbors**.
- The nearest neighbors are decided based on **Eucledian distance**.

Example usage:
Consider original feature matrix $\mathbf{X}$ 
$$
X_{4 \times 3} = \begin{bmatrix}
1 & 2 & nan\\
3 & 4 & 3 \\
nan & 6 & 5 \\
8 & 8  & 7\\
\end{bmatrix}
$$

```
from sklearn.impute import KNNImputer
knni = KNNImputer(n_neighbours = 2, weights = 'uniform')
knni.fit_transform(X)
```

Transformed feature matrix $\mathbf{X}'$
$$
X_{4 \times 3}' = \begin{bmatrix}
1 & 2 & 4\\
3 & 4 & 3 \\
5.5 & 6 & 5 \\
8 & 8  & 7\\
\end{bmatrix}
$$

### 1.2  Numeric Transformers

There are three types of numeric transformers
1. Feature scaling
2. Polynomial transformation
3. Discretization

#### 1.2.1. Feature scaling

Numeical features with different scales leads to slower convergence of iterative optimization procedures like gradient descent, mini batch gradient descent and stochastic gradient descent.
Sklearn provides the following APIs for feature scaling:

- <mark>StandardScalar </mark>
- <mark>MaxAbsScalar </mark>
- <mark>MinMaxScalar </mark>

**StandardScalar**:
Transforms the original feature vector $x$ into a new feature vector $x'$ using the formula
$$
x' = \frac{x - \mu}{\sigma}
$$

{{% callout note %}}
This procedure is also called as ***standardization***.
{{% /callout %}}


Example usage:
Consider original feature matrix $\mathbf{X}$ 
$$
X_{5 \times } = \begin{bmatrix}
4 \\
3 \\
2 \\
5 \\
6 \\
\end{bmatrix}
\text{and} \quad \mu = 4, \sigma = \sqrt 2
$$

```
from sklearn.preprocessing import StandardScaler
ss = StandardScaler()
ss.fit_transform(X)
```

Transformed feature matrix $\mathbf{X}'$
$$
X_{5 \times 1}' = \begin{bmatrix}
0 \\
\frac{-1}{\sqrt 2}\\
\frac{-2}{\sqrt 2}\\
\frac{1}{\sqrt 2}\\
\frac{2}{\sqrt 2}\\
\end{bmatrix} 
\text{and} \quad \mu' =0 , \sigma' = 1
$$

{{% callout note %}}
Note that the transformed feature vector $x'$ has $\mu' =0 , \sigma' = 1$.
{{% /callout %}}

**MinMaxScalar**: Transformes the original feature vector $x$ into new feature vector $x'$ so that all values fall within the range $[0,1]$.
$$
x' = \frac{x - x.min}{x.max - x.min}
$$
where $x.min$ and $x.max$ are smallest and largest values of that feature respectively, of the original feature vector $x$.

{{% callout note %}}
This procedure is also called as ***normalization***.
{{% /callout %}}

Example usage:
Consider original feature matrix $\mathbf{X}$ 
$$
X_{5 \times 1} = \begin{bmatrix}
15 \\
2 \\
5 \\
-1 \\
-5 \\
\end{bmatrix}
x.max = 15, x.min = -5
$$

```
from sklearn.preprocessing import MinMaxScalar
mms = MinMaxScalar()
mms.fit_transform(X)
```

Transformed feature matrix $\mathbf{X}'$
$$
X_{5 \times 1}' = \begin{bmatrix}
1 \\
0.35 \\
0.5 \\
0.6 \\
0 \\
\end{bmatrix} 
$$

{{% callout note %}}
Note that the largest number is transformed to 1 and the smallest number to 0.
{{% /callout %}}

**MaxAbsScalar**: Transformes the original feature vector $x$ into new feature vector $x'$ so that all values fall within the range $[-1,1]$.
$$
x' = \frac{x}{max(x.max,|x.min|)} \\
\text{where, } max(x.max,|x.min|) \text{ is the max absolute value.}
$$

Example usage:
Consider original feature matrix $\mathbf{X}$ 
$$
X_{5 \times 1} = \begin{bmatrix}
4 \\
2 \\
5 \\
-1 \\
-100 \\
\end{bmatrix} \\
\text{MaxAbsoluteValue} = max(5, |-100|) = 100
$$

```
from sklearn.preprocessing import MaxAbsoluteScalar
mas = MaxAbsoluteScalar()
mas.fit_transform(X)
```

Transformed feature matrix $\mathbf{X}'$
$$
X_{5 \times 1}' = \begin{bmatrix}
0.04 \\
0.02 \\
0.05 \\
-0.01 \\
-1 \\
\end{bmatrix} 
$$


#### 1.2.2. Polynomial Transformation

- Polynomial transformation helps us learn non-linear relationships b/n features and labels.
- Polynomial transformation generates a new feature matrix cosisting of all polynomial combinations of the features with degree less than or equal to the specified degree.

#### 1.2.3. Discretization
<mark>KBinsDiscretizer</mark>
- Divides a continuous variable into bins.
- One hot encoding or ordinal encoding is further applied to the bin labels.

$$
X_{9 \times 1} = \begin{bmatrix}
0 \\
0.125 \\
0.25 \\
0.375 \\
0.5 \\
0.675 \\
0.75 \\
0.875 \\
1.0 \\
\end{bmatrix} 
$$

```
XBinsDiscretizer(
    n_bins=5,
    strategy='uniform',
    encode = 'ordinal'
)
```

The entire range is split into 5 different parts or bins.
$$
X_{9 \times 1}' = \begin{bmatrix}
0 \\
0 \\
1 \\
1 \\
2 \\
3 \\
3 \\
4 \\
4 \\
\end{bmatrix} 
$$