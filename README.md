# url-classification

Objective:

Accurate classification of urls into one of three classes: benign, phishing or malicious.


Background:

Machine learning techniques are being applied to cyber security problems, and there are several machine learning models which analyze and classify urls. These studies utilized one or more of the following sources to develop data feature sets: Lexical properties of the url; host-based characteristics; url, domain and/or IP reputation; domain name registration and domain resolution information; connection speed between web client and server; url link popularity; underlying url resource code (assessment of web content such as links, tags, scripts).
 
 
Project Approach:

This url classification project relied entirely on url strings to train a machine learning model. This is a light-weight approach that does not require additional features which are limiting due to one or more of the following: 

•	Threat actors' infrastructure and TTPs (tactics, techniques and procedures) change over time.

•	Detonation infrastructure resources or subscriptions are valuable tools to analyze url web content, but anti-forensic measures may curtail proper analysis of malicious urls.  

•	There is inherent risk in connecting to malicious web links for analysis purposes.

•	Reputable websites with clean records are often compromised and leveraged to host malicious content. Features created from domain registration records or reputation lists may 
be useless in these cases. Blacklists alone are not a 100% reliable resource for url analysis and classification.

•	Information may be unavailable - e.g. urls may go offline, whois information may be incomplete.


Data:

Verified phishing and malicious urls were retrieved from PhishTank and the URLHAUS project from abuse.ch. Benign urls were collected by crawling Alexa's top 2500 websites. Each url's reputation was checked via VirusTotal's reputation service. Virus scans were initiated when necessary.


Feature Creation: 

Two sets of features were created, trained and tested. 

Feature Set 1: 
96 predictor features created based on lexical properties of a url and url segments (scheme, netloc, path, params query, fragment). Features were based on length, character types, presence of special characters, character continuity rate, entropy, masquing characteristics, etc.

Feature Set 2: 
URLs were separated into tokens for further processing (e.g. https, ://, www, ., google, ., com). 


Machine Learning:

Supervised learning algorithms capable of multi-class classification were explored.

Feature Set 2 achieved the best overal scores. Natural language processing techniques were applied to convert url tokens into vector representations. Term Frequency–Inverse Document Frequency (TF-IDF) was utilized to measure each token in comparison to the entire set of url tokens in the dataset. Using TF-IDF, less frequent tokens are considered more informative and important. TF-IDF encoding normalized the frequency of tokens with respect to the rest of the corpus (set of url tokens).
