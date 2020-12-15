# 1- Introduction

![alt text](https://github.com/mehdigolzadeh/Data_science_helper/blob/master/images/OverviewTextClassification.png?raw=true)

Most text classification and document categorization systems can be deconstructed into the following four phases:
* [Feature extraction](#fe)
* [Dimensionality Reduction](#dr)
* [Classifier selection](#cs)
* [Evaluations](#ev)

In general, the text classification system contains four different levels of scope that can be applied:
  1. Document level: In the document level, the algorithm obtains the relevant categories of a full document.
  2. Paragraph level: In the paragraph level, the algorithm obtains the relevant categories of a single paragraph (a portion of a document).
  3. Sentence level: In the sentence level, obtains the relevant categories of a single sentence (a portion of a paragraph).
  4. Sub-sentence level: In the sub-sentence level, the algorithm obtains the relevant categories of sub-expressions within a sentence (a portion of a sentence )).
  
# 2- Feature Extraction<a name="fe"></a>
In this secion, we introduce methods for cleaning text data sets, thus removing implicit noise and allowing for informative featurization. 

## 2.1. Text Cleaning and Pre-processing
In many algorithms, especially statistical and probabilistic learning algorithms, Unnecessary words such as stopwords, misspelling, slang, etc. and unnecessary features can have adverse effects on system performance:

### 2.1.1. Tokenization
Tokenization is a pre-processing method which breaks a stream of text into words, phrases, symbols, or other meaningful elements called tokens. The main goal of this step is the investigation of the words in a sentence.

  >_After sleeping for four hours, he decided to sleep for another four._
  
  >_{ “After” “sleeping” “for” “four” “hours” “he” “decided” “to” “sleep” “for” “another” “four” }_
  
### 2.1.2. Stop Words
Text and document classification includes many words which do not contain important significance to be used in classification algorithms, such as _{“a”, “about”, “above”, “across”, “after”, “afterwards”, “again”,. . .}_ The most common technique to deal with these words is to remove them from the texts and documents
  
### 2.1.3. Capitalization
The most common approach for dealing with inconsistent capitalization is to reduce every letter to lower case. This technique projects all words in text and document into the same feature space, but it causes a significant problem for the interpretation of some words _(e.g., “US” (United States of America) to “us” (pronoun))_.

### 2.1.4. Slang and Abbreviation
A common method for dealing with these words is converting them into formal language

### 2.1.5. Noise Removal
Critical punctuation and special characters are important for human understanding of documents, but it can be detrimental for classification algorithms.

### 2.1.6. Spelling Correction
Spelling correction is an optional pre-processing step. Typos (short for typographical errors) are commonly present in texts and documents, especially in social media text data sets (e.g., Twitter).Many techniques and methods are available for researchers including hashing-based and context-sensitive spelling correction techniques, as well as spelling correction using Trie and Damerau–Levenshtein distance bigram.

### 2.1.7. Stemming
One word could appear in different forms (i.e., singular and plural noun form) while the semantic meaning of each form is the same. Text stemming modifies words to obtain variant word forms using different linguistic processes such as affixation (addition of affixes). For example, the stem of the word _“studying”_ is _“study”_).

### 2.1.8. Lemmatization
Lemmatization is a NLP process that replaces the suffix of a word with a different one or removes the suffix of a word completely to get the basic word form (lemma).

## 2.2 Syntactic Word Representation
Many researchers addressed novel techniques for solving this problem, but many of these techniques still have limitations. In [this study](https://link.springer.com/chapter/10.1007/11766247_28), a model was introduced in which the usefulness of including syntactic and semantic knowledge in the text representation for the selection of sentences comes from technical genomic texts. 

The other solution for syntactic problem is using the n-gram technique for feature extraction.

### 2.2.1. N-Gram
The n-gram technique is a set of n-word which occurs “in that order” in a text set. This is not a representation of a text, but it could be used as a feature to represent a text.
BOW is a representation of a text using its words (1-gram) which loses their order (syntactic). It is very common to use 2-gram and 3-gram. In this way, the text feature extracted could detect more information in comparison to 1-gram. 

An example of 2-Gram

  > _After sleeping for four hours, he decided to sleep for another four._

  > _{ “After sleeping”, “sleeping for”, “for four”, “four hours”, “four he” “he decided”, “decided to”, “to sleep”, “sleep for”, “for another”, “another four” }._
  
An example of 3-Gram

  > _After sleeping for four hours, he decided to sleep for another four._
  
  > _{ “After sleeping for”, “sleeping for four”, “four hours he”, “ hours he decided”, “he decided to”, “to sleep for”, “sleep for another”, “for another four” }._
  
### 2.2.2. Syntactic N-Gram
In [this study](https://link.springer.com/chapter/10.1007/978-3-642-37798-3_1), syntactic n-grams are discussed which is defined by paths in syntactic dependency or constituent trees rather than the linear structure of the text.


Two common methods of text feature extraction: Weighted word and word embedding techniques:

## 2.3. Weighted Words

The most basic form of weighted word feature extraction is TF, where each word is mapped to a number corresponding to the number of occurrences of that word in the whole corpora.

### 2.3.1. Bag of Words (BoW)

The bag-of-words model (BoW model) is a reduced and simplified representation of a text document from selected parts of the text, based on specific criteria, such as word frequency.

In a BoW, a body of text, is thought of like a bag of words. Lists of words are created in the BoW process. The words are often representative of the content of a sentence. While grammar and order of appearance are ignored, multiplicity is counted and may be used later to determine the focus points of the documents.

Here is an example of BoW:

>“As the home to UVA’s recognized undergraduate and graduate degree programs in systems engineering. In the UVA Department of Systems and Information Engineering, our students are exposed to a wide range of range”

>Bag-of-Words (BoW)
>{“As”, “the”, “home”, “to”, “UVA’s”, “recognized”, “undergraduate”, “and”, “graduate”, “degree”, “program”, “in”, “systems”, “engineering”, “in”, “Department”, “Information”,“students”, “ ”,“are”, “exposed”, “wide”, “range” }

>Bag-of-Feature (BoF)
>Feature = {1,1,1,3,2,1,2,1,2,3,1,1,1,2,1,1,1,1,1,1}


## 2.3.3. Term Frequency-Inverse Document Frequency

IDF assigns a higher weight to words with either high or low frequencies term in the document. This combination of TF and IDF is well known as Term Frequency-Inverse document frequency (TF-IDF). 

>W(d,t) = TF(d,t)∗log( N/df(t) )

Here N is the number of documents and d f (t) is the number of documents containing the term t in the corpus. The first term in Equation (1) improves the recall while the second term improves the precision of the word embedding


## 2.4. Word Embedding

Word embedding is a feature learning technique in which each word or phrase from the vocabulary is mapped to a N dimension vector of real numbers. Various word embedding methods have been proposed to translate unigrams into understandable input for machine learning algorithms. Recently, the Novel technique of word representation was introduced where word vectors depend on the context of the word called “Contextualized Word Representations” or “Deep Contextualized Word Representations”.

### 2.4.1. Word2Vec

An improved word embedding architecture. The Word2Vec approach uses shallow neural networks with two hidden layers, continuous bag-of-words (CBOW), and the Skip-gram model to create a high dimension vector for each word. The Skip-gram model dives a corpus of words w and context c. This method provides a very powerful tool for discovering relationships in the text corpus as well as similarity between words. For example, this embedding would consider the two words such as “big” and “bigger” close to each other in the vector space it assigns them.





# Dimensionality Reduction<a name="dr"></a>


# Classifier selection<a name="cs"></a>


# Evaluations<a name="ev"></a>
