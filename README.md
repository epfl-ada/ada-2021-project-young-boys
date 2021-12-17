# How favourable are countries to the USA ? 

Data story : https://nicolaskirsch2000.github.io/young_boys_final_project/

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

### A. Can we extend the PEW results with the Quotebank data

### A. Do politicians and nonpoliticians say the same thing?
Politicians are biased in many issue areas, as interest groups or politicians themselves benefit from policies that harm
the public. In other words, politicians' opinions are different from nonpoliticians' opinions. We will perform the 
sentiment analysis on these two separate datasets. Then we study and compare the results to understand how politicians' 
options differ from nonpoliticians.

### B. How does the world see the United States with a new president?
Europeans' attitudes toward the United States have undergone a massive change during Donald Trump's presidency. 
At first, we intended to study the period before and after Joe Biden's presidency. However, the period right after an election might be pretty different 
from the middle of a United States president's presidency because the discussion is more about hopes and fears 
associated with the new president than about what the president has done politically. Thus, we consider the years of 
2015-16 and 2019-20 where there is a transition from Barack Obama to Donald Trump to analyze the changes in people's 
opinion towards the United States. 

This relative comparison of sentiment can also help us see how Quotebank data compares to PEW data, as raw sentiment scores cannot be compared directly between the two datasets. These relative values give insights on trends, which could be comparable instead.

### C. What are the main positive and negative topics per countries ? 
After gaining insights on the sentiments of the countries towards the USA, it is interesting to understand better what drives these feelings. There might be some common sources of positive or negative feelings, or maybe each country has their own reasons for feeling a specific way towards the USA. We therefore want to find what is the most common topic per country for the most positive and negative quotes, and see how this evolves throughout the years.


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

### Bias removal 
During our research, we have seen that the Quotebank data seemed to be biased and thus did not provide accurate sentiment scores. To investigate this, we pursued several analysis. We wanted to see whether the medias could increase the bias, by selecting only positive or negative quotes. This was adressed by looking at the mean score and distribution per media. The medias with independent distribution and too extreme means were eliminated, as overall, the sentiment per should have a somewhat uniform distribution centered close to 0.
Another possible bias source was the difference between politicians and non-politicians. This was adressed by comparing their relative scores to the PEW data, to see wether politicians shifted the sentiment scores compared to 'normal' citizens

A final potential bias source is the importance each speaker has. If a person with extreme views speaks a lot about them, it will have a strong impact on the population sentiment score, while maybe not representing it. This possible bias was adressed by making a unique entry per speaker, with a weighted sentiment score

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

### Main topic extraction 
To extract the main positive and negative topic per country, we will train an LDA model on the dataset, which will assign a topic to each quotes. After some tests, we have seen that creating 150 topics is what yields the most qualitative results. We will then divide the data on a sentiment thresholds (to get postive and negative). A group by by country and year finding the most common topics will be used. The topics will then be labeled manually to retrieve their actual meaning. 

## Organization within the team
| Task | November | December |||
| :------------: | :-----------: | :-----------: | :-----------: | :-----------: |
| | Week 4 | Week 1 | Week 2 | Week 3 |
| Keyword Enrichment | Saleh | | | |
|Topic retrieval | | Alireza | | |
| PEW comparative analysis | | Alireza and Saleh | | |
| Politicians vs Non-Politicians | | | Jonathan | |
| Speaker importance | | | Jonathan | |
| Medias bias | | | Nicolas |   |
| Interactive map | | |  | Nicolas |
| Writing report | | | | All  |
