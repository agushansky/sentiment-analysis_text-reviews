## Using Customer Reviews to Make Informed Strategic Decisions About Theme Parks

### Problem Statement & Motivation

Theme parks draw millions of visitors each year around the world. They are a hallmark of adventure-seekers and adrenaline-junkies, who flock to the newest bone-rattling roller coaster and revel at near-supersonic speeds. Park owners and operators are constantly evaluating ways to grow their brand and compete for their customers' hard-earned dollars. 

With the recent advancement of public-review websites like TripAdvisor, a treasure trove of new data has become available for analysts. Sentiment analysis serves as a powerful framework with which to analyze review data. It helps decision-makers understand how customers *feel* about their experiences. Research has consistently shown that customer sentiment correlates with key business metrics, including retention and monetization. After all, it is that unmatched feeling -- that thrill -- that brings the masses back to their favorite theme parks year-after-year.

### Dataset

The dataset used was extracted from Kaggle and can be accessed via this [this](https://www.kaggle.com/dwiknrd/reviewuniversalstudio) link. There are 50,847 total reviews that span three Universal Studios theme parks (one each in Florida, Japan, and Singapore. There are six columns, which can be summarized as follows:

1.  "reviewer" - username of the reviewer on TripAdvisor
2.  "rating" - integer rating assigned by the reviewer, from '1' (unsatisfied) to '5' (satisfied)
3.  "written_date" - date stamp of the review
4.  "title" - title of the review
5.  "review_text" - text review logged by the visitor
6.  "branch" - theme park that was reviewed

It is also important to note that this dataset is comprised of only reviews that were originally submitted in English. This fact has substantial implications on the conclusions that can be drawn from this analysis. Specifically, results will be biased toward sentiments that are shared by individuals whose primary language is English. To provide a concrete example of potential consequences, while English-speakers might positively rate food at a park, it certainly does not mean that others will feel the same way!

### Exploratory Data Analysis (EDA)

A couple of findings from EDA are worth highlighting. Firstly, the number of reviews assigned to each park is majorly imbalanced. Reviews assigned to the Universal Studios park in Florida make up over half of all available reviews -- and they outnumber reviews assigned to Japan by a factor of nearly six! This imbalance needs to be addressed prior to modeling when comparing reviews between parks; otherwise, the results will be biased toward oversampled data. The second finding is that the distribution of star-ratings is imbalanced. Four- and five-star ratings make up the overwhelming majority of all reviews. This will also need to be accounted for, specifically when doing sentiment analysis.

![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/rating_dist.png?raw=true)
![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/park_dist.png?raw=true)

### Methodology

There are a host of available machine-learning classifiers that are appropriate to perform sentiment analysis on this data. I focus on two-- Support Vector Machine (SVM) and Logistic Regression. Each method provides a linear classifier that can work well on sparse data, as is the case here. 

Prior to fitting these classifiers, there are a few preprocessing steps of note. The resulting models are designed to predict binary sentiment (i.e. positive or negative) on text reviews. To this end, three-star reviews were removed for the purpose of the analysis. Punctuation was also stripped to prepare the text to be converted into a matrix of token counts. Finally, the data was split with a train-to-test ratio of 4-to-1 prior to modeling. Classes were re-weighted prior to fitting the classifier to account for imbalanced sampling, as described above. 

### Results

Classification reports using two classifiers -- Support Vector Machine (SVM) and Logistic Regression -- are shown below. Overall accuracy on the test data was about 90% for both classifiers. The close performance makes sense, since both classifiers are linear and parametric. The different objective functions results in slightly different results. For both models, the f-1 score was substantially better for positive reviews than negative ones. 

SVM results:  
![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/svm_results.jpg?raw=true)

LogReg results:  
![alt text](https://github.com/agushansky/sentiment_analysis/blob/main/images/logistic_reg_results.jpg?raw=true)

While sentiment prediction has its limitations, it also has some interesting use-cases. Such models can predict sentiment from many forms of input text, including those of suggestion boxes. They can also efficiently extract information from reviews that might otherwise be neglected (e.g., "neutral" or three-star reviews). Finally, customer sentiment can be used alongside star ratings to predict important outcomes, like whether customers are expected to return to a park or how much money they might spend per visit.
