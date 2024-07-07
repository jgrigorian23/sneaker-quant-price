# Instructions for the data team

## Emmanuel
We have 2 tasks for you that involve building on and formatting the dataset. 

1. With the way it's set up, right now if you look up a shoe on ebay, you might get thousands of results. Ebay can't store all of these results at once, so they break it up into different pages. The problem with this though is that for our jupyter notebook, when we save the webpage as an html file, we're only really saving that first page and so we're missing the rest of the pages that have the results. The first task is to add a block of code/script to the ebay.ipynb that will automatically save each page of the ebay search result, upload them to the jupyter notebook, and add it to the csv file. This way, we won't have to manually go through each page, save it, upload it, and add it to the csv file, as your code will automate that.

To do this, you'll probably need to use BeautifulSoup. The code in the jupyter notebook already uses it, so you can use that as an example, but here's also this: [Beautiful Soup docs](https://beautiful-soup-4.readthedocs.io/en/latest/)

2. So far all that's in the csv file is just the data we scraped from ebay search results, so it's a little unpolished. The second task is to edit the columns, so that the model team can work with them a little bit easier. Specifically, it would be nice if you could do the following
* On the sold date column, remove the "Sold" from every entry, we just want the date. Furthermore, instead of "Apr" or "Mar", see if you can turn these into numbers like 4 or 3 so that we're working with strictly numbers
* A lot of the shoe titles have a size in their title. See if you can extract the size from each shoe's title and add it as a separate column for each shoe.
* The brand section also unwantedly records the condition of each shoe. See if you can remove the condition from the brand section so that it's strictly just the brand for each shoe
* For the price section, remove the dollar sign so it's strictly a number
* For the bid section, remove the word "bids" from every entry that has one, so that it's just numbers
* For the shipping section, remove the "+$" and "shipping" from every entry so that it's strictly just shipping.

To do this, you'll be wrangling with panda dataframes. You'll use these a lot in csci360 and ML in general, so hopefully this will be a good learning experience. Here's a [cheatsheet](https://www.educative.io/blog/pandas-cheat-sheet) and the [documentation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)

## Emma
We want you to perform sentiment analysis so we have a better picture of volatility.

For whatever shoe we search and add to the jupyter notebook, it will have a sold date. The task is to go to twitter and, using their API, search twitter for that shoe on that day. Record how many hits/tweets that came up as a number on the csv file next to that shoe. This will give us important information about how popular/hype/volatile that shoe was when it got sold, so that we can better understand how to price it.

## Jake

We want you to measure performance so we can keep track of it as an indicator. A starting point could be that we rate performance from a scale of -1 to 1 where anything positive would be performing better than expected and anything negative would be performing worse than expected (if you can find a better way then go for it, this was just the first idea that came to mind). For the NBA players that have a shoe deal, we want you to find any data you can about how their performance was projected for the season, and then any data on how they actually peroformed. 

There's different ways you could go about doing this. One way is by taking the +/- for each game for a player and averaging it over their whole career. Another way could be to look at the pts/reb/ast from season to season and see if they're trending up or down (are they a player who's reaching their prime or are they starting to get old?). Another way could be to even take a look at fantasy basketball to look for projections and then comparing those to what they actually scored/did. Whichever way makes the most sense to you, we trust you, just be able to explain your thought process.

Depending on how you decided to measure their performance, you might need to use this formula for relative error in order to scale your result to $[-1,1]$ : $|\frac{\textnormal{expected - actual}}{\textnormal{actual}}|$. Don't worry too much about integrating this with the jupyter notebook. It's ok if you have a separate python file or whatever that does this.
