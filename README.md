# url-classification

Objective: Accurate classification of phishing and malicious urls.

| Step|Description|File(s)|
|:----|:----------|:------|
|Proposal|Full Project Proposal|[report](https://github.com/hlplacid/url-classification/blob/main/URL%20Classification%20Project%20Proposal.pdf)|
|Data Wrangling|Data notebooks|[code](https://github.com/hlplacid/url-classification/tree/main/Data)|
|EDA & Data Stories|Notebook|[code](https://github.com/hlplacid/url-classification/blob/main/EDA%20and%20Data%20Stories.ipynb)|
|Inferential Statistics|Notebook|[code](https://github.com/hlplacid/url-classification/blob/main/Inferential%20Statistics.ipynb)|
|Machine Learning|Notebooks|[lexical-based](https://github.com/hlplacid/url-classification/blob/main/Machine%20Learning%20with%20Lexical%20Feature%20Set.ipynb), [td-idf-based](https://github.com/hlplacid/url-classification/blob/main/Machine%20Learning%20Using%20TF-IDF%20Scores.ipynb), [stacked](https://github.com/hlplacid/url-classification/blob/main/Machine%20Learning%20-%20Stacked%20Classifiers.ipynb)|
|Milestone Reports|Milestone Presentations and Reports|[reports](https://github.com/hlplacid/url-classification/tree/main/MilestoneReports)|
|Final Reporting|Report and Presentation|[report](https://github.com/hlplacid/url-classification/blob/main/FinalReports/Final%20Report.docx), [prez](https://github.com/hlplacid/url-classification/blob/main/FinalReports/Final%20Presentation.pptx)|

Executive Summary:

Malicious web content is leveraged by threat actors in phishing and malware attacks to achieve objectives such as credential harvesting, data exfiltration or destruction. Accurate classification of URLs is critical for the security of computing systems and networks.

This project’s goal was to develop a machine learning model that accurately classifies URLs related to a potential security incident. This is a multi-class classification problem, as we seek to accurately categorize URLs as benign, phishing or malicious. 

Incident investigations typically involve analysis of activity that has been permitted by security defenses. An important consideration for this project: What URL characteristics should we train and build our model with, to re-classify truly malicious URLs that had bypassed our security controls? After considering available information on URLs and their underlying web infrastructure, it was decided that the project would rely on lexical characteristics, and also explore natural language processing techniques. These characteristics are not leveraged by signature, behavior or rule-based security tools. Thus, we may more accurately classify URLs in a post-incident stage.

Since we are most interested in post-incident URL classification, recall scores for phishing and malicious URLs were designated as the most important scoring mechanism for our model. A 95% or higher recall score was considered a good threshold for adopting a model and placing it into production. 

The training data consisted of 30,000 unique URLs, with an equal balance from benign, phishing and malicious categories. Models were built using two unique feature sets. One lexical-based, the other leveraging natural language processing with TF-IDF vector representations of URL tokens (substrings).  Multiple algorithms were explored before final algorithms were selected for each model. The model trained on the TF-IDF feature set outperformed the lexical-based model, and also met our 95% threshold. Final results for each model follow:

Model 1. A Random Forest Classifier was trained on a lexical-based set of ninety-six predictor features. Overall accuracy score was .931. Recall scores: benign- .9727, phishing-.9055, and malicious-.9158.

Model 2. A Random Forest Classifier was trained on vectors consisting of URL string, token and TF-IDF scores. Overall accuracy score was .9625. Recall scores: benign-.9765, phishing-.9554, malicious-.955.
