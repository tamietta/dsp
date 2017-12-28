[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Cohen's D is an example of effect size. Other examples of effect size are: correlation between two variables, mean difference, regression coefficients and standardized test statistics such as: t, Z, F, etc. In this example, you will compute Cohen's D to quantify (or measure) the difference between two groups of data.

You will see effect size again and again in results of algorithms that are run in data science. For instance, in the bootcamp, when you run a regression analysis, you will recognize the t-statistic as an example of effect size.

#### Exercise 2.4

> Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

#### Cohens' d for First Babies vs. Non-First Babies
* **Pregnancy Length: 0.029** (3 d.p.)
* **Birth Weight: 0.089** (3 d.p.)

The Cohen's *d* effect size for birth weight is approximately three times larger than the Cohen's *d* for pregnancy length. However, both these values are less than 0.1% of their respective standard deviations, and are thus statistically insignificant. 

#### Python Code

```python
import numpy as np
import pandas as pd

import first

live, first, others = first.MakeFrames()

def cohens_d(data1, data2):
    '''
    INPUT: data1, numpy 1D array/pandas Series
           data2, numpy 1D array/pandas Series

    OUTPUT: cohens_d, float

    Computes Cohen's d for the two groups.
    Cohen's d is a test statistic measuring the difference in means as a 
    proportion of the pooled standard deviation.
    '''
    mean1 = data1.mean()
    mean2 = data2.mean()

    var1 = data1.var(ddof=1)
    var2 = data2.var(ddof=1)

    pooled_var = (var1 * data1.size + var2 * data2.size)/(data1.size + data2.size)

    cohens_d = abs(mean1 - mean2)/np.sqrt(pooled_var)

    return cohens_d

# Cohen's d for Pregnancy Length

preg_length = cohens_d(first.prglngth, others.prglngth)

# Cohen's d for Total Weight

total_weight = cohens_d(first.totalwgt_lb, others.totalwgt_lb)

```
