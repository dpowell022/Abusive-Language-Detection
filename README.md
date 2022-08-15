# Abusive-Language-Detection

Full notebook available [here](https://github.com/dpowell022/Abusive-Language-Detection/blob/main/Capstone_Detect_HateSpeech.ipynb)

Detailed project report available [here](https://github.com/dpowell022/Abusive-Language-Detection/blob/main/Capstone2_Project_Report.docx)

High-level presentation [here](https://github.com/dpowell022/Abusive-Language-Detection/commit/3fe422ad035dcadb36bc8433007e1e0084ae137b)

***
### Business problem
***
As the world of digital media continues to grow and permeate every part of our life, certain aspects of communication remain the same. We should seek to communicate with strangers, colleagues, associates, and generally most others in a manner which is courteous, professional, inviting, and effective. 

Effective communication leads to human interest and engagement. Conversely, ineffective, rude, off putting, or abusive language has the opposite effect. It tends to deter human interest and engagement. If a business featuring an online communication platform is to be successful, effective communication is what they want to encourage. It then becomes obvious that there is a growing need for companies to be able to effectively (and efficiently) moderate the communication of those using the platform; to restrict abusive communication, and limit or eliminate other forms of ineffective communication. 

The goal of this project is to develop a machine learning model which has been trained to detect and report on abusive communications in digital text.

***
### Acquiring and cleaning the data
***
 - 135,000 curated dataset of Twitter tweets with key features for user tweet text and an abusive score
 - Cleaned text field, removing special characters and stop words and lowercasing
 - Dropped features deemed irrelevant for model training
 - Checked for missing values, found none

***
### Feature engineering and Pre-processing
***
 - Created a new binary feature indicating Abusive (1) or not (0) based on the Abusive score feature, and then dropped that Abusive score feature
 - Ran text corpus through TF-IDF word vectorizer, dropping words which occurred less than 10 times in the corpus

![](/images/abusive1.png)
 
***
### Modeling
***
 - Started with two models: logistic regression and random forest
 - Ran GridSearchCV w/ RepeatedStratifiedKFold CV to perform parameter tuning on both models
 - Random forest performed best and was the final model

![](/images/abusive2.png)

***
### Conclusions and future scope
***
Our dataset was too big to process entirely with current hardware specifications, so we used a subset of a very well annotated Twitter dataset. We confirmed there were no missing data points and no wild outliers that we didn't expect.

We were able to process the text data to clean it up, lowercase everything, remove special characters, and then vectorize the cleaned text via TF IDF, to value important words higher.

With the vectorized vocabulary, we trained both Logistic Regresion and Random Forest models. After optimizing hyperparameters in both cases, We found the Random Forest model confidently outperformed the Logistic Regression model, giving us an accuracy of 87.5% and Recall of 92%.

Future Scope:
1. Attempt other models
2. Perform more targeted cleanup of the word corpus
3. Use full dataset of 135000 tweets
