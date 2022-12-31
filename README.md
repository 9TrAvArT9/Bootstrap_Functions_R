# Bootstrap_Functions_R
This is a repository to demonstrate bootstrapping functions developed in R. Here, there are also examples of applications in statistical analysis. 

[examples](https://github.com/9TrAvArT9/Bootstrap_Functions_R/blob/main/Bootstrap_Functions.md)

Bootstrap_Functions
================
R. Travis Merrill
2022-12-24

## Distribution Functions

\##Estimating the population distribution when considering population
size. <br>

\#Large population: Generally N/n \> 20, we sample *with* replacement
from a *single* copy of the sample

\##Small population with N/n = a \< 20 and an *integer*. We sample
*without* replacement from *a* copies of the sample.

\#For populations such that N/n = b \< 20, b *not* an integer, we use
the methods of Booth, Butler, and Hall (1994). The idea is to randomly
adjust the composition of the population estimate several times in an
attempt to balance out case representation, and avoid bias.

### Examples using functions.

``` r
#This synthesized examples pertain to a sample of 7 laboratory mice. Suppose these scores pertain to the post surgery survival time, in days, of mice after given pre-surgical treatment.


micedata = c(94, 197, 16, 38, 99, 141, 23);


bootmedplus(micedata,7,2500)
```

    ## $SE
    ## [1] 38.84282
    ## 
    ## $bias
    ## [1] -14.3252
    ## 
    ## $NormalCI
    ## [1]  30.10356 157.89644
    ## 
    ## $SCI
    ## [1]  23 141
    ## 
    ## $NSCI
    ## [1]  47 165

``` r
#Suppose we know that N = 28. Then we have 

micedata1 = rep(micedata,28/7)

bootmedplus(micedata1,7,2500)
```

    ## $SE
    ## [1] 38.01481
    ## 
    ## $bias
    ## [1] -14.4
    ## 
    ## $NormalCI
    ## [1]  31.46563 156.53437
    ## 
    ## $SCI
    ## [1]  23 141
    ## 
    ## $NSCI
    ## [1]  47 165

``` r
#Now suppose that N = 31. Then we have 
BBHmedplus(micedata, 31, 7, 10, 250)
```

    ## $SE
    ## [1] 33.42869
    ## 
    ## $bias
    ## [1] -15.8912
    ## 
    ## $NormalCI
    ## [1]  39.0098 148.9902
    ## 
    ## $SCI
    ## [1]  23 141
    ## 
    ## $NSCI
    ## [1]  47 165

``` r
#Notice the similarities in the outputs of these two methods. 
```
