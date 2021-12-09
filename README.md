# US favorability

## Abstract
Nations around the world with different cultures and traditions have economic and political relationships with each 
other. Pew Research Center, a nonpartisan American fact tank that does not take policy positions, provides information 
about how the world feels about the United States. However, the number of countries is limited to thirty-seven. Our 
proposed project investigates only the quotations over five years to learn how other nations see a specific country. 
The dataset contains quotes from sources who are perceived to be biased in many issue areas. Thus, we identify factors 
that create those biases and eliminate them from our dataset to achieve comparable outcomes to the Pew Research Center 
for those thirty-seven countries. Consequently, we will estimate the favorability of the rest of the world towards the 
United States.

## Research Questions
### A. Do politicians and nonpoliticians say the same thing?
Politicians are biased in many issue areas, as interest groups or politicians themselves benefit from policies that harm
the public. In other words, politicians' opinions are different from nonpoliticians' opinions. We will perform the 
sentiment analysis on these two separate datasets. Then we study and compare the results to understand how politicians' 
options differ from nonpoliticians.

### B. Do the media reflect the nation?
As a society, we employ many different media and spend considerable time with media. We rely on it as a news source and 
entertainment, and we often assume that what we consume is pretty reliable. However, this assumption could not be 
accurate, as the media might be biased and has the tendency to lean towards or against someone or something. In most 
countries, media bias is thought to either lean to the left or right, favoring liberal or conservative politics. In some
countries, media bias can ultimately reflect the ideals of the governing body; for example, in North Korea, the media 
bias essentially becomes propaganda. Thus, we analyze the quotes given by cable news television channels or newspapers 
such as CNN, Fox News, The New York Times, etc.

### C. How does the world see the United States with a new president?
Europeans' attitudes toward the United States have undergone a massive change during Donald Trump's presidency. They 
thought that the United States' political was broken, furthermore European countries could not trust the United States 
to defend them. They tend to invest in their own economy and defense and look to Germany rather than the United States. 
They preferred to stay neutral in a conflict between the United States and China or Russia. Most Europeans rejoiced at 
Joe Biden's victory in the November 2020 US presidential election. Many people may have hoped that his victory election 
would have changed that dynamic. Still, the question is whether they believe that Biden can help the United States make 
a comeback as the pre-eminent global leader and positively impact their countries. At first, we intended to study the 
period before and after Joe Biden's presidency. However, the period right after an election might be pretty different 
from the middle of a United States president's presidency because the discussion is more about hopes and fears 
associated with the new president than about what the president has done politically. Thus, we consider the years of 
2015-16 and 2019-20 where there is a transition from Barack Obama to Donald Trump to analyze the changes in people's 
opinion towards the United States.

### D. How does the United States see the rest of the world?
According to Pew Research Center in 2013, Americans don't like Middle Eastern countries, and they don't like the United 
States. But there was one notable difference. The British don't have nearly the same affection for the United States as 
Americans have for Great Britain. In our proposed project, we will also compare the sentiments of countries about each 
other, e.g., see whether country 'A' likes country 'B' more than country 'B' likes country 'A'. We evaluate how the 
United States feels about the world and how the world thinks about the United States.

## Proposed additional datasets
In this project, we employed two additional datasets named Pew Research Center and Wikidata. From Pew Research Center, 
we used the dataset of 2016-2020, which conducts public opinion polling over the phone to evaluate public attitudes 
toward the United States. However, their analysis does not include the vast majority of the countries.

We also considered Wikidata, which is a free database to provide support for Wikipedia. Wikidata enables us to access 
additional metadata such as nationality about the speakers in the Quotebank dataset. Thanks to Wikidata, we can enhance 
keyword selection, which is essential for our project. 


## Methods
### Countries quotes sentiment analysis
We considered the quoting bank from 2015 to 2020, which contains 18.702Go of data. We manually defined keywords "US," "U.S," 
"USA," and "United States," then extracted 253.1Mo of data that contained these keywords. We identified the speaker nationality
of these quotes and performed a sentiment analysis. Sentiment analysis is a text analysis that determines polarity 
within the text. Finally, we study the positiveness or negativeness of the quotes of all countries towards the United 
States. 
You can find our preliminary results in the attachment.

![alt text](results_world_map.png)

### Investigation in sentiment analysis algorithms
We evaluated the accuracy of the sentiment analysis algorithm by conducting a user survey where fifty 
quotes were selected randomly, and different Python libraries named NLTK, Flair, and TextBlob were applied. As we 
observe in the Table below, the Flair library results in better sentiment analysis accuracy.

| | NLTK | TextBlob | Flair | 
|-------|:-------:|-------|-------| 
|Accuracy| 54 % | 42 % | 66 % | 
|Time | 0.135[s] | 0.021[s] | 4.064[s] (without initialization)| 

### Keyword enrichment
To make our results of sentiment analysis more attractive and trustworthy, we will enrich the keywords. In our project, 
We extract all the American speakers using the "speaker_attributes.parquet" dataset, where we have the speaker and their 
nationality. Then, we filter the quotes that contain American names from 2015 to 2020.

### Estimate US favorability in unstudied countries using machine learning
## Organization within the team
| Research Questions | November | December |||
| :------------: | :-----------: | :-----------: | :-----------: | :-----------: |
| | Week 4 | Week 1 | Week 2 | Week 3 |
| A | Saleh | | | |
| B | | Alireza | | |
| C | | | Jonathan | |
| D | | | | Nicolas  |
| D | | | Nicolas | |
| Writing report | | | | All  |



# Potential skeleton to the data story

## Introduction and PEW dataset
In the PEW dataset, get an idea of how different countries appreciate the United States. However, there are not a lot of countries and many data is missing. It is still an interesting thing to look at and we want to see if we can achieve a similar stidy using the sentiment of quotes about the US in the Quotebank dataset. If so, we would like to see how this comapres to the PEW analysis. 

	- Pew heatmap

## What is the sentiment of speakers in the  quotebank dataset ? 

Looking at the raw sentiment analysis we can get an initial insight as to how the different countries feel about the United states

	- First sentiment world map

Albeit this is already an interesting result, it is still quite vague. Is this really truthul and without bias, and if so, it would be interesting to go deeper, and see what drives these feelings. 

## Are the media bringing a bias in the feeling. 

Most of the medias are USA based and nearly all are English speaking, so it is possible that some of them are more inclined to share positive or negative views on the USA. 

	- Distribution of the top 30 most recurring medias (violin and boxplot) 
	- P-values
	
Most seems to be similar so not that much bias, but some extreme values - look at how they are linked to the number of nationality speaker per media
So seems like media does not induce massive bias - that is good, but it does not explain the reason behind the varying sentiments. 

## Which subject brings out most positive quotes

	- What subjects sparks the most emotions 

By doing subject clustering on different subject, could be possible to get whether some subjects brings out more or less positivity. 

## Do politicians and nonpoliticians say the same thing?

That is good. One of the major subject when looking at international relation is politics, so would be nice to see how different it is in different countries between politicians and non-politicians

	- Politician non politician study 
  

## Trump era versus Obama era, have the feelings changed

Okay, the US politics has been marked by a sharp change recently from Obama to Trump. Could this be a strong driver of the sentiment of people towards the US. 


## Conclusion : What drives US favorability and how does this compares to the PEW data

