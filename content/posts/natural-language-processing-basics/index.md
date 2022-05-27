---
title: "Natural Language Processing Basics"
description: "Notes Taken on Stanford CS224N"
date: "2020-09-01"
slug: "natural-language-processing-basics"
categories:
    - Artificial Intelligence
    - Learning Notes
tags:
    - artificial intelligence
    - learning notes
---

## How to define the meaning of a word
### One-Hot Vector
Say we have 3 word, "natural", "language", "processing", we can define:
* "nature"=[1, 0, 0],
* "language"=[0, 1, 0],
* "processing"=[0, 0, 1]
#### Cons:
* With the increase of the words, the dimension of the vectors grows rapidly.
* Any vector timing another vector equals 0, we cannot use cosine to measure their similarity.
### Word2Vec
The basic theory is that we can know the meanning of a word from the words beside them.
#### Skip-Gram Model
Say we have a phrase "natural language processing", take "language" as a central word then we have:
P("natural") = P("natural"|"language")
P("processing")=P("processing"|"language")
Generally, we have
$$ 
P(Context Word = o| Center Word = c) = \frac{e^{(u_o^Tv_c)}}{\sum\nolimits_{w\in{Vocab}}e^{(u_w^Tv_c)}}
$$
Loss function would be 
$$
J(\theta) = -\frac{1}{T}logL(\theta) = -\frac{1}{T}\sum_{t=1}^T\sum_{-m\leq j\leq m\&j\neq0}logP(w_{t+j}|w_t; \theta)
$$
Note that $L(\theta)$ is the maximum likelihood function.
### Single Value Decomposition
We use a word-to-document co-occurrence matrix.
Say we have two sentences, and the window size = 1.
I like deep learning.
I like natural language processing.
| | I | like | deep | learning | natural | language | processing
| - | - | - | - | - | - | - | - |
| I | 0 | 2 | 0 | 0 | 0 | 0 | 0 | 
| like | 2 | 0 | 1 | 0 | 1 | 0 | 0 |
| deep | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
| learning | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| natural | 0 | 1 | 0 | 0 | 0 | 1 | 0 |
| language | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| processing | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
Then we can compress the matrix and store the vectors.
### GloVe
As its name suggests, GloVe uses global information to build vectors.
$X_{ij}$ means how many times word j has shown up in the context of word i, then $X_i = \sum_kX_{ik}$ means all the words showing up in the context of word i. The probility of word j showing up in the context of word i is denoted as
$$
P_{ij} = P(j|i) = X_{ij} / X_i
$$
Loss Function:
$$
w_i * w_j = logP(i|j)
$$
$$
J = \sum_{i, j = 1}^Vf(X_{ij})(w_i^T\tilde{w_j} + b_i + \tilde{b_j} - logX_{ij})^2
$$
## Named Entity Recognition
We want to find the names in the text and classfy them, for example:  
Only France [LOC] and Britain [LOC] back Fischler [PER] 's proposal.
### Window Classification
We can use the words beside the target word to classify it.  
Say the window size = 2 and the target word is Paris. We can have a window like:  
museum  in  Paris  are  amazing  
x1      x2  x3     x4   x5  
$X_{window} = [x_1, x_2, x_3, x_4, x_5]$
If we have mulitple class, we can use a softmax classifier.  
Say x denotes the input word vector and y is the target class among k classes, then we have
$$
P(y|x) = \frac{e^{(W_y*x)}}{\sum_{c=1}^ke^{(W_c*x)}}
$$
The loss function is a cross entropy function:
$$
J(\theta) = \frac{1}{N}\sum_{i = 1}^N-log(\frac{e^{(W_y*x)}}{\sum_{c = 1}^ke^{(W_c*x)}})
$$
## Syntactic Structure Analaysis
### Constituency Parsing
Analyse the words as part of speech [POS], and then connect them as phrases and finally sentences.  
Say we have a phrase like  
the cute cat at the coffee shop  
Its structure is [DET] [ADJ] [NOUN] [PREP] [DET] [NOUN], and Noun Phrase = { [DET] [ADJ] [NOUN] }, Preposition Phrase = { [PREP] [DET] [NOUN] }, and they together make a sentence.
### Dependency Parsing
#### Transition-based Dependency Parsing
Transition-based dependency parsing is very similar to a state machine, for a given sentence $S = \{w_0w_1\cdots w_n\}$, the state has three parts, $(\sigma, \beta, A)$.  
$\sigma$ is a stack of words.  
$\beta$ is a buffer of words.  
A is a collection of dependency arc, every edge is like $(w_i, r, w_j)$, and r denotes the dependency between words.  
At the initial state, $\sigma$ contains ROOT $w_0$ only, and $\beta$ contains the rest of the sentence, while A is an empty set.  
There are 3 transition between states:
* SHIFT: pop the first word out of the buffer and put it in the stack.
* LEFT-ARC: add $(w_j, r, w_i)$ to the collection of edges, and $w_j$ is on the top of the stack while $w_i$ is the second top one of the stack.
* RIGHT-ARC: add $(w_i, r, w_j)$ to the collection of edges, and $w_i$ is on the top of the stack while $w_j$ is the second top one of the stack.
## Language Model
The model is about :  
Given {$x_1, x_2, \cdots, x_n$}, predict $x_{n+1}$.
$$
P(x^{t + 1}, x^t, \cdots, x^1) = \sum_{t = 1}^TP(x^{t+1} | x^t, \cdots, x^1)
$$
### N-Gram Model
The most classic one is the N-Gram Model. For example, the bigram of "natural language processing" is "natural language" and "language processing".  
The basic assumption of the model is that 
* the probability of n-gram is propotional to the probability of the word.
* $P(x^{t + 1})$ is only related to the (n - 1) word before it.
$$
P(x^{t + 1} | x^t, \cdots, x^1) \approxeq \frac{count(x^{t + 1}, x^t, \cdots, x^{t - n + 2})}{count(x^t, \cdots, x^{t - n + 2})}
$$
Cons:
* Sparsity Problem
* The storage grows very fast as the n grows.
### Recurrent Neural Network
In a RNN, different parameters share a same matrix, and they are not limited to a fixed size window.  
Hidden Layer:
$$
h_t = \sigma(W^{(hh)}h_{t - 1} + W^{ht}x_{[t]})
$$
Output:
$$
\hat{y_t} = softmax(W^{(S)}h_t)
$$
The loss function is cross entropy loss.  
We can use perplexity to evalute our language model.
$$
perplexity = e^{J(\theta)}
$$
Pros:
* It can deal with input of any length.
* We can use information with a long history.
* The size of the model does not increase with input size.
* The parameters of weights are shared efficiently.
Cons:
* RNN is comparatively slow because it is not parallel.
* Gradient vanishing makes long history information hard to capture.
## Gradient Vanishing and Gradient Explosion
In $W^{(t - k)}$, if |W| is smaller than 1, as t - k incrrases, W is likely to become very small so it is very likely for us to loss information from the past.
In the opposite, if |W| is greater than 1, as t - k incrrases, W is likely to become very large and cause explosion.
### Gradient clipping
If the gradient is greater than the preset threshold, we clip the gradient.
## Long Short Term Memory (LSTM)
We introduce cell states to store the long-term information, and they can be written and erased by control gate.
A general LSTM:
Input gate
$$
i_t = \sigma(W^{(i)}x_t + U^{(i)}h_{t - 1}) 
$$
Forget gate
$$
f_t = \sigma(W^{(f)}x_t + U^{(f)}h_{t - 1})
$$
Output gate
$$
o_t = \sigma(W^{(o)}x_t + U^{(o)}h_{t - 1}) 
$$
New memory cell
$$
\tilde{c_t} = tanh(W^{(c)}x_t + U^{(c)}h_{t - 1})
$$
Final memory cell
$$
c_t = f_t\circ c_{t - 1} + i_t\circ \tilde{c_t}
$$
Hidden state
$$
h_t = o_t\circ tanh(c_t) 
$$
Gated Recurrent Unit (GRU)
GRU is very similar to LSTM, it combines forget gate and input gate into an update gate, and the cell state is combined into hidden state.
Update gate
$$
z_t = \sigma(W^{(z)}x_t + U^{(z)}h_{t - 1}) 
$$
Reset gate
$$
r_t = \sigma(W^{(r)}x_t + U^{(r)}h_{t - 1}) 
$$
New memory cell
$$
\tilde{h_t} = tanh(r_t\circ Uh_{t - 1} + Wx_t) 
$$
Hidden state
$$
h_t = (1 - z_t)\circ \tilde{h_t} + z_t\circ h{t - 1}
$$
## Neural Machine Translation
Neural machine translation is generally a sequence to sequence model. It uses RNN as an encoder and another RNN as a decoder.  
Loss function:
$$
J(\theta) = \frac{1}{T}\sum_{t = 1}^T-log\tilde{y_{x_{t + 1}}^{(t)}}
$$
We choose the word with highest probability as the next input of the decoder.
### Bilingual Evaluation Study (BLEU)
Presion score: $p_n = \frac{\# matched n-grams}{\# n-grams in the candidate translation}$
Weight: $w = \frac{1}{2^n}$
Penalty: $\beta = e^{min(0, 1 - \frac{len_{ref}}{len_{MT}})}$
BLEU:
$$
BLEU = \beta\prod_{i = 1}^kp_n^{w_n}
$$
### Attention
We can use the attention method to focus on the specific context of the current word.  
#### Process:
* Get the hidden states of the encoder $(h_1, h_2, h_T)$.
* Say the hidden state of the current decoder is $s_{t - 1}, we can use it for the relationship between input index j and current output index. $e_{ij} = a(s_{t - 1}, h_j)$, in the form of the vector is $\vec{e_t} = (a(s_{t - 1}, h_1), \cdots, a(s_{t - 1}, h_T))$, a denotes a relationship operation between s and h.
* Compute the attention by softmaxing $\vec{e_t}$: $\vec{a_t} = softmax(\vec{e_t})$
* Compute the context vector: $\vec{c_t} = \sum_{j =1}^Ta_{ij}h_j$
* Finally, we have the next hidden state of the decoder in the form $s_t = f(s_{t - 1}, y_{t - 1}, c_t)$, and the ouput would be $p(y_t|y_1, \cdots, y_{t - 1}, \vec{x}) = g(y_{i - 1}, s_i, c_i)$.
## Question Answering System
We use the Stanford Question Answering Dataset.
### Stanford Attention Reader
We get the features of the questions with a Bidirectional LSTM. For the answers, we can use a Bidirectional LSTM to get the features of every word, and $Attention = (\vec{feature_{q_i}}, \vec{feature_{w_i}})$, so that we can infer the start position and the end position of the answer.  
The loss function is:
$$
L = -\sum logP^{start}(a_{start}) - \sum logP^{end}(a_{end})
$$
### Birectional Attention Flow
The attention model here is bidirectional, because we have a query-to-context layer and a context to query layer.  
Similar matrix:
$$
S_{ij} = w_{sim}^T[c_i; q_j, c_i \circ q_j]\in R
$$
Note that $c_i$, $q_i$ denote context vector and query vector respectively.  
For the context to query attention,  
Attention score:
$$
\alpha^i = softmax(S_{i,:})\in R^M \forall i\in{1,\cdots, N}
$$
Weighted vector:
$$
a_i = \sum_{j = 1}^M\alpha^i_jq_j \in R^{2h} \forall i\in{1,\cdots, N}
$$
For the query to context attention,  
$$
m_i = max_jS_{ij } \in R \forall i\in{1,\cdots, N}
$$
$$
\beta = softmax(m)\in R^N
$$
$$
c' = \sum_{i = 1}^N\beta^ic_i \in R^{2h} 
$$
The output of the Attention Flow Layer would be
$$
b_i = [c_i; a_i; c_i\circ a_i; c_i\circ c'] \in R^{8h} \forall i \in{1, \cdots, N}
$$
## Convolutional Neural Network
If the embedding of a word is a k-dimensional vector, a sentence is a matrix. With n word, the matrix size is n * k. We usually need to pad the sentence to have a deeper convolutional network.  
The initiative of pooling is the stablize the network, when the input changes little.
### Quasi Recurrent Neural Network
Quaso Recurrent Neural Network is a combination of convolutional neural network and recurrent neural network. The main idea is to use a convolutional neural network to extract features and replace the pooling layer with dynamic average pooling.  
For the feature extraction, the candidate vector, forget gate, output gate is:
$$
Z = tanh(W_z * X)
$$
$$
F = \sigma(W_f * X)
$$
$$
O = \sigma(W_o * X)
$$
The dynamic average pooling is:
$$
x_t = f_t\cdot c_{t - 1} + (1 - f_t)\cdot z_t
$$
$$
h_t = o_t\cdot c_t
$$
## Subword Model
### Character-level model
We can use more layers of convolution, pooling and highway to solve the complexity problem.
### Byte Pair Encoding
Byte pair encodes n-grams of the highest frequency until its vocabulary reaches the preset threshold.
### FasttText
It takes a word as bag of character n-gram.
## Contextual Word Representation
### Embeddings from Language Models (ELMO)
ELMO uses a bidirectional LSTM to compute the contextual embedding. The lower layer represents the basic grammar information, while the higher layer represents context information.  
Forward language model:
$$
p(t_1, t_2, \cdots, t_N) = \prod_{k = 1}^Np(t_k|t_1, t_2, \cdots, t_{k - 1})
$$
Backword language model:
$$
p(t_1, t_2, \cdots, t_N) = \prod_{k = 1}^Np(t_k|t_{k + 1}, t_{k + 2}, \cdots, t_N)
$$
The initiative of the bidirectional LSTM is to maximaize:
$$
\sum_{k + 1}^N(logp(t_k|t_1, t_2, \cdots, t{k - 1}) + logp(t_k|t_{k + 1}, t_{k + 2}, \cdots, t_N))
$$
For the word at index k, it is represented by (2L + 1) vectors. One of them is an embedding not related to the context, while L layers of forward LSTM produces $\vec{h_{kj}} related to the former paragraph and L layers of backward LSTM produces $\vec{h_{kj}} for the rest of the paragraph.
For the following layers, we have:
$$
ELMO_k^{task} = E(R_k; \theta^{task}) = \gamma^{task}\sum_{j = 0}^Ls_j^{task}h_{k, j}^{LM}
$$
Note that $s^{task}$ is softmaxed and $\gamma^{task}$ is a scale parameter.
### Generative Pre Training (GPT)
The basic structure of the GPT is a transformer, which is used for unsupervised learning for the text, and then we can use the embedding for supervised fine-tuning for the following tasks.  
Note that it is one direction.
### Bidirectional Encoder Representations from Transformers
Bert is especially tuned for:
* Predict a word with k% missing.
* Predict a following sentence.
### Transformer
#### Self Attention
We compute the ralationship between words in self attention. The encoder has multiple self-attention layers, after which the input gets the context information for every word.  The decoder has a similar structure, but it takes the output of itself and the output of encoder as its input.
##### The Structure of Self Attention
* MatMul
* Scale
* Mask
* SoftMax
* MatMul
For the encoder, the input is Query, Key and Value, and $d_k$ denotes that dimension of query and vectors.
$$
Attention(Q, K, V) = softmax(\frac{QK^T}{\sqrt{d_k}})V
$$
#### The Structure of a transformer
* Positional encoding
* Multi-Head attention
* Add & Normalize
* Feed forward
Position encoding allows the model to learn about the position of a word in the sentence.  
Multi-head attention contains multiple self-attention layers, and different head may learn different information of the features.  
The Add part is very similar to Residual Connection, which can pass the information of the former layer to the next one.