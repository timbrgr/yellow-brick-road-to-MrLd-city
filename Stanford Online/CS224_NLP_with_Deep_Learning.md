# NLP with Deep Learning (CS24)
Course website: http://web.stanford.edu/class/cs224n/

Youtube: https://www.youtube.com/playlist?list=PL3FW7Lu3i5Jsnh1rnUwq_TcylNr7EkRe6

## Lecture 2: Word Vector Representations: word2vec

### From symbolic to distributed representations

* one hot encoding: $ motel [000100] hotel [010000]^T = 0$
  * even though words are very similar (in spelling and in meaning) have no 'similarity'
  * problematic since query and document vectors are orthogonal --> no 'natural' notation of similarity
  
* **idea**: represent a word by means of its neighbours --> **distributed similarity**
  > Define a model that aims to predict between a *center word* $ w_t $ and *context words* $ w_{-t} $
  > with a loss function of $ J = 1 - p(w_{-t} | w_t) $
  
### Skip-gram prediction:
![skip gram](/img/CS224/skip_gram.PNG)

## Lecture 3: GloVe: Global Vectors for Word Representations

$$ J_t (\theta) = log \sigma (u_o^T v_c) + \sum_{j ~ P(w)} [log \sigma(-u_j^T v_c)] $$
