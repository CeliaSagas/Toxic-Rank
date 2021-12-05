![Header](https://github.com/CeliaSagas/Toxic-Rank/blob/0444a5f20ef80d64064f5506d0f8ef1391a0367a/img/Toxic%20Rank.jpg)




# Toxic
**Ranking Toxicity in Wikipedia Talk Page Comments**

<br><br>
The goal of this project is to give individual comments a toxicity score which can be used to make comparisons between comments in a dataset.

Cleaning methods may be important for topic modeling that may help with toxic comment scoring using a ridge model, however, models such as Bert and RoBERTa have also proven to be very effective in use cases and do not require text cleaning.

I will be using both methods in order to better assess what works best for this data.

# Cleaning

<br><br>
Text cleaning involves removing punctuation, stopwords, underscores, and empty spaces, as well as characters from other languages.

        def to_token(text):


        text = [text.translate(str.maketrans('', '', string.punctuation))]
        text = [word_tokenize(word) for word in text]
        text = [item for sublist in text for item in sublist]
        text = [stemmer.stem(word) for word in text]
        text = [re.sub(r'http\S+', '', each) for each in text]
        text = [re.sub('[0-9+]', '', each) for each in text]
        text = [re.sub('_', '', each) for each in text]
        text = [re.sub("\n","",each) for each in text]
        text = [re.sub('/_/g', '', each) for each in text]
        text = [re.sub('[^\u0000-\u05C0\u2100-\u214F]+', '', each) for each in text]
        text = [re.sub('[\u0401\u0451\u0410-\u044f]', '', each) for each in text]
        text = [word for word in text if word not in stop]
        text = [word.lower() for word in text]
        text = ["".join(dict.fromkeys(word)) for word in text]

        return text

I am currently unable to remove Greek letters from the dataset, as they are unicode, and have left them in for now.

<img src="https://github.com/CeliaSagas/Toxic-Rank/blob/5cfdd40f8d814b721ee9dce6eaef922ac6ae9ec9/img/data.png" width = 100>


I plan on finding a way to translate all text and include it for modeling-- however, it is unclear whether the human coders were given translated text or not.


Comparing scores generated from untranslated text and translated text should answer this question.


# Topic Modelling

<br><br>

Comparing Count Vectorization with TFIDF reveals a clear advantage for TFIDF with this dataset. I chose 10 topics on purpose in order to view the top 10 distinguishing characteristics for this dataset. However, it's most probable that I will be using the top five.


![Topics in NMF model with Count Vectorizer](https://github.com/CeliaSagas/Toxic-Rank/blob/5cfdd40f8d814b721ee9dce6eaef922ac6ae9ec9/img/Count_Vectorize.png)



The Count Vectorizer topic model reveals that topics are based primarily on one word alone, making it difficult to understand what these vectors correspond to. Additionally, at least two topics seem highly similar and may be difficult to distinguish. Finally, almost all of the top 10 topics derived from Count Vectorization are toxic in nature, which will make it more difficult to distinguish between toxic and non-toxic comments.





![Topics in NMF model with TFIDF Vectorizer](https://github.com/CeliaSagas/Toxic-Rank/blob/5cfdd40f8d814b721ee9dce6eaef922ac6ae9ec9/img/TFIDF_Vectorize.png)

The individual topic vectors in the TFIDF Vectorizer topic model are comprised of a wider set of words that facilitate topic comprehension for modeling. Additionally, the individual topics derived from the model are not similar, making interpretation easier. Finally, topics derived are both toxic ("fuck") and non-toxic ("articl") which will make it easier to distinguish between toxic and non-toxic comments.
