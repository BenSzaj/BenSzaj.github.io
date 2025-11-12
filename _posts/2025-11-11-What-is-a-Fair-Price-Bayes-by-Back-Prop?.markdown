---
layout: post
title:  "What is a 'Fair Price' (Bayes by Back Prop)?"
date:   2025-11-11 12:03:37 -0500
categories: jekyll update
---
![Portfolio Composition]({{ site.url }}/Figures/BayesByBackProp/PortfolioComposition.png)

{% highlight ruby %}
Features = ['Log RoE', 'Daily Fed Funds', '1 - year treasury', <br>
'2 - year treasury', '3 - year treasury', \
'5 - year treasury', '7 - year treasury', '10 - year treasury',  
'20 - year treasury', '30 - year treasury', '30 - year mortgage', '15 - year mortgage', 'Junk - Treasury Spread','AAA Corporate Index', 'BBB Corporate Index',  'CCC Corporate Index','5 - year TIPS', '7 - year TIPS', '10 - year TIPS', '20 - year TIPS','30 - year TIPS', 'Emerging Markets Corporate Index', 'Emerging Markets Junk Index', 'Asia Emerging Markets Corporate Index', 'Car Loan Index', '1 - year corporate', '3 - year corporate', '5 - year corporate',  '7 - year corporate', '10 - year corporate', '15 - year corporate', 'Personal Loan Index', 'Delinquency Rates: All Loans', 'Delinquency Rates: Consumer Loans', 'Delinquency Rates: Loans Secured by Real Estate', 'Delinquency Rates: Commerical Real Estate', 'Delinquency Rates: Credit Card Loans', 'Delinquency Rates: Residential Mortgages', 'Delinquency Rates: Lease Financing Receivables', 'Delinqueny Rates: Business Loans', '1 - Year Expected Inflation', '2 - Year Expected Inflation', '3 - Year Expected Inflation', '5 - Year Expected Inflation', '1 - Year Real Interest Rate', '1 - Month Real Interest Rate',  'Federal Debt to GDP', 'Federal Deficit to GDP', 'Population Growth', 'Real GDP Rate', 'Unemployment Rate',  'UMich Inflation Expectation', 'Personal Savings Rate', 'Annualized CPI', 'Annualized PCE', 'Annualized Core PCE', 'Annualized M1 Money Supply', 'Annualized M2 Money Supply', 'Annualized M3 Money Supply', 'Annualized Hourly Earnings', 'EG5']
{% endhighlight %}

{% highlight ruby %}
Target = ['Log P/B']
{% endhighlight %}

![Histogram Of Data]({{ site.url }}/Figures/BayesByBackProp/HistogramOfData.png)

![Feature Importance]({{ site.url }}/Figures/BayesByBackProp/FeatureImportance.png)


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

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
