# YouTube-Analysis-Project
YouTube - 2nd most visited site in the world
Real world analysis of YouTube data across 10 countries including the United States (US).

### Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Results and Findings](#results-and-findings)
- [Exploratory Analysis](#exploratory-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

## Project Overview
Explore sample Youtube datasets from across 10 countries and perform the following anaysis to generate insights that answer a given set of goals
- Analysis types:
  - Perform Sentiment Analysis
  - Perform Wordcloud Analysis
  - Perform Emoji Analysis
- Project goals
  - Analyze most liked categories on Youtube
  - Analyze audience engagement
  - Analyze channels with most trending videos
  - Analyze the effect of puctuations in video titles on views

![wordcloud_likes](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/2dc5445f-de88-43db-9fd6-7de2807f207b)
![highest_trending](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/08250587-f406-4aee-96d9-5e94dd12a5af)
![category_most_liked](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/740cb08e-9531-4ce7-acb0-bc2af162c911)
![punctuation_count_and_views](https://github.com/AbuTaoheed/Youtube-Analysis/assets/159118239/86829c5c-3477-474b-8d97-a6884a4d4fe7)

## Data Source
Project Datasets [Download here.](https://drive.google.com/drive/folders/1makDwgfKzmqOSikEnOLkmMskT3609dAo?usp=share_link)

## Tools 
- Python (Jupyter IDE)
  - Data cleaning
  - Data Analysis
  - Data visualization
- Special Packages used
  - Textblob(Sentiment.polarity)
  - Wordcloud
  - String.punctuations
  - Emoji

## Data Cleaning and Preparation
In the data cleaning and preparation phase, the following tasks were performed:
1. Data loading and inspection
2. Handling missing values and duplicates
3. Data formating and transformation

## Exploratory Analysis 
EDA involved exploration to answer and reveal the following:
1. What type of sentiments are expressed in comments? (using sentiment polarity analysis)
2. What are the most used words by users in video comments? (using wordcloud analysis)
3. What emoji's did users use most in their comments? (using emoji analysis)
4. Which content categories has the most likes?
5. Are audience engaged? (using regression and heatmap to find correlation between views and likes)
6. Which channels have the most trending videos? (using simple frequency and groupby techniques)
7. Does number of puctuations in video titles have impact on views? (using the string.punctuation package)

## Data Analysis
1. Analyzing sentiments expressed in comments?
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

2. Analyzing words most used by users in video comments?
```
from wordcloud import WordCloud, STOPWORDS
PositiveCommentsStr = ' '.join(sample_df_pos_comments['comment_text'])
PosWordCloud = WordCloud(stopwords=set(STOPWORDS)).generate(PositiveCommentsStr)
plt.imshow(PosWordCloud)
plt.axis('off')
```

## Results and Findings
1. Sentiments expressed in comments.
   - 10% of comments expressed positive sentiments whike 3% expressed negative comments. Over 85% of the comments were neutral.
2. Most important words used in comments.
   - Words like 'Best', 'Awesome' and 'Great' were most positive words used while words such as 'Terrible', 'Worst' and 'Boring' were the most negative words used in the comments
3. Emoji most used in the comments.
   - The following emojis were the top 3 used in comments 🤣 😆 😄
4. Content categories with the most likes and engagement.
   - The Music and Entertainment categories had the most likes followed by Sports and People\Lifestyle categories. The Trailers and Movies category had the least likes.
5. Channels having the most trending videos.
   - The top 5 channels with most trending videos are as follows:
       
|Channel|No. Trending videos|
|-------|-------------------|
|The Late Show with Stephen Colbert|710|
|WWE|643|
|Late Night with Seth Meyers|592|
|TheEllenShow|555|
|Jimmy Kimmel Live|528|

6. Impact of number of puctuations in video title.
   - Likes and views are higher for titles with 2, 3 and 5 punctuation marks.

## Recommendations

## Limitations
- 7 lines were skipped during the data extratction process due to inconsistent number of columns
- 26 null value were found and removed from the dataset of 691399 rows during data cleaning

## References 
1. Internet references
   - [Stack Overflow](somelink.com)
2. Book reference
   - Real-life projects using python

🍎

:Emoji_name

**Bold**

*Italic*
