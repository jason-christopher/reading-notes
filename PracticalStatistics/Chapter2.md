# Chapter 2: Data and Sampling Distributions

## Random Sampling and Sample Bias

A **random sample** is a sample taken from a population where each member of the population has an equal chance of being selected. Random sampling is important for ensuring that the sample is representative of the entire population. In practice, true random sampling is often difficult to achieve.

**Sample bias** occurs when the sample is not representative of the population, leading to incorrect conclusions about the population. Sample bias can be introduced through various factors, such as non-random sampling, selection bias, or nonresponse bias.

To avoid sample bias, data scientists should strive for random sampling, be cautious about generalizing results from convenience samples, and consider using techniques to adjust for known biases.

## Selection Bias

**Selection bias** occurs when the sample is systematically different from the population due to the way it is selected. Some common types of selection bias include:

- **Nonresponse bias**: When individuals who are selected for a sample do not respond, and their nonresponse is related to the variable being studied.
- **Survivorship bias**: When data is only available for individuals who "survived" some process or selection criteria, causing a distortion in the sample.

Data scientists must be aware of the potential for selection bias and carefully design their sampling strategies to minimize its impact.

## Sampling Distribution of a Statistic

The **sampling distribution of a statistic** is the distribution of the statistic computed from all possible samples of a given size from a population. It is important to understand the sampling distribution because it allows us to quantify the uncertainty in our estimates and make inferences about the population.

Suppose we have a population and we draw a random sample of size *n*. Let's say we compute the sample mean, denoted as *x̄*. If we repeatedly draw random samples of the same size from the population and compute the sample mean each time, we will obtain a distribution of sample means. This is the sampling distribution of the sample mean.

In Python, we can simulate the sampling distribution of the sample mean using the following code:

```python
import numpy as np

population = np.random.normal(loc=0, scale=1, size=10000)
sample_size = 100
n_samples = 1000
sample_means = []

for _ in range(n_samples):
    sample = np.random.choice(population, size=sample_size)
    sample_mean = np.mean(sample)
    sample_means.append(sample_mean)
```

## Central Limit Theorem

The **Central Limit Theorem (CLT)** is a fundamental concept in statistics that states that, for large sample sizes, the sampling distribution of the sample mean approaches a normal distribution with the same mean as the population and a standard deviation equal to the population standard deviation divided by the square root of the sample size.

The CLT is important because it allows us to make inferences about the population mean using the normal distribution, even if the population distribution is not normal. It also helps us understand the concept of **standard error**.

## Standard Error

**Standard error** is a measure of the variability in a sample statistic, such as the sample mean, due to random sampling. It is the standard deviation of the sampling distribution of the statistic. The standard error gives us an idea of how much our sample statistic might vary from the true population parameter. Smaller standard errors indicate more precise estimates.

For the sample mean, the standard error can be calculated as:

$$
SE = \frac{\sigma}{\sqrt{n}}
$$

Where *σ* is the population standard deviation and *n* is the sample size. When the population standard deviation is unknown, the sample standard deviation (*s*) can be used as an estimate.

In Python, we can compute the standard error of the sample mean using the following code:

```python
import numpy as np

sample = np.random.normal(loc=0, scale=1, size=100)
sample_std_dev = np.std(sample, ddof=1)  # ddof=1 for unbiased estimator
standard_error = sample_std_dev / np.sqrt(len(sample))
```

## Bootstrap

The **bootstrap** is a powerful resampling technique used to estimate the sampling distribution of a statistic. By repeatedly drawing random samples with replacement from the original sample, the bootstrap generates many "bootstrap samples" which can be used to compute the statistic of interest. This results in an empirical distribution of the statistic, allowing us to estimate its standard error, confidence intervals, and other characteristics.

In Python, we can perform a simple bootstrap to estimate the standard error of the sample mean using the following code:

```python
import numpy as np

def bootstrap_sample(data, n_samples):
    return np.random.choice(data, size=n_samples, replace=True)

sample = np.random.normal(loc=0, scale=1, size=100)
bootstrap_means = [np.mean(bootstrap_sample(sample, len(sample))) for _ in range(1000)]
bootstrap_standard_error = np.std(bootstrap_means, ddof=1)
```

## Confidence Intervals

**Confidence intervals** provide a range of values within which the true population parameter is likely to fall, with a specified level of confidence. For example, a 95% confidence interval for the population mean indicates that we are 95% confident that the true population mean falls within the calculated range.

For the sample mean, we can calculate the confidence interval using the standard error and the appropriate critical value from the normal distribution (or t-distribution if the sample size is small). The confidence interval is defined as:

$$
CI = \bar{x} \pm z \times SE
$$

Where *x̄* is the sample mean, *z* is the critical value, and *SE* is the standard error.

In Python, we can compute the 95% confidence interval for the sample mean using the following code:

```python
import numpy as np
import scipy.stats as stats

sample = np.random.normal(loc=0, scale=1, size=100)
sample_mean = np.mean(sample)
sample_std_dev = np.std(sample, ddof=1)
standard_error = sample_std_dev / np.sqrt(len(sample))
critical_value = stats.norm.ppf(0.975)  # 0.975 for a two-tailed 95% CI

confidence_interval = (sample_mean - critical_value * standard_error,
                       sample_mean + critical_value * standard_error)
```

## Normal Distribution

The **normal distribution**, also known as the Gaussian distribution or bell curve, is a continuous probability distribution that is symmetric around the mean and characterized by its mean (*µ*) and standard deviation (*σ*). Many natural phenomena and sample statistics follow the normal distribution, making it an important concept in statistics and data science.

The probability density function of the normal distribution is defined as:

$$
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$

Where *x* is the value, *µ* is the mean, and *σ* is the standard deviation.

In Python, we can work with the normal distribution using the `scipy.stats` module:

```python
import numpy as np
import scipy.stats as stats

mean = 0
std_dev = 1
x_values = np.linspace(-5, 5, 100)
pdf_values = stats.norm.pdf(x_values, loc=mean, scale=std_dev)
```

## Long-Tailed Distributions

**Long-tailed distributions** are probability distributions with tails that extend farther than the tails of the normal distribution. They have more extreme values, or outliers, than would be expected in a normal distribution. Examples of long-tailed distributions include the exponential, Pareto, and log-normal distributions.

When working with long-tailed distributions, data scientists should be cautious about using methods that rely on the normal distribution, such as the Central Limit Theorem and standard parametric tests. Nonparametric tests and robust statistics might be more appropriate in these cases.

## Student's t-Distribution

The **Student's t-distribution** is a probability distribution that is similar to the normal distribution but with heavier tails. It is used to estimate the mean of a normally distributed population when the sample size is small and the population standard deviation is unknown.

The t-distribution is characterized by its degrees of freedom (*df*), which is related to the sample size. As the degrees of freedom increase, the t-distribution approaches the normal distribution.

When working with small samples, data scientists should use the t-distribution instead of the normal distribution to compute confidence intervals and perform hypothesis tests.

In Python, we can work with the t-distribution using the `scipy.stats` module:

```python
import numpy as np
import scipy.stats as stats

degrees_of_freedom = 10
x_values = np.linspace(-5, 5, 100)
pdf_values = stats.t.pdf(x_values, df=degrees_of_freedom)
```

## Summary

In conclusion, understanding data and sampling distributions is crucial for data scientists as it forms the foundation of statistical inference. It is important to recognize potential biases in the data and ensure that the sample is representative of the population. Moreover, being aware of the Central Limit Theorem, standard error, and various probability distributions can help data scientists make better decisions about which statistical methods to apply in different situations.
