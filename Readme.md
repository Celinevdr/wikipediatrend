# wikipediatrend

# Author

Peter Meißner



# Last Update

2015-10-05





# Status (current version on Github)



<table>
<tr>
<td> 
Ubuntu build 
</td>
<td> 
<a href="https://travis-ci.org/petermeissner/wikipediatrend">
<img src="https://api.travis-ci.org/petermeissner/wikipediatrend.svg?branch=master">
</a>
</td>
</tr>
<tr>
<td> 
Windows build
</td>
<td> 
<a href="https://ci.appveyor.com/project/petermeissner/wikipediatrend">
<img src="http://ci.appveyor.com/api/projects/status/github/petermeissner/wikipediatrend">
</a>
</td>
</tr>
<tr>
<td>
Version on CRAN  
</td> 
<td>
<a href="https://cran.r-project.org/web/packages/wikipediatrend/index.html">
<img src="http://www.r-pkg.org/badges/version/wikipediatrend">
</a>
</td>
</tr>
<tr>
<td>
Version on Github
</td> 
<td>
<a href="https://github.com/petermeissner/wikipediatrend"> <img src="data:image/svg+xml; charset=utf-8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNzAiIGhlaWdodD0iMjAiPgogPGxpbmVhckdyYWRpZW50IGlkPSJiIiB4Mj0iMCIgeTI9IjEwMCUiPgogPHN0b3Agb2Zmc2V0PSIwIiBzdG9wLWNvbG9yPSIjYmJiIiBzdG9wLW9wYWNpdHk9Ii4xIi8+CiA8c3RvcCBvZmZzZXQ9IjEiIHN0b3Atb3BhY2l0eT0iLjEiLz4KIDwvbGluZWFyR3JhZGllbnQ+CiA8bWFzayBpZD0iYSI+CiA8cmVjdCB3aWR0aD0iMTcwIiBoZWlnaHQ9IjIwIiByeD0iMyIgZmlsbD0iI2ZmZiIvPgogPC9tYXNrPgogPGcgbWFzaz0idXJsKCNhKSI+PHBhdGggZmlsbD0iIzU1NSIgZD0iTTAgMGg3MHYyMEgweiIvPgogPHBhdGggZmlsbD0iIzRjMSIgZD0iTTcwIDBoOTl2MjBINzB6Ii8+CiA8cGF0aCBmaWxsPSJ1cmwoI2IpIiBkPSJNMCAwaDE3MHYyMEgweiIvPgogPC9nPgogPGcgZmlsbD0iI2ZmZiIgdGV4dC1hbmNob3I9Im1pZGRsZSIKIGZvbnQtZmFtaWx5PSJEZWphVnUgU2FucyxWZXJkYW5hLEdlbmV2YSxzYW5zLXNlcmlmIiBmb250LXNpemU9IjExIj4KIDx0ZXh0IHg9IjM2IiB5PSIxNSIgZmlsbD0iIzAxMDEwMSIgZmlsbC1vcGFjaXR5PSIuMyI+CiBHaXRodWIKIDwvdGV4dD4KIDx0ZXh0IHg9IjM2IiB5PSIxNCI+CiBHaXRodWIKIDwvdGV4dD4KIDx0ZXh0IHg9IjExNS41IiB5PSIxNSIgZmlsbD0iIzAxMDEwMSIgZmlsbC1vcGFjaXR5PSIuMyI+CjEuMS43LjkwMDAwMDwvdGV4dD4KIDx0ZXh0IHg9IjExNS41IiB5PSIxNCI+CjEuMS43LjkwMDAwMDwvdGV4dD4KIDwvZz4KIDwvc3ZnPgo=">
</td>
</tr>
<tr>
<td>
Downloads from <a href='http://cran.rstudio.com/'>CRAN.RStudio</a>&nbsp;&nbsp;&nbsp;
</td>
<td>
<img src="http://cranlogs.r-pkg.org/badges/grand-total/wikipediatrend">
<img src="http://cranlogs.r-pkg.org/badges/wikipediatrend">
</td>
</tr>

</table>



# Meta ([cranlogs](https://github.com/metacran/cranlogs)) wikipediatrend

![](README_files/figure-html/unnamed-chunk-3-1.png) 




# Purpose

The wikipediatrend package is designed to make Wikipedia page access statistics data availible in R in a most convenient way. 

*Consequently the package provides* 

- daily page views as data frames 
- page views for user set time spans
- page views for multiple articles in one function call
- page views for articles in different language domains
- a function to check article titles in other country domains
- background caching of results to minimize function execution time as well as server burdens






# Installation 

A stable version of the package can be found on CRAN and installed via ...

```r
install.packages("wikipediatrend")
```

... while the current developement version can be retrieved by using `install_github()` from the devtools package ... 


```r
devtools::install_github("petermeissner/wikipediatrend")
```

After loading the package several functions are available.


```r
library(wikipediatrend)
```




# Usage


The workhorse of the package is the `wp_trend()` function:


```r
wp <- wp_trend(page = c("Fever","Fieber"), 
               from = "2013-08-01", 
               to   = prev_month_end(), 
               lang = c("en","de"))
```

```
## http://stats.grok.se/json/en/201308/Fever
## http://stats.grok.se/json/en/201309/Fever
## http://stats.grok.se/json/en/201310/Fever
## http://stats.grok.se/json/de/201311/Fieber
## http://stats.grok.se/json/de/201312/Fieber
## http://stats.grok.se/json/de/201401/Fieber
## http://stats.grok.se/json/de/201402/Fieber
```

```r
# (... messages shortened)
```



The function's return is a data frame with six variables *date*, *count*, *project*, *title*, *rank*, *month* paralleling the data provided by the stats.grok.se server:


```r
head(wp)
```

```
##   date       count lang page  rank month  title
## 1 2013-08-26 2993  en   Fever 5014 201308 Fever
## 2 2013-08-27 3153  en   Fever 5014 201308 Fever
## 3 2013-08-28 2984  en   Fever 5014 201308 Fever
## 4 2013-08-19 3229  en   Fever 5014 201308 Fever
## 5 2013-08-18 2700  en   Fever 5014 201308 Fever
## 6 2013-08-31 2441  en   Fever 5014 201308 Fever
```

![](README_files/figure-html/unnamed-chunk-9-1.png) 




# Vignette

*For a more detailed usage have a look at the vignette accompanying the package. `vignette("using-wikipediatrend", package="wikipediatrend")`*

... or GoTo [CRAN](http://cran.r-project.org/web/packages/wikipediatrend/index.html) or build it from scratch from [Github](https://raw.githubusercontent.com/petermeissner/wikipediatrend/master/vignettes/using-wikipediatrend.Rmd).



# Some examples for using page view statistics

- Munzert, Simon (2015): *Using Wikipedia Page View Statistics to Measure Issue Salience.* WEBDATANET CONFERENCE 2015. http://conference.webdatanet.eu/uploads/submission/full_paper/35/munzert-wikipedia-webdatanet.pdf

- Wilkerson, Bill (2015): *Post-Republican debate on Wikipedia follow-up: before and after public interest in the candidates.* http://www.wrwilkerson.com/ .
http://www.wrwilkerson.com/blog/2015/8/15/post-republican-debate-on-wikipedia-follow-up-before-and-after-public-interest-in-the-candidates

- Taha Yasseri and Jonathan Bright (2015): *Predicting elections from online information flows: towards theoretically informed models*. http://arxiv.org/abs/1505.01818

- Mellon, Jonathan (2014) *Internet Search Data and Issue Salience: The Properties of Google Trends as a Measure of Issue Salience* Journal of Elections, Public Opinion and Parties 24(1):45-72.
http://www.tandfonline.com/doi/abs/10.1080/17457289.2013.846346 

- Yla Tausczik, Kate Faasse, James W. Pennebaker, Keith J. Petrie (2012): *Public Anxiety and Information Seeking Following the H1N1 Outbreak: Blogs, Newspaper Articles, and Wikipedia Visits*. Health Communication, Vol. 27, Iss. 2.
 http://www.tandfonline.com/doi/pdf/10.1080/10410236.2011.571759

- Ripberger, Joseph T. (2011): *Capturing curiosity: using Internet search trends to measure public attentiveness*. Policy Studies Journal 39(2):239-259.
http://onlinelibrary.wiley.com/doi/10.1111/j.1541-0072.2011.00406.x/full





 
*(I missed your application? Make a pull request, open an issue, drop me a line and I put it here)*



# Thanks 

Fernando Reis, Eryk Walczak, Simon Munzert, Kristin Lindemann





# Credits

- Parts of the package's code have been shamelessly copied and modified from R base package written by R core team. This concerns the `wp_date()` generic and its methods and is detailed in the help files. 




