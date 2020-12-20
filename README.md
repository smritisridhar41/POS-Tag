# Part of Speech-Tag
There are two “tagsets” that are more commonly used to classify the PoS of a word: the Universal Dependencies Tagset (simpler, used by spaCy) and the Penn Treebank Tagset (more detailed, used by nltk).

Ultimately, what PoS Tagging means is assigning the correct PoS tag to each word in a sentence. 
Today, it is more commonly done using automated methods. Let us first understand how useful is it, then we can discuss how it can be done.
Main ways to do so:

1. Manual Tagging: This means having people versed in syntax rules applying a tag to every and each word in a phrase.
This is the time consuming, old school non automated method. Reminds you of homeworks? Yeah… But it is also the basis for the third and fourth way.

2. Rule-Based Tagging: The first automated way to do tagging. Consists of a series of rules (if the preceding word is an article and the succeeding word is a noun, then it is an adjective…). Has to be done by a specialist and can easily get complicated (far more complicated than the Stemmer we built).
The position of “Most famous and widely used Rule Based Tagger” is usually attributed to E. Brill’s Tagger.

3. Stochastic/Probabilistic Methods: Automated ways to assign a PoS to a word based on the probability that a word belongs to a particular tag or based on the probability of a word being a tag based on a sequence of preceding/succeeding words. These are the preferred, most used and most successful methods so far. 
They are also the simpler ones to implement (given that you already have pre annotated samples — a corpus).
Among these methods, there could be defined two types of automated Probabilistic methods: the Discriminative Probabilistic Classifiers (examples are Logistic Regression, SVM’s and Conditional Random Fields — CRF’s) and the Generative Probabilistic Classifiers (examples are Naive Bayes and Hidden Markov Models — HMM).

4. Deep Learning Methods: Methods that use deep learning techniques to infer PoS tags. So far, these methods have not shown to be superior to Stochastic/Probabilistic methods in PoS tagging — they are, at most, at the same level of accuracy — at the cost of more complexity/training time.
Today, some consider PoS Tagging a solved problem. Some closed context cases achieve 99% accuracy for the tags, and the gold-standard for Penn Treebank is kept at above 97.6 f1-score since 2002 in the ACL (Association for Computer Linguistics) gold-standard records.

But I’ll make a short summary of the things that we’ll do here.
First, download a corpus. A corpus is how we call a Dataset in NLP. We’ll use Penn Treebank sample from NLTK and Universal Dependencies (UD) corpus. We’ll also see how to use the CoNLL-u format, the most common format for linguistic annotated corpora (the plural of corpus).
Second step is to extract features from the words. We do that to by getting word termination, preceding word, checking for hyphens, etc. This will compose the feature set used to predict the POS tag.
Third, we load and train a Machine Learning Algorithm. We’ll use a Conditional Random Field (CRF) suite that is compatible with sklearn, the most used Machine Learning Module in Python.
We test the trained models, checking f1 scores (explained there) for each. We also provide a way to test the models in a more “practical” manner.
We save the models to be able to use them in our algorithm.
