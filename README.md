# Youtube-Analysis-Project
2nd most visited site in the world

## Project Overview
Explore sample Youtube datasets from across  10 countries and perform the following anaysis to generate insights that answer a given set of goals
- Analysis
  - Sentiment Analysis
  - Perform Wordcloud Analysis
  - Perform Emoji Analysis
- Project goals
  - Analyze most liked categories on Youtube
  - Analyze audience engagement
  - Analyze channels with most trending videos
  - Analyze the effect of puctuations in video titles on views

## Data Source
Youtube Data [Download here.](www.link.com)

## Tools 
- Python - Data cleaning
- SQL - Data Analysis
- PowerBI - Creating Reports

## Data Cleaning/Preparation
In the data cleaning and preparation phase, the following tasks were performed:
1. Data loading and inspection
2. Handling missing values and duplicates
3. Data cleaning and formating 

## Exploratory Analysis 
EDA involved exploration to answer and reveal the following:
1. What type of sentiments are expressed in comments? (using sentiment polarity analysis)
2. What are he most used words by users in video comments? (using wordcloud analysis)
3. What emoji's did users use most in their comments? (using emoji analysis)
4. Which content categories has the most likes?
5. Are audience engaged? (using regression and heatmap to find correlation between views and likes)
6. Which channels have the most trending videos? (using simple frequency and groupby techniques)
7. Does number of puctuations in video titles have impact on views? (using the string.punctuation package)

## Data Analysis
1. What type of sentiments are expressed in comments?
```
from textblob import TextBlob
polarity = []
for comment in sample_df['comment_text']:
    try:
        polarity.append(TextBlob(comment).sentiment.polarity)
    except:
        polarity.append(0)
sample_df['polarity'] = polarity
positivePol = sample_df['polarity'] == 1
negativePol = sample_df['polarity'] == -1
sample_df_pos_comments = sample_df[positivePol]
sample_df_neg_comments = sample_df[negativePol]
```

2. What are he most used words by users in video comments?
```
from wordcloud import WordCloud, STOPWORDS
PositiveCommentsStr = ' '.join(sample_df_pos_comments['comment_text'])
PosWordCloud = WordCloud(stopwords=set(STOPWORDS)).generate(PositiveCommentsStr)
plt.imshow(PosWordCloud)
plt.axis('off')
```

## Results/Findings


