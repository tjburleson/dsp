[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

    numbers = np.random.random(size=1000)

    numbers_pmf = thinkstats2.Pmf(numbers)
    thinkplot.Pmf(numbers_pmf)

The PMF shows the probability of each number being included in the generated 1000. Since numbers randomly generated 1000 numbers, the probability of any number being generated should be the same (uniform distribution). However, graphed as a PMF, it simply looks like a block of color because there are so many data points (which also means the probability for each is quite small), each with similar probability.

    numbers_cdf = thinkstats2.Cdf(numbers)
    thinkplot.Cdf(numbers_cdf)
    thinkplot.Config(xlabel='percentile rank', ylabel='CDF')

The distribution is uniform because the probability linearly approaches 1.0 as numbers increases. This means that 20% of the numbers generated are below the 20th percentile, and 30% are below the 30th percentile, etc.