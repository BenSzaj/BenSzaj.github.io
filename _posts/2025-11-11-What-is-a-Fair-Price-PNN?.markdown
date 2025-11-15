---
layout: post
title:  "What is a 'Fair Price' (Part I. Probabilistic Neural Network)?"
date:   2025-11-11 12:03:37 -0500
categories: [Probabilistic Neural Network]
---
In the world of A.I. fueled growth, stocks are expensive. Various measures such as price-to-earnings ratio, price-to-book ratio, and the Cyclically adjusted price-to-earnings ratio (CAPE) are all approaching Dot-com levels of the late 90's. Examples of high price-to-earnings and price-to-book ratios for the total US stock market can be seen in the `Portfolio Composition` tab found on Vanguard and shown below. Despite these high valuations, the stock bulls claim that high prices are justified by higher expected growth of high quality companies, and **`this time is is different`**. Is it really? Are they right? Or otherwise are stocks over-priced and are we in for another lost decade (e.g. 2000 - 2010)?


![Portfolio Composition]({{ site.url }}/Figures/BayesByBackProp/PortfolioComposition.png)

In the interest of this blog, the aim is to use the `Portfolio Composition` data (as shown above) in conjunction with various rates and macroeconomic variables available through the Federal Reserve Bank of St. Louis ([FRED][FRED]) to answer this exact question. More concisely, I would like to estimate a probability distribution for a `Fair Value` for the `P/B ratio` given the 62 variables listed below. I have excluded variables that depend on price of stocks such as dividend yield and price-to-earnings ratio since these would create a data leak with the `target` variable. In addition, I have log scaled `Return on Equity`, and `P/B ratio` and additionally abbreviated earnings growth to `EG5.' 

{% highlight ruby %}
Features = ['Log RoE', 'Daily Fed Funds', '1 - year treasury',
            '2 - year treasury', '3 - year treasury', '5 - year treasury', 
            '7 - year treasury', '10 - year treasury', '20 - year treasury', 
            '30 - year treasury', '30 - year mortgage', '15 - year mortgage', 
            'Junk - Treasury Spread','AAA Corporate Index', 
            'BBB Corporate Index',  'CCC Corporate Index','5 - year TIPS', 
            '7 - year TIPS', '10 - year TIPS', '20 - year TIPS','30 - year TIPS', 
            'Emerging Markets Corporate Index', 'Emerging Markets Junk Index', 
            'Asia Emerging Markets Corporate Index', 'Car Loan Index', 
            '1 - year corporate', '3 - year corporate', '5 - year corporate',  
            '7 - year corporate', '10 - year corporate', '15 - year corporate', 
            'Personal Loan Index', 'Delinquency Rates: All Loans', 
            'Delinquency Rates: Consumer Loans', 
            'Delinquency Rates: Loans Secured by Real Estate', 
            'Delinquency Rates: Commerical Real Estate', 
            'Delinquency Rates: Credit Card Loans', 
            'Delinquency Rates: Residential Mortgages', 
            'Delinquency Rates: Lease Financing Receivables', 
            'Delinqueny Rates: Business Loans', '1 - Year Expected Inflation', 
            '2 - Year Expected Inflation', '3 - Year Expected Inflation', 
            '5 - Year Expected Inflation', '1 - Year Real Interest Rate', 
            '1 - Month Real Interest Rate',  
            'Federal Debt to GDP', 'Federal Deficit to GDP', 'Population Growth', 
            'Real GDP Rate', 'Unemployment Rate',  'UMich Inflation Expectation', 
            'Personal Savings Rate', 'Annualized CPI', 'Annualized PCE', 
            'Annualized Core PCE', 'Annualized M1 Money Supply', 
            'Annualized M2 Money Supply', 'Annualized M3 Money Supply', 
            'Annualized Hourly Earnings', 'EG5']
{% endhighlight %}

Where available, I have tabulated the above data collected on a daily basis for ~100 ETF index funds representing most of the Vanguard passive lineup. In total, there are 71395 observations each with 62 features. The temporal distribution of the data is shown below. I partition pre-2025 data into `Training` shown in blue and post-2025 data into `Testing` shown in red, corresponding to a ~71/29 split. Additionally, all data is standard scaled to a zero-mean and unit standard deviation, i.e.

```Z = \frac{X-\mu}{\sigma}```
 
![Histogram Of Data]({{ site.url }}/Figures/BayesByBackProp/HistogramOfData.png)

![Feature Importance]({{ site.url }}/Figures/BayesByBackProp/FeatureImportance.png)

![Loss Curves]({{ site.url }}/Figures/BayesByBackProp/LossCurvesExample.png)

![Parity Plot]({{ site.url }}/Figures/BayesByBackProp/ParityPlot.png)

![Predictions Data]({{ site.url }}/Figures/BayesByBackProp/Predictions_Data.png)

![Predictions Results Vanguard]({{ site.url }}/Figures/BayesByBackProp/Predictions_Results_Vanguard.png)

![Predictions BarChart Vanguard]({{ site.url }}/Figures/BayesByBackProp/Predictions_BarChart_Vanguard.png)


You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[FRED]: https://fred.stlouisfed.org/
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
