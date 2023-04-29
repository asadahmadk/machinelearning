## Topic Selection: Movie Reviews

### Changes in Feature
<b> AFINN sentiment dictionary </b>
AFINN module was used to handle the totalling and additional characters / basic lemmatizing before scoring. The dictionary was modified to remove all positive words and convert negative scores into positive scores. Each review was then given a score based on the total value of words that matched the AFINN dictionary. This score was added to the quantitative features array.

<b> Lemmatizer Function </b> 
It aims to combine words that are the same (hate, hates etc) during the countVectorizer stage. Stop words were also lemmatized for use in the vecotizer and ignored in the lemmatize class.

Using the <b> CountVectorizer over the HashingVectorizer </b>, in combination with the Lemmatizer function enhanced the performance. Stop words were removed, accents stripped, words converted to lowercase & n-grams included.

# Iterations

1. SVM Model
2. RDG Model
3. RDF Model
For final submission a I chose a combination of Ridge Regression Classifier, Random Forest Classifier and Perceptron.
