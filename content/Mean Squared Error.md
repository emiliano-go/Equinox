In [[06_Statistical_Analysis/Statistical Analysis|Statistical Analysis]], the **Mean Squared Error** (MSE), also called **Mean  Squared Deviation** (MSD), of an [[Estimator|estimator]] measures the **average** of the square of the errors. This is the average [[Squared Difference|squared difference]] between the **estimated** values and the [[True Value|true value]].

**MSE** is a [[Risk Function|risk function]], corresponding to the expected value of the [[Squared Error Loss]]. It's a measure of quality of the estimator. 

It is always a positive value that decreases as the error approaches 0.

The MSE is the **second** [[Moment|moment]] (**about the origin**) of the error. This means it incorporates the [[Variance]] of the estimator (how the estimates are spread from one data sample) and it's [[Bias|bias]] (how far off the average estimated value is from the true value). 

For an [[Unbiased Estimator|unbiased estimator]], the MSE is the variance of the estimator. 

## Definition and Properties

The MSE either asses the quality of a [[Predictor|predictor]] or of an [[Estimator|estimator]]. The **definition** of an MSE differs according to whether one is describing a predictor or an estimator.

### Predictor

If a vector of $n$ is generated from a sample data of $n$ data points on all variables, and $Y$ is the vector of observed values being predicted, and $\hat{Y}$ being the predicted values, then the MSE is computed as: $$ MSE = \frac{1}{n}\sum_{i=1}^n(Y_{i}-\hat{Y_{i}})$$
### Estimator

The MSE of an **estimator** with respect to an unknown parameter $\theta$ is defined as the [[Expected Value|expected value]] of $\theta$ of the squared difference between the estimator and the parameter. 
$$ MSE(\hat{\theta}) = E_{\theta}[(\hat{\theta}-\theta)²]$$
The MSE can be written as the **sum** of the **variance** of the estimator and the squared **bias** of the estimator. This means that, for an unbiased estimator, the MSE and the variance are equivalent.

