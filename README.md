# keywords and Keyphrases Extraction
Based on: 

[TextRank: Bringing Order into Texts - by Rada Mihalcea and Paul Tarau]
(https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf)

The input text is given: .pdf file

## Steps:
#### 1) Extracting PDF file
#### 2)Cleaning Text Data
#### 3)POS Tagging For Lemmatization
NLTK is again used for <b>POS tagging</b> the input text so that the words can be lemmatized based on their POS tags.

Description of POS tags: 
http://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html

#### 4)Lemmatization

The tokenized text (mainly the nouns and adjectives) is normalized by <b>lemmatization</b>.
In lemmatization different grammatical counterparts of a word will be replaced by single
basic lemma. For example, 'glasses' may be replaced by 'glass'. 

Details about lemmatization: 
    
https://nlp.stanford.edu/IR-book/html/htmledition/stemming-and-lemmatization-1.html

#### 5)POS tagging for Filtering
#### 6)POS Based Filtering: 
any word from the lemmatized text, which isn't a noun, adjective, or gerund (or a 'foreign word'), is here
considered as a <b>stopword</b> (non-content). This is based on the assumption that usually keywords are noun,
adjectives or gerunds. 

Punctuations are added to the stopword list too

#### 7)Complete stopword generation
(Used longstopword.txt for better filtering of stopwords)

(Source of stopwords data: https://www.ranks.nl/stopwords)

#### 8)Removing Stopwords
#### 9)Vocabulary Creation
#### 10)Building Graph (refered paper and other online articals)
#### 11)Calculating weighted summation of connections of a vertex
inout[i] will contain the total no. of undirected connections\edges associated withe the vertex represented by i.
#### Scoring Vertices
The formula used for scoring a vertex represented by i is:

score[i] = (1-d) + d x [ Summation(j) ( (weighted_edge[i][j]/inout[j]) x score[j] ) ] where j belongs to the list of vertices that has a connection with i. 

d is the damping factor.

The score is iteratively updated until convergence. 
#### 12)Phrase Partitioning

Paritioning lemmatized_text into phrases using the stopwords in it as delimeters.
The phrases are also candidates for keyphrases to be extracted. 

#### 13)Create a list of unique phrases.
Repeating phrases\keyphrase candidates has no purpose here, anymore. 

#### 14)Thinning the list of candidate-keyphrases.
Removing single word keyphrase-candidates that are present multi-word alternatives.

#### 15)Scoring Keyphrases

Scoring the phrases (candidate keyphrases) and building up a list of keyphrases
by listing untokenized versions of tokenized phrases\candidate-keyphrases.
Phrases are scored by adding the score of their members (words\text-units that were ranked by the graph algorithm)

#### 16)Ranking Keyphrases

Ranking keyphrases based on their calculated scores. Displaying top 'keywords_num' no. of keyphrases.


## Keyword and Score
<img src="https://github.com/chanduparmar/Keywords_and_keyphrases_extraction/blob/master/Score%20and%20Keyword.png" alt="Keyword and Score">

## Keyphrases and Score
<img src="https://github.com/chanduparmar/Keywords_and_keyphrases_extraction/blob/master/keyphrases_score.JPG" alt="Keyphrases and Score">


## References:
http://bdewilde.github.io/blog/2014/09/23/intro-to-automatic-keyphrase-extraction/
http://en.wikipedia.org/wiki/Stop_words
https://nlp.stanford.edu/IR-book/html/htmledition/stemming-and-lemmatization-1.html
http://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html
https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf


