#Email Spam Classifier — Using NLP


Introduction and Background

Natural Language Processing is a branch of Data Science that deals with human language. It deals with text data which in the form of strings. There are various applications of Natural Language Processing(NLP), as the amount of data is increasing day by day. Various applications of NLP are Sentiment analysis, Fake news classifier, Email Spam Classifier.
Sklearn provides us with a library called NLTK for processing the text data.

2. Email Spam Classifier
When you open up your mail, you would have noticed that there is a normal email that is inside INBOX but there is also a folder called a SPAM folder. How do some of the emails end up inside the SPAM folder? The answer is simple, an algorithm runs on the backend which captures words from a particular email, and then based on some processing it classifies whether the email is spam or not.

3. Steps to Build an Email Spam Classifier
Dataset Link:- https://archive.ics.uci.edu/ml/datasets/sms+spam+collection

a) Import all the necessary libraries and Load the Dataset
The dataset consists of 2 columns message and label, the message is the email message and the label tells whether the email is spam or not.

b) Preprocessing
Step1: Eliminating the symbols and punctuations from the text
Using Regular Expression library-‘re’ we can eliminate the punctuations and symbols as they don’t play a part in classifying whether an email is a spam or not.
Step2: Removing Stopwords and performing Lemmatization
After the punctuations and unnecessary symbols are removed the next step is removing stopwords. Stopwords are the words that don’t add much value to the given text. Words like “ I, we, you, shouldn't, etc.” are all stopwords. Stopwords can be present in multiple languages, but in this given problem we will eliminate stopwords that occur in English. This can be done using stopwords.words(‘english’). If a particular word is not a stopword then that particular word gets lemmatized. Lemmatization means reducing the words to meaningful words. For example history and historical will be converted and stored as history. What Lemmatization basically does is, it converts words to meaningful root words. Once all this is done, the trimmed text is then combined and stored.

c) More image preprocessing
The machine can understand numeric data only, so we need to convert our Label column from words to numeric data. This can be done using get_dummies, this will split the data into numeric columns based on the number of classifications. Example:- In this case, there are 2 label values spam and ham, so the get_dummies will convert this into 2 columns namely ham and spam, and the values in the respective column will be 1 if it was actually ham or spam, and 0 otherwise.
TfidVectorizer
TF-IDF = term frequency — inverse document frequency (gives semantic meaning to words). Bag of words treats all the words as having same importance but TF-IDF eliminates this and gives semantic meaning to words.
Term Frequency = (number of repetitions of words in sentence )/ (total number of words in sentence)
Eg- good boy => term frequency of good is ½ , term frequency of boy =1/2
good girl => term frequency of good is ½ , term frequency of girl =1/2
good boy girl => term frequency of good is 1/3 , term frequency of girl =1/3, term frequency boy=1/3
Inverse Document Frequency = log(number of sentences/number of sentences containing word)
Good — log(3/3)=0 , boy=log(3/2) , girl=log(3/2)
TF*IDF = vectors (the output is table again)

d) Building a model
Once all the preprocessing is done, the next step is building a model, this starts by preparing and splitting the data for training and testing. In our example, 80% of data is training and 20% of data is used for testing. The model which we will be using, in this case, will be Naive Bayes Classifier. As naive Bayes classifier works best with classification. Naive Bayes Classifier works on probability and on Bayes Theorem.
Bayes Theorem
Bayes Probability
Using Bayes theorem, we can find the probability of A happening, given that B has occurred. Here, B is the evidence and A is the hypothesis. The assumption made here is that the predictors/features are independent. That is the presence of one particular feature does not affect the other. Hence it is called naive.
Then the next step is fitting the training data to the model, once the data is fit, the data is predicted using test data. Then the output of the test data is compared with the actual test output data to find the accuracy.
Accuracy = (TP + TN)/All


4. Conclusion
Hence we have built an email spam classifier model that has an accuracy of 97%.

