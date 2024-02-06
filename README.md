# Youtube-Analysis-Project
2nd most visited site in the world

## Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)

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

![wordcloud_likes](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/2dc5445f-de88-43db-9fd6-7de2807f207b)
![punctuation_count_and_views](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/86829c5c-3477-474b-8d97-a6884a4d4fe7)
![highest_trending](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/08250587-f406-4aee-96d9-5e94dd12a5af)
![emoji_analysis](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/327ecca8-9425-4bae-b5cc-3bccccb045ff)
![category_most_liked](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/740cb08e-9531-4ce7-acb0-bc2af162c911)
![audience_engagement](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/ca8dbc58-c163-4cac-bcd8-0e2b434d6d80)

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
1. What type of sentiments are expressed in comments? (using sentiment polarity analysis)
2. What are he most used words by users in video comments? (using wordcloud analysis)
3. What emoji's did users use most in their comments? (using emoji analysis)
4. Which content categories has the most likes?
5. Are audience engaged? (using regression and heatmap to find correlation between views and likes)
   - 
7. Which channels have the most trending videos? (using simple frequency and groupby techniques)
   - Conclusion:
     - The top 5 channels with trending videos
     - The Late Show with Stephen Colbert 989
WWE 808
Late Night with Seth Meyers 778
VikatanTV 768
TheEllenShow 747
8. Does number of puctuations in video titles have impact on views?
   - Conclusion:
     - Likes are higher for titles with 2, 3 and 5 punctuation marks
     - Views are higher for titles with 2 or 3 punctuation marks

## Recommendations

## Limitations
- 7 lines were skipped during the data extratction process due to inconsistent number of columns
- 26 null value were found and removed from the dataset of 691399 rows during data cleaning

## References 
1. Internet references
   - [Stack Overflow](somelink.com)
2. Book reference
   - Real-life projects using python
