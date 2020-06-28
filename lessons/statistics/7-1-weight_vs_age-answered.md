[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

    import first

    live, firsts, others = first.MakeFrames()
    live = live.dropna(subset=['agepreg', 'totalwgt_lb'])

    bwt, agepreg = live.totalwgt_lb, live.agepreg
    thinkplot.Scatter(agepreg, bwt, alpha=0.1, s=5)
    thinkplot.Config(xlabel="Mother's age at end of preg, in yrs",
                 ylabel='Birth Weight in lbs',
                 axis=[10, 50, 0, 17],
                 legend=False)
                 
    bins = np.arange(10, 46, 2.5)
    indices = np.digitize(live.agepreg, bins)
    groups = live.groupby(indices)

    mean_age = [group.agepreg.mean() for i, group in groups]
    cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups]

    thinkplot.PrePlot(3)
    for percent in [75, 50, 25]:
        weight_percentiles = [cdf.Percentile(percent) for cdf in cdfs]
        label = '%dth' % percent
        thinkplot.Plot(mean_age, weight_percentiles, label=label)
    
    thinkplot.Config(xlabel="Mother's age at end of preg, in yrs",
                 ylabel='Birth weight in lbs',
                 axis=[10, 46, 5, 9],
                legend=False)


    Corr(agepreg, bwt)
   0.0688339703541091

    SpearmanCorr(agepreg, bwt)
   0.09461004109658226

Based on the scatterplot, there doesn't seem to be a strong correlation between the two variables - it seems like there's just an average birth weight across the mother's age.
The correlation coefficients support this - both are very close to 0 (less than 0.1).
Since the correlation coefficients are somewhat varied, it's possible that there is a nonlinear relationship. The lines in the percentile plot seem to suggest this as well.