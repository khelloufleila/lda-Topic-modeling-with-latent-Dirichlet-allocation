

lda: Topic modeling with latent Dirichlet allocation
====================================================

Objectif
------------
The subject relates to "Topic Modeling". This is to extract the most recurring themes from a set of sentences. 
Themes can be single words or compound words of size 2 or 3 (n-grams).

Requirements:
------------
Python 3. The following packages are required:
numpy, pandas, gensim, pyLDAvis, matplotlib, spacy

Installation
------------
"!pip install pyLDAvis"

``pip install lda``

Notes
---------------

Topic Models, in a nutshell, are a type of statistical language models used for uncovering hidden structure in a collection of texts. 
In a practical and more intuitively, we can think of it as a task of:

- Dimensionality Reduction, where rather than representing a text T in its feature space as {Word_i: count(Word_i, T) for Word_i in Vocabulary}, we can represent it in a topic space as {Topic_i: Weight(Topic_i, T) for Topic_i in Topics}
- Unsupervised Learning, where it can be compared to clustering, as in the case of clustering, the number of topics, like the number of clusters, is an output parameter. By doing topic modeling, we build clusters of words rather than clusters of texts. A text is thus a mixture of all the topics, each having a specific weight
- Tagging, abstract “topics” that occur in a collection of documents that best represents the information in them.

There are several existing algorithms we can use to perform the topic modeling.
The most common of it are, Latent Semantic Analysis (LSA/LSI), Probabilistic Latent Semantic Analysis (pLSA), and Latent Dirichlet Allocation (LDA)


LDA is a generative probabilistic model that assumes each topic is a mixture over an underlying set of words, 
and each document is a mixture of over a set of topic probabilities.
The parameters of LDA are: 
- Alpha parameter is Dirichlet prior concentration parameter that represents document-topic density — with a higher alpha, 
documents are assumed to be made up of more topics and result in more specific topic distribution per document.
- Beta parameter is the same prior concentration parameter that represents topic-word density — with high beta, 
topics are assumed to made of up most of the words and result in a more specific word distribution per topic.



Getting started
---------------

In this work I used LDA for topic modeling using sklearn implementation in python 3

Firstly, I used a regular expression to remove any punctuation, removing contract forms, deleting mutiple space , removing low lenght words  and then lowercase the text.
To verify whether the preprocessing, I maked a simple word cloud using the wordcloud package to get a visual representation of the most common words. 

Then, I transformed the textual data in a format that will serve as an input for training LDA model.
I started by tokenizing the text, removing stopwords, make bigrams , make trigrams and lemmatize. 
Next I convert the tokenized object into a corpus object and dictionary.

For that, I kept the parameters to defaul except for inputting the number of topics. 
I built a model with 4 topics where each topic is a combination of keywords, and each keyword contributes a certain weightage to the topic.

Now that we have a trained model we visualize the topics for interpretability. To do so, 
I used a popular visualization package, pyLDAvis which is designed to help interactively with:

Better understanding and interpreting individual topics, and
Better understanding the relationships between the topics.

My approach to finding the optimal number of topics is to build many LDA models with different values of number of topics (k) and pick the one that gives the highest coherence value.
get 5 as the optimal number of topics with the Coherence of 0.57

For the second method, I used TF-IDF with gridsearch on LDA hyperparameters and pick the one that gives the highest coherence value. 
 
