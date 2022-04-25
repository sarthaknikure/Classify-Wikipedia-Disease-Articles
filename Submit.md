# Classify Wikipedia Disease Articles

I have provided a sample of articles taken from Wikipedia. There are lots of different kinds of articles, and one flavor is those that describe a disease. The data are html dumps of wikipedia articles. I have given a labelled set of disease articles (positives), and non-diseases articles (negatives).


## Part 1

In part 1 I have to classify whether article is about disease or not. It is a binary classification problem.


## Tasks
* Extracting text out of html dump.
* Data Preprocessing.
* Model Selection.


### Extracting text out of html dump

[link to notebook](https://github.com/sarthaknikure/Classify-Wikipedia-Disease-Articles/blob/main/Dump_files_to_csv.ipynb)

I have used `beautifulsoup` library to parse html document and extract text from `<title></title>` and`<p></p>` tags, and Created few csv files. 


**Columns** `article, y`

* positive_data.csv (A CSV of all positive samples)
* negative_data.csv (A CSV of all negative samples)

I have concatenated the positive_data.csv and negative_data.csv files into single csv file `dataset.csv` before that I have shuffle and reset the index of dataset.



### Data Preprocessing and Model Selection

[link to notebook](https://github.com/sarthaknikure/Classify-Wikipedia-Disease-Articles/blob/main/Disease%20Classifier.ipynb)

For Data Preprocessing, I had followed below cleaning process: 

* Regex for removing numbers and symbols.
* String Lower
* Removal of Stopwords
* PorterStemmer for Stemming
* Get index values of words using one_hot and vec_size.
* Pad Sequencing (pre padding).



**Initial Idea** I have decided to go with Bidirectional LSTM model.

For Model creation, I had followed below process:
* Create Sequential() which is essential while creating model with tensorflow keras.
* Word Embedding Layer. 
* Bidirectional LSTM Layer.
* Last Layer is Dense Layer with sigmoid activation function.
* While compiling the model loss=’binary_crossentropy’, optimizer=’adamax’ and metrics=’accuracy’ is used.
* Train_test_split for creating train and test data.
* fitting the model.


#### Model Metrics

**Confusion Matrix**

| Negative | Positive |
| ------ | ------ |
| 3274 | 41 |
| 54 | 1177 | 

**Test Accuracy** 

Accuracy: 99.64% and Val Accuracy: 97.90


**Evaluation Metrics**

              precision    recall  f1-score   support

           0       0.98      0.99      0.99      3288
           1       0.97      0.96      0.96      1231

    accuracy        -        -         0.98      4519
   


## Part 2

[link to notebook](https://github.com/shkr/project-sim-ram-kumar/blob/master/DataExtraction.ipynb)


## Data Extraction from Disease Articles

The HTML dump is parsed using BeautifulSoup and Information like `disease_name`  `Symptoms`, `Treatment` or any other available information is captured.


Results are stored in ExtractedData.csv

### Headings captured

* Signs and symptoms
* Causes
* Diagnosis
* Treatment
* Prognosis
* Other First Level Table of Content headings



