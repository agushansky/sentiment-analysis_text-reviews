## Using Customer Reviews to Make Informed Strategic Decisions

### Problem Statement & Motivation

Theme parks are a hallmark of adventure-seekers and adrenaline-junkies alike. Millions of annual visitors from around the world flock to the newest bone-rattling roller coaster and revel at near-supersonic speeds. On the business side of things, owners and operators are constantly evaluating ways to improve the overall experience and earn their customers' hard-earned dollars. 

With the recent ascent of public-review websites like TripAdvisor, a treasure trove of new data has become available for analysts. Sentiment analysis serves as a powerful framework with which to analyze reviews. It helps decision-makers understand how customers *feel* about their experiences. Research has consistently shown that customer sentiment correlates with key business metrics, including retention and monetization. After all, it is that unmatched feeling -- that thrill -- that brings people back to their favorite theme parks year-after-year.

### Dataset

The dataset used was extracted from Kaggle and can be accessed via this [this](https://www.kaggle.com/dwiknrd/reviewuniversalstudio) link. There are 50,847 total reviews that span three Universal Studios theme parks (one each in Florida, Japan, and Singapore). The six features can be summarized as follows:

1.  "reviewer" - username of the reviewer on TripAdvisor
2.  "rating" - integer rating assigned by the reviewer, from '1' (unsatisfied) to '5' (satisfied)
3.  "written_date" - date stamp of the review
4.  "title" - title of the review
5.  "review_text" - text review logged by the visitor
6.  "branch" - theme park that was reviewed

It is important to note that this dataset is comprised of only reviews that were originally submitted in English. This fact has substantial implications on the conclusions that can be drawn from the resulting analysis. Specifically, results will be biased toward sentiments that are shared by individuals whose primary language is English. To provide a concrete example, while English-speakers might collectively rate the food highly at a park, it certainly does not mean that others will do the same!

### Exploratory Data Analysis (EDA)

A couple of findings from EDA are worth highlighting and are visualized below. Firstly, the number of reviews assigned to each park is majorly imbalanced. Reviews attributed to the Universal Studios park in Florida make up over half of all available reviews -- and they outnumber reviews assigned to Japan by a factor of nearly six! This imbalance needs to be addressed prior to modeling to compare reviews between parks; otherwise, the results will be biased toward oversampled data. The second finding is that the distribution of star-ratings is imbalanced. Four- and five-star ratings make up the overwhelming majority of all reviews. This will also need to be accounted for, specifically when performing sentiment analysis.

![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/rating_dist.png?raw=true)
![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/park_dist.png?raw=true)

### Methodology

There are a host of available machine-learning classifiers that are appropriate to perform sentiment analysis on this data. I focus on two-- Support Vector Machine (SVM) and Logistic Regression. Each method provides a linear classifier that can work well on sparse data.

Prior to fitting the classifiers, there are a few preprocessing steps to note. The resulting models are designed to predict binary sentiment (i.e. positive or negative) on text reviews. To this end, three-star reviews (i.e. neutral reviews) are removed. Punctuation is also stripped to prepare the text to be converted into a matrix of token counts. The resulting matrix takes into account unigrams and bigrams, which refer to single words and two-word phrases, respectively. Higher-fidelity models often use higher-order n-grams, but unigrams and bigrams are sufficient for the purpose of this analysis (especially to preserve computational efficiency). Finally, the data is split with a train-to-test ratio of 4-to-1. Classes are re-weighted prior to fitting the classifier to account for imbalanced sampling, as described above. 

### Results & Discussion

The resulting classification reports are shown below. Accuracy on the test data quite is high for both classifiers -- near 90%. Interestingly, the F1 score is substantially better for positive reviews compared to negative ones. At a high level, negative language can be more difficult to decipher systematically, especially when only taking into account unigrams and bigrams, as I did for this analysis.

SVM results:  

![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/svm_results.jpg?raw=true)

Logistic Regression results:  

![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/logistic_reg_results.jpg?raw=true)

Models like these can be used to predict sentiment from many forms of input text, including suggestion boxes and online reviews that don't specify the park branch. They can also be used to extract important information from reviews that might otherwise be ignored (e.g. from "neutral" or three-star reviews) by humans. Customer sentiment can be used in conjunctino with star-ratings to predict important outcomes, like customer retention and monetization. Ultimately, while sentiment-prediction models are just one piece of the analytics puzzle, decision-makers would be wise to use them to help make informed decisions.
