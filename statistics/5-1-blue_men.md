[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

This is a classic example of hypothesis testing using the normal distribution. The effect size used here is the Z-statistic.

#### Exercise 5.1

>In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters μ = 178 cm and σ = 7.7 cm for men, and μ = 163 cm and σ = 7.3 cm for women.
>
>In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.

Given that the normal distribution with shape parameters, μ = 178 cm and σ = 7.7 cm adequately models the height of U.S. male population, 34.19% of the population are between 5'10" (177.85 cm) and 6'1" (185.47 cm) tall. 

#### Python Code

```python
import scipy.stats

def convert_height(feet, inches):
    '''
    INPUT: feet, integer
           inches, integer

    OUTPUT: cm, float

    Converts height in feet and inches to centimeters, where 1 cm is 0.0328
    '''
    feet += inches/12
    cm = feet/0.0328

    return cm 


def calculate_percentage(mu, sigma, lower, upper):
    '''
    INPUT: mu, integer/float
          sigma integer/float

    OUTPUT: percentage, float

    Returns the percentage of the normal distribution spanned by the 'lower' and 'upper' values.
    '''
    normal = scipy.stats.norm(loc=mu, scale=sigma)
    cdf_lower = normal.cdf(lower)
    cdf_upper = normal.cdf(upper)

    percentage = cdf_upper - cdf_lower

    return percentage
    

mu = 178
sigma = 7.7

lower = convert_height(5, 10)
upper = convert_height(6, 1)

percentage = calculate_percentage(mu, sigma, lower, upper)

print('{:.2%} of the U.S. male population are between 5\'10\" and 6\'1\"'.format(percentage))

```

