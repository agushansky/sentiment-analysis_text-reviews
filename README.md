# Consider changing repo name to NLP_sentiment_analysis?

### Using customer review data about theme parks to make informed strategic decisions

#### Problem Statement & Motivation

Theme parks are at the center of spur-of-the-moment excursions and vacations in the U.S. and around the world. Millions flock each year to try the newest bone-ratting roller-coaster, or reach new heights at near-supersonic speeds. Theme parks are a hallmark of adventure-seekers and adrenaline-junkies, and they collectively bring in billions of dollars yearly. Park owners and operators are constantly looking for new ways to quantify their customers' experiences in order to create more meaningful experiences and drive profits. 

With the recent rise of public review websites like TripAdvisor, a gold mine of data is available for processing. Sentiment analysis serves as a powerful framework to discover how customers *feel* about their experiences. Studies have consistently shown that customer sentiment correlates with key business metrics like retention and per-customer monetization. After all, it is that unmatched feeling that brings the masses back to their favorite theme parks. 

Along with the increase of available data, there are a host of machine learning models and methods that can analyze it. Advances allow analysis and data scientists to use Natural Language Processing (NLP) methods and techniques to quickly vectorize text reviews and predict nominal sentiment. This project uses some of those techniques to analyze over 50,000 reviews of three Universal Studios theme parks.

### Dataset

The dataset used was extracted from Kaggle and can be accessed via this [this](https://www.kaggle.com/dwiknrd/reviewuniversalstudio) link. There are 50,847 total reviews spanning three Universal Studios theme parks (one each in Florida (U.S.A.), Japan, and Singapore. There are six features (columns), summarized as below:

1.  "reviewer" - username of the reviewer on TripAdvisor
2.  "rating" - integer rating assigned by the reviewer, from '1' (unsatisfied) to '5' (satisfied)
3.  "written_date" - date stamp of the review
4.  "title" - title of the review
5.  "review_text" - text review logged by the visitor
6.  "branch" - theme park branch reviewed.

It is important to highlight that the dataset consists only of reviews that were originally submitted in English. This fact has large implications about the results of the analysis. Specifically, it means the model will be biased toward customer experiences of people who use English as their primary language. English-speakers often hold cultural norms and traits that are not shared by other cultures. Concretely, while English-speakers may have a positive impression of the available food at a park, it does not mean that others feel the same way!

### Exploratory Data Analysis (EDA)

A couple of findings from EDA are worth noting and are summarized in the plots below. The first is that the number of reviews assigned to each park is imbalanced. Reviews assigned to the Universal Studios park in Florida make up over half of the available data-- and outnumber reviews assigned to Japan by a factor of nearly six. This imbalance will need to be addressed prior to modeling; otherwise, results will be biased toward oversampled data. The second finding is that the ratings themselves are imbalanced. The overwhelming majority of reviews assigned are four- and five-star reviews. This will also need to be corrected.

![alt text](https://github.com/agushansky/sentiment_analysis/images/rating_dist.png?raw=true)

### Methodology

The dataset was preprocessed prior to getting fit. 

### Results


