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




# Dimensionality Reduction<a name="dr"></a>


# Classifier selection<a name="cs"></a>


# Evaluations<a name="ev"></a>
