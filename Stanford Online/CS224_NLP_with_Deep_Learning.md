# NLP with Deep Learning (CS24)
Course website: http://web.stanford.edu/class/cs224n/

Youtube: https://www.youtube.com/playlist?list=PL3FW7Lu3i5Jsnh1rnUwq_TcylNr7EkRe6

## Lecture 2: Word Vector Representations: word2vec

### From symbolic to distributed representations

* one hot encoding: $ motel [000100] hotel [010000]^T = 0$
  * even though words are very similar (in spelling and in meaning) have no 'similarity' :zap:
  * problematic since query and document vectors are orthogonal --> no 'natural' notation of similarity
  
* :bulb: **idea** &rightarrow; represent a word by means of its neighbours --> **distributed similarity**
  > Define a model that aims to predict between a *center word* $ w_t $ and *context words* $ w_{-t} $
  > with a loss function of $ J = 1 - p(w_{-t} | w_t) $
  
### Skip-gram prediction:
![skip gram](/img/CS224/skip_gram.PNG)

&rightarrow; $ \forall t, t \in {1, ..., T} $ with radius $ m $: maximize probability of any *context word* given current *center word*

Using the `maximum likelihood` approach we would arrive at
$$ J'(\theta) = \prod_{t=1}^T \prod_{-m \leq j \leq m; j \neq 0}  p(w_{t+j} | w_t, \theta) $$

Using the `negative likelihood` method to convert the products into sum we arrive at
$$ J(\theta) = - \frac{1}{T} \sum_{t=1}^T \sum_{-m \leq j \leq m; j \neq 0} \log p(w_{t+j} | w_t) $$

which is the objective function that we try to *minimize*.

### word2vec
&rightarrow; predicting surrounding words in radius of $ m $ for $ p( w_{t+j} | w_t)

Using the `soft max` function we can calculate each word's probability 

$$ p (o | c) = \frac{\exp(u_o^T v_c)}{\sum_{w=1}^V \exp(u_w^T v_c} $$

where $ p (o | c) $ is the probability that $ o $ occurs as a *context word* of *center word* $ c $.

:question: &rightarrow; getting the right parameters of $ J (\theta) $ and $ p (o | c) $.

## Lecture 3: GloVe: Global Vectors for Word Representations

$$ J_t (\theta) = \log \sigma (u_o^T v_c) + \sum_{j ~ P(w)} [\log \sigma(-u_j^T v_c)] $$
