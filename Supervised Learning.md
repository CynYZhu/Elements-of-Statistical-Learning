# Supervised Learning

# Key points

- Regression and classification.
- Least Squares (LS) vs K-Nearest Neighbors (KNN)
- Curse of Dimensionality
- Central Limit Theorem
- Assumptions of Linear Regression

# Main types of models

- Regression: predict quantitative outputs
- Classification: predict qualitative outputs

# Least Squares

LS vs KNN: two extreme examples of models in the spectrum.

Linear model: assumed structure 

KNN: non-parametric. Assumes no structure.

<aside>
💡 The linear model makes huge assumptions about structure and yields stable but possibly inaccurate predictions.

</aside>

![Screen Shot 2023-02-01 at 1.11.23 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_1.11.23_PM.png)

- Linear model in vector form
    
    ![Screen Shot 2023-02-01 at 1.11.35 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_1.11.35_PM.png)
    
    - $X^T$ denotes vector or matrix transpose. X being a column vector ($m * 1$ - matrix with 1 column)
    - Y hat is a scalar
- General linear model form:

![Screen Shot 2023-02-01 at 1.18.19 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_1.18.19_PM.png)

# L**east squares**

- Core: pick the coefficient beta to minimize residual sum of squares RSS
    - stable - result in low variance but high bias (**heavy assumption** on the linear decision boundary)

![Screen Shot 2023-02-01 at 1.24.25 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_1.24.25_PM.png)

# KNN

![Screen Shot 2023-02-01 at 1.27.49 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_1.27.49_PM.png)

- non-parametric model
- n >> p
- Uses metric Euclidean distance - we find the k observations with $x_i$ closest to x in input space and average their responses, assign y hat to y if the distance of x is close to x
- Unstable - high variance but low bias (no assumption on shape of data / can single out various shape of subregions)
- Tend to overfit

# **[Curse of dimensionality](https://www.youtube.com/watch?v=oTSj0TTDSPI)**

- Feature selection / dimensionality
    - dimensions  = features or attributes
    - with more dimensions, you need large amount of data whose features are abundant in each feature/dimension (otherwise scarcity of feature/data points will confuse the model); otherwise, large set of features are not useful. Only save the informative features.
    - this is why we need to do  feature selection / dimensionality reduction

<aside>
💡 if we wish to be able to estimate such functions with the **same accuracy as** function in low dimensions, then we need the size of our training set to grow exponentially as well.

</aside>

# Bias-variance decomposition -  MSE

![Screen Shot 2023-02-01 at 2.35.06 PM.png](Supervised%20Learning%20ced8984fe6494977a7a39d430247a59d/Screen_Shot_2023-02-01_at_2.35.06_PM.png)

two components: variance +  squared bias

Statistical Models, Supervised Learning and Function Approximation

# **Central Limit Theorem**

If you repeatedly sample a random variable a large number of times, the distribution of sample mean will approach a normal distribution regardless of the initial distribution. 

# **[Assumptions of Linear Regression](https://www.youtube.com/watch?v=-qXMA7mOecg)**

1. **X and Y has linear relationship. <MUST MEET>**
    1. **diagnose**: residual on y-axis , predicted value of y on x-axis; points should be symmetrically distributed around the line
2. **Residuals are independent. <MUST MEET>**
    1. often violated if time series, the successive residual tend to be positive. 
    2. **diagnose**: 
        1. check if data is collected in a sequence. whether observe a pattern
        2. using y vs x; residuals vs predicted values 
3. **The residuals are normally distributed. <NICE TO HAVE> Multivariate Normal - lienar combination of variables should follow a normal distribution**
    1. CLT gives us the parameter estimates and predicted values of the dependent variable are approximately normally distributed even if the residuals are not. 
    2. Violation of normality
    3. **diagnose:**
        1. **histogram** (count vs variable) AND check **quantile-quantile(Q-Q) plot** of the residuals. if the distribution of residuals is normal then the shape should follow a linear line. 
4. **Residuals should have equal variance (homoscedasticity)** **<less important>**
    1. the residuals should have approximately equal variances. 
    2. **diagnose:** check residual plot