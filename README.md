# url-classification

Objective: Accurate classification of phishing and malicious urls.

Background:

Malicious web content is leveraged by threat actors in phishing and malware attacks. This web content may assist an actor in achieving objectives such as credential harvesting, data exfiltration, or data destruction. Threat actors have utilized their own web-based infrastructure in phishing and malware attacks, but they also compromise legitimate, reputable websites to host their malicious content.

It is imperative to detect and block malicious urls effectively, and organizations utilize a host of preventive and defensive measures to block these and other threats. Machine learning techniques are being applied to cyber security problems, and there have been several studies which employ machine learning algorithms to classify urls. These studies have leveraged a variety of predictor features to train their models. This project differs, as it attempts to build a light-weight predictive model that leverages url strings as the basis for its feature set. Models are trained on two select feature sets, one based on url lexical features and another base on TF-IDF scores, a natural language processing scoring technique applied to url segments, or ‘tokens’. 

Machine Learning Results:

Supervised learning algorithms capable of multi-class classification were explored for both feature sets. 

While both approaches are at least 90% accurate in classifying urls, models trained with TF-IDF-based features achieve superior results. 

Feature Set 1 - Several algorithms were explored with the full feature set of 96 lexical predictors as well as a reduced feature set of 22 predictors. RandomForestClassifer achieved the best overal accuracy score of 92.28. A confusion matrix delivered the following true positive scores: Benign-96.66, Phishing-89.70, Malicious-92.00. Recall scores: Benign-97.27, Phishing-90.55, Malicious-91.58. 

Feature Set 2 achieved beter scores. Natural language processing techniques were applied to convert the url tokens into vector representations. Term Frequency–Inverse Document Frequency (TF-IDF) was utilized to measure each token in comparison to the entire set of url tokens in the dataset. Again, multiple algorithms were explored. LinearSVC achieved and Random Forest Classifier tied for the best overall accuracy score of 96.25. The Random Forest Classifier returned the best true positive rate (95.30) for detecting malicious urls with a recall rate of 95.55. LinearSVC returned the best true postive rate for benign (98.35) and phishing (96.49) urls. In the end, three base models were stacked: LinearSVC, Random Forest Classifier and Logistic Regression. A Logistic Regression meta-classifier was fitted using these base model predictions. Slight improvements in all scores were achieved.

| Step|Description|File(s)|
|:----|:----------|:------|
|Proposal|Full Project Proposal|[report](https://github.com/hlplacid/url-classification/blob/main/URL%20Classification%20Project%20Proposal.pdf)|
|Data Wrangling|Data notebooks|[code](https://github.com/hlplacid/url-classification/tree/main/Data)|
|EDA & Data Stories|Notebooks|[code](https://github.com/hlplacid/url-classification/blob/main/EDA%20and%20Data%20Stories.ipynb)|
|Inferential Statistics|Notebook|[code](https://github.com/hlplacid/url-classification/blob/main/Inferential%20Statistics.ipynb)|
|Machine Learning|Notebooks|[lexical-based](https://github.com/hlplacid/url-classification/blob/main/Machine%20Learning%20with%20Lexical%20Feature%20Set.ipynb), [td-idf-based](https://github.com/hlplacid/url-classification/blob/main/Machine%20Learning%20Using%20TF-IDF%20Scores.ipynb)|
|Milestone Reports|Milestone Presentations and Reports||
|Final Reporting|Report and Presentation||
