# url-classification

Objective:

Accurate classification of urls into one of three classes: benign, phishing or malicious.


Background:

Machine learning techniques are being applied to cyber security problems and there are several published studies using machine learning models to analyze and classify urls. These studies utilize one or more of the following sources to develop data feature sets: Lexical properties of the url; host-based characteristics; url, domain and/or IP reputation; domain name registration and domain resolution information; connection speed between web client and server; url link popularity; underlying url resource code (assessment of web content such as links, tags, scripts).
 
 
Project Approach:

This url classification project relies entirely on url strings and their properties to train a machine learning model. This is a light-weight approach that does not require additional features (built using url reputation, url infrastructure characteristics, or a url's underlying code) which are limiting due to one or more of the following: 

•	Threat actors' infrastructure and TTPs (tactics, techniques and procedures) change over time.

•	Detonation infrastructure resources or subscriptions are valuable tools to analyze url web content, but anti-forensic measures may curtail proper analysis of malicious urls.  

•	There is inherent risk in connecting to malicious web links for analysis purposes.

•	Reputable websites with clean records are often compromised and leveraged to host malicious content. Features created from domain registration records or reputation lists may 
be useless in these cases. Blacklists alone are not a 100% reliable resource for url analysis and classification.

•	Information may be unavailable - e.g. urls may go offline, whois information may be incomplete, brand new url or domain with no reputation data.


Data:

Verified phishing and malicious urls were retrieved from PhishTank and the URLHAUS project from abuse.ch. Benign urls were collected by crawling Alexa's top 2500 websites. Each 'benign' url's reputation was checked via VirusTotal's reputation service. Virus scans were initiated when necessary.


Feature Creation: 

Two sets of features were created, trained and tested. 

Feature Set 1: 
96 predictor features created based on lexical properties of a url and url segments (scheme, netloc, path, params query, fragment). For example, features were based on length, character types, presence of special characters, character continuity rate, entropy, masquing characteristics, etc.

Feature Set 2: 
URLs were separated into tokens to enable natural language processing (NLP). For example, https://www.google.com is tokenized into [https, ://, www, ., google, ., com].


Machine Learning:

Supervised learning algorithms capable of multi-class classification were explored for both feature sets. 

Final Models and Analysis:
Feature Set 1 - Several algorithms were explored with the full feature set of 96 predictors as well as a reduced feature set of 22 predictors. RandomForestClassifer achieved the best overal accuracy score of 92.93. A confusion matrix delivered the following True Positive scores: Benign - 97.39, Phishing - 91.33, Malicious - 90.12.
Feature Set 2 achieved beter scores. Natural language processing techniques were applied to convert the url tokens into vector representations. Term Frequency–Inverse Document Frequency (TF-IDF) was utilized to measure each token in comparison to the entire set of url tokens in the dataset. Again, multiple algorithms were explored. LinearSVC achieved the best overall accuracy score of 96.25, however RanfomForestClassifier returned the best true positive rate (95.30) for detecting malicious urls. In the end, three base models utilizing LinearSVC, Random Forest Classifier and Logistic Regression were stacked. A Logistic Regression meta-classifier was fitted using these base model predictions. The final accuracy score was 96.37. Confusion Matrix true positive rates: Benign-98.10, Phishing-96.94, Malicious-94.06.


