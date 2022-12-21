DataScience - Honey Production in the USA
================
Martina Djordjijevic
2022-09-28

- <a href="#introduction" id="toc-introduction">Introduction</a>
- <a href="#research-questions" id="toc-research-questions">Research
  questions</a>
- <a href="#data-analysis" id="toc-data-analysis">Data analysis</a>
- <a href="#trends-in-data" id="toc-trends-in-data">Trends in data</a>
- <a href="#conclusion" id="toc-conclusion">Conclusion</a>
- <a href="#references--source-for-dataset"
  id="toc-references--source-for-dataset">References &amp; Source for
  dataset</a>

# Introduction

Bees have been around for many millennia, however in most recent times
the hardworking colonies face many trials and tribulations due to
various factors such as an extensive use of pesticides, loss of habitat
– mostly because of rapid urbanization, unusually warm winters that
cause a shift in plant development etc. The importance of these insects
in the process of pollination is undeniable, valid for both wild bees
and honeybees, hence the rapid decline in the number of their colonies
presents a problem not only on the more global level in the nature, but
also to the world agricultural output economic value. (Gallai et al.,
2009)

Back in 2006, there was a huge decline in the honeybee population
reported mostly in North America, which had a huge impact on the
American honey agriculture. This decline was due to the Colony Collapse
Disorder, a phenomenon reported in many countries and continents since
1998.

Let’s take a look at Wikipedia’s definition (“Colony Collapse Disorder,”
2022) of this phenomenon:

> > > Colony collapse disorder (CCD) is an abnormal phenomenon that
> > > occurs when the majority of worker bees in a honey bee colony
> > > disappear, leaving behind a queen, plenty of food, and a few nurse
> > > bees to care for the remaining immature bees.

It is important to note that this phenomenon also causes the remaining
hive colony to collapse. The cause of the decline of 2006 is probably to
be found in hive diseases and pesticides harming the pollinators, as
these two processes are highly correlated, though no real consensus was
reached. Ever since the collapse, the American honey industry has been
largely struggling. After the collapse the U.S. is forced to import
large amounts of honey, more precisely 350 of the 400 million pounds
each year, which is in stark contrast to this industries brilliant past
when almost half the honey consumed was produced locally. (Ferdman,
2021)

The dataset analysed here gives insight into honey production supply and
demand in America by state from 1998 to 2012. This dataset does not
provide any variables that might reveal causal relationships regarding
colony collapse disorder, it is instead focused on honey production.
However I find it important to mention such phenomenon, not only because
it is of general importance, but also because it explains the decline in
honey production.

![](closeup-shot-bee-chamomile-flower.jpg)

# Research questions

As the data set is fairly large, there’s a number of different things
one might focus on. After spending some time reading about honey
production and also looking at this specific data set, the thing that
marked my interest the most was the relationship between honey
production and number of colonies through time. The questions I find
most relevant regarding that would be the following:

- *Which states have the most bee colonies?*
- *Which states produce the most honey?*
- *What happens to the rates of production over time?*
- *What about the prices, do they get higher over time?*
- *Are there any trends in honey production related to the number of
  colonies?*

This will be a simple exploratory data analysis on the production of
honey in the U.S. focusing on the following hypotheses:

**H0** - Number of bee colonies in any state has no impact on honey
production.

**H1** - Number of bee colonies in any state has impact on honey
production.

# Data analysis

Firstly, let’s take a quick look at the data we’ll be analyzing.

    ##   state numcol yieldpercol totalprod   stocks priceperlb prodvalue year
    ## 1    AL  16000          71   1136000   159000       0.72    818000 1998
    ## 2    AZ  55000          60   3300000  1485000       0.64   2112000 1998
    ## 3    AR  53000          65   3445000  1688000       0.59   2033000 1998
    ## 4    CA 450000          83  37350000 12326000       0.62  23157000 1998
    ## 5    CO  27000          72   1944000  1594000       0.70   1361000 1998
    ## 6    FL 230000          98  22540000  4508000       0.64  14426000 1998

Here’s also a description of each column’s content:

- *numcol*: Number of honey producing colonies, more precisely the
  maximum number of colonies from which honey was taken during the year.
- *yieldpercol*: Honey yield in pounds per colony.
- *totalprod*: Total production in pounds (numcol x yieldpercol).
- *stocks*: Refers to stocks in pounds held by producers.
- *priceperlb*: Refers to average price per pound, in dollars, based on
  expanded sales.
- *prodvalue*: Value of production in dollars (totalprod x priceperlb).

This dataset is rather rich in information. However the first thing I’d
like to investigate further is the relationship between the states and
number of honey producing colonies. Let’s plot a box plot of state and
numcol to verify this.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

Let’s try finding outliers and eliminating them, so our boxplot makes
more sense.

    ##   25%   75% 
    ##  9000 63750

    ## [1] 54750

![](Data-Practicle_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

As expected, the box plot shows differences between the states. Let’s
plot a histogram of 20 states with the highest number of bee colonies.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

It appears that four states with the highest number of colonies are
California(CA), North Dakota(ND), South Dakota(SD) and Florida(FL).

What are some other questions we could pose regarding the data set?
**Which states produce the most honey?**

To see this let’s take a look at the total honey production in every
state. We could plot that on a U.S. map.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

This plot looks lovely, but it’s kind of hard to read. Let’s plot 20
states with the largest production on a histogram.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

In this plot we can see top 20 states in honey production, with North
Dakota(ND), California(CA) South Dakota(SD) and Florida(FL) as the four
major states producing honey. This adds up to what we’ve seen before,
those were also the four states with the highest number of bee colonies.

Finally, we could plot the change in total honey production over the
period from 1998 to 2012, to see whether there was an overall increase
or decrease depending on the state.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

What we can see from this plot is that the total honey production
decreases for most states, however only North Dakota (ND) recorded
significant increase.

# Trends in data

We can also look at some existing trends in our dataset. **What happens
to the rates of honey production over time?** because there is a huge
drop of number of colonies existing, it should be expected that the
total honey production is also dropping. Let’s verify if that is
correct.

    ## 'data.frame':    626 obs. of  8 variables:
    ##  $ state      : chr  "AL" "AZ" "AR" "CA" ...
    ##  $ numcol     : num  16000 55000 53000 450000 27000 230000 75000 8000 120000 9000 ...
    ##  $ yieldpercol: int  71 60 65 83 72 98 56 118 50 71 ...
    ##  $ totalprod  : num  1136000 3300000 3445000 37350000 1944000 ...
    ##  $ stocks     : num  159000 1485000 1688000 12326000 1594000 ...
    ##  $ priceperlb : num  0.72 0.64 0.59 0.62 0.7 0.64 0.69 0.77 0.65 1.19 ...
    ##  $ prodvalue  : num  818000 2112000 2033000 23157000 1361000 ...
    ##  $ year       : int  1998 1998 1998 1998 1998 1998 1998 1998 1998 1998 ...

![](Data-Practicle_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

As seen from the plot above, honey production has been decreasing over
time. But **what about the prices?** We can expect that the price will
increase over time. Let’s verify that.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

The plot confirms that the prices have been going up over the years.

Finally, let’s plot the number of colonies and honey production
together, in order to observe their development over time.

![](Data-Practicle_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

From this plot we can conclude that *as the number of colonies
decreases, so does the honey production*.

- Additionally, the number of colonies begins dropping from 1999,
  however the honey production is in a surge from 1999 to 2000.This is
  explained by the fact that honey can be collected even from collapsed
  colonies. However, as expected there was a huge drop in honey
  production in the period from 2000 to 2002, which is directly
  influenced by the collapsed colonies from 1999 onward. This pattern is
  found again in the period from 2006 to 2008.

- After 2008 up to 2010 the number of colonies increase rapidly, which
  leads to an increase in production.

# Conclusion

As we’ve seen in the previous sections, honey production is highly
dependent on the number of bee colonies. The states that produce the
most honey had the biggest number of bee colonies. Additionally, as the
number of bee colonies dropped, so did the production of honey. We can
safely reject our **H0** in favor of the **H1** - Number of bee colonies
in any state has impact on honey production.

# References & Source for dataset

The clean version of this dataset was provided by Kaggle, however the
original raw dataset was from the USDA’s National Agricultural
Statistics Service (NASS).

<a href="https://www.freepik.com/free-photo/closeup-shot-bee-chamomile-flower_13411366.htm#query=bee&position=29&from_view=search&track=sph">Image
by wirestock</a> on Freepik

April 29, & Zissu, 2022 Alexandra. (n.d.). Colony Collapse Disorder: Why
Are Bees Dying? NRDC. Retrieved December 10, 2022, from
<https://www.nrdc.org/stories/buzz-about-colony-collapse-disorder>

Colony collapse disorder. (2022). In Wikipedia.
<https://en.wikipedia.org/w/index.php?title=Colony_collapse_disorder&oldid=1123481094>

Data Analysis of Honey Production. (n.d.). Retrieved December 12, 2022,
from
<https://kaggle.com/code/koki25ando/data-analysis-of-honey-production>

Ferdman, R. A. (2021, November 25). Dying honeybees, and the uncertain
future of honey. Washington Post.
<https://www.washingtonpost.com/news/wonk/wp/2015/05/14/dying-bees-could-mean-the-end-of-american-honey/>

Gallai, N., Salles, J.-M., Settele, J., & Vaissière, B. E. (2009).
Economic valuation of the vulnerability of world agriculture confronted
with pollinator decline. Ecological Economics, 68(3), 810–821.
<https://doi.org/10.1016/j.ecolecon.2008.06.014>

Honey Production in the USA (1998-2012). (n.d.). Retrieved December 12,
2022, from
<https://www.kaggle.com/datasets/jessicali9530/honey-production>

Honey Production in USA (1998-2012). (n.d.). Retrieved December 12,
2022, from
<http://rstudio-pubs-static.s3.amazonaws.com/453012_5f25e98ad0184f0da25b99e9c1ea42eb.html>

Honey Production USA. (n.d.). Retrieved December 12, 2022, from
<https://kaggle.com/code/jcraggy/honey-production-usa>

Ten years since the colony collapse crisis began, what is happening to
the world’s bees? (2017, May 8). ABC News.
<https://www.abc.net.au/news/2017-05-08/colony-collapse-ten-years-after-crisis-what-is-happening-to-bees/8507408>
