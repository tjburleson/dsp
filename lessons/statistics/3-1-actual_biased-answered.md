[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

    kidspmf = thinkstats2.Pmf(resp['numkdhh'], label='actual')
    biased_kidspmf = BiasPmf(kidspmf, 'observed')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([kidspmf, biased_kidspmf])
    thinkplot.Config(xlabel='Number of Kids', ylabel='PMF')

    print("Actual Mean", kidspmf.Mean())
    print("Observed Mean", biased_kidspmf.Mean())

   Actual Mean 1.024205155043831
   Observed Mean 2.403679100664282