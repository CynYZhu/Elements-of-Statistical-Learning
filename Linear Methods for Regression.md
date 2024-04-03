# Linear Methods for Regression

Linear Regression model has the form 

![Screen Shot 2023-02-02 at 12.42.55 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-02_at_12.42.55_PM.png)

$`X_j`$ can come from different sources

1. quantitative inputs
2. transformation of quantitative inputs, such as log, square-root, or square
3. numeric or dummy coding of the levels of qualitative inputs. EX, low, medium, high - 1,2,3
4. interaction between variables, X = X1*X2

The most popular estimation method is **least squares**, in which we pick the coefficients β = (β0, β1, . . . , βp)T to **minimize the residual sum of squares**

## Simple Linear Regression

### RSS, ESS, TSS

Residual sum of squares -  RSS: 

![Screen Shot 2023-02-03 at 2.55.03 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_2.55.03_PM.png)

![Screen Shot 2023-02-03 at 2.59.45 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_2.59.45_PM.png)

$\hat{y_i}$ - predicted y (at each point)

$\bar{y}$ - mean of y (single value, mean of all ys)

TSS: total variance of inherent in the response **before the regression is performed.** 

RSS: measure the amount of variability that is left **unexplained** after performing the regression. 

ESS: measures the amount of variability that is **explained** after performing the regression. 

$TSS = RSS + ESS$

![Screen Shot 2023-02-03 at 3.05.59 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_3.05.59_PM.png)

$R^2$ -  measures the proportion of the variability in Y that can be explained using X. 

$R^2$ vs Correlation?

## Multiple Linear Regression model

![Screen Shot 2023-02-03 at 3.16.50 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_3.16.50_PM.png)

## F statistics

- measures the change of residual sum of squares (RSS) per additional parameter in the bigger model, and it is normalized by an estimate of $σ^2$

![Screen Shot 2023-02-03 at 3.18.12 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_3.18.12_PM.png)

- p = number of predictors

![Screen Shot 2023-02-03 at 3.26.28 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-03_at_3.26.28_PM.png)

**[When to use F-test.](https://www.statisticshowto.com/probability-and-statistics/f-statistic-value-test/#Regression)**

- both p-value and f-statistics need to be significant

# Subset Selection

- Variable subset selection with linear regression

## Best-subset Selection

- ISL P205
- very computationally expansive / brute force finding the best combination of features from feature space $2^p$ (p=total num of features)
- choose k that minimizes the estimate of the expected prediction error

## Stepwise Selection

### Forward-stepwise selection

- forward stepwise can always be used whether n>>p or n<<p
- starts with the intercept, and then sequentially adds into the model the predictor that most improves the fit.
- a greedy algo, large computation
- pros:
    - less expensive than best-subset approach, even when p>>N
    - will have lower variance, but perhaps more bias

### Backward-stepwise selection

- Backward-stepwise selection starts with the full model, and sequentially deletes the predictor that has the least impact on the fit.
- The candidate for dropping is the variable with the smallest Z-score (Exercise 3.10). Backward selection can only be used when N > p, while **forward stepwise can always
be used.**

### Simulation to compare selection methods

![Screen Shot 2023-02-02 at 3.15.56 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-02_at_3.15.56_PM.png)

- y - MSE
- forward and backward stepwise performs the same
- forward stagewise takes longer to reach the min error.

Others to select: 

- AIC criterion: (not always used anymore)
    - AIC criterion for weighing the choices, which takes proper account of the number of parameters fit; at each step an add or drop will be performed that minimizes the AIC score.
- F-Statistics: (not always used anymore)

### Stagewise regression

- Steps:
    1. it starts like forward-stepwise regression, with an intercept equal to mean y, and centered predictors with coefficients initially all 0. 
    2. At each step the algo identifies the variable most correlated with the current residual
    3. it then computes the simple linear regression coefficient of the residual on this chosen variable, and then adds it to the current coefficient for that variable. This is continued till none of the variables have correlation with the residual. 
- works well with high dimensional problems.
- 

Lasso and Ridge

![Screen Shot 2023-02-02 at 4.20.11 PM.png](Linear%20Methods%20for%20Regression%20c790e18346fb43598bf8e402a1a530ad/Screen_Shot_2023-02-02_at_4.20.11_PM.png)

region for ridge regression is the disk $β_1^2 + β_2^2 ≤ t$, while that for lasso is
the diamond $|β_1| + |β_2| ≤ t$.