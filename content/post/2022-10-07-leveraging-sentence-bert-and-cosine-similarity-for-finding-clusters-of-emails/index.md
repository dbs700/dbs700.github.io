---
title: Leveraging SBERT and Cosine Similarity for finding clusters of similar emails
authors: 
- Dmitrii Storozhenko
date: '2022-10-07'
slug: []
categories: []
tags: []
hero: /images/hero-22.jpg
excerpt: What is the difference between a phishing e-mail and an ordinary e-mail you receive from a colleague, friend, or even family member? One can say that the difference is in the way the message is presented to the recipient. This is a good point, but there are a few things to remember before making the distinction.
---

What is the difference between a phishing e-mail and an ordinary e-mail you receive from a colleague, friend, or even family member? One can say that the difference is in the way the message is presented to the recipient. This is a good point, but there are a few things to remember before making the distinction. There are many articles and papers about how to identify a phishing email. For instance:

- Legit companies don’t request your sensitive information via email
- Legit companies usually call you by your name
- Legit companies have domain emails
- Legit companies know how to spell
- Legit companies don’t force you to their website
- Legit companies don’t send unsolicited attachments

And even considering all those things, it's still difficult to distinguish between an ordinary e-mail and a phishing e-mail. But if you receive not one but a thousand emails every day, how can you ensure that you haven't missed or misclassified anything? 


Let's assume that phishing emails could be very similar, especially within a phishing campaign. 

After research, we ended up with a model that combines the strengths of masked and permuted language modeling for language understanding based on Sentence Transformers. Sentence Transformers is a Python framework for state-of-the-art sentence, text, and image embeddings. The initial work is described in the paper Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks.
 
An embedding is a relatively low-dimensional space into which you can translate high-dimensional vectors. Embeddings make it easier to do machine learning on large inputs like sparse vectors representing words.
When we have a vector representation for each email's data, we can compare it with each other and use cosine similarity. This is a measure of similarity between two sequences of numbers. To define it, the sequences are viewed as vectors in an inner product space, and the cosine similarity is defined as the cosine of the angle between them, that is, the dot product of the vectors divided by the product of their lengths.

The similarity increases when the distance between the vectors decreases. We can also configure the cosine similarity threshold for which we consider two sentences are similar. Also, we can specify the minimum size for a local community. This allows us to get either large coarse-grained clusters or small fine-grained clusters.

What about the inference time? For instance, using SBERT fast_clustering.py we have a clustering algorithm that is tuned for large datasets (50k sentences in less than 5 seconds). In a large list of sentences it searches for local communities. In our case, the time was ~5 min based on structure and amount of data. Then we went with a different approach, using the same SBERT capabilities:


## sentence_transformers.util.semantic_search


This function performs a cosine similarity search between a list of query embeddings and a list of corpus embeddings. It can be used for Information Retrieval / Semantic Search for corpora up to about 1 Million entries.

Parameters
- query_embeddings – A 2 dimensional tensor with the query embeddings.
- corpus_embeddings – A 2 dimensional tensor with the corpus embeddings.
- query_chunk_size – Process 100 queries simultaneously. Increasing that value increases the speed, but requires more memory.
- corpus_chunk_size – Scans the corpus 100k entries at a time. Increasing that value increases the speed, but requires more memory.
- top_k – Retrieve top k matching entries.
- score_function – Function for computing scores. By default, cosine similarity.

Returns a list with one entry for each query. Each entry is a list of dictionaries with the keys ‘corpus_id’ and ‘score’, sorted by decreasing cosine similarity scores.

This approach helped to increase the inference time and the efficiency, at the same time empower us to identify more groups of similar emails with ease.


[SBERT:Semantic Search](https://www.sbert.net/examples/applications/semantic-search/README.html)
[Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks](https://arxiv.org/abs/1908.10084)

{{<subscribe email = "your@email.com">}}
