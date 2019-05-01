---
layout: page
title: Acedemic Network
subtitle: I analyzed the relationship between topics and authors and visualized them.
---

# Abstract

With the rapid development of science and technology, the cross-convergence between various topics or fields is also increasing. Many problems may be technically difficult in the original topics or fields, but they can be easily solved after integrating knowledge of other topics or fields. Past researches has proven that there is indeed a link between different topics or fields. However, such correlations are often mutual, and there are few scholars studying the directed relationship between the topics or fields. This paper is going to find the relationship between different topics or fields based on the directed topic network.
Previously, some scholars used the K-core, an algorithm for measuring the density of graphs in undirected graphs, to analyze the relevance of different academic topics/fields and visualized them. This paper will analyze academic networks based on D-cores algorithm, a variant of K-core algorithm based on directed graphs. The algorithm will divide topics or fields into four categories. In order to study the frequent patterns of topics in the entire academic network, this paper uses the gSpan algorithm to analyze the entire academic network. As a result, three more common academic topics/fields were discovered.

# My model
I designed an algorithm to create a directed graph depicting different topics in the Academic Network. 

The procedure of creating the model is as follows.
Assume graph G = {V, E}. Then V is a collection of all topics/fields. For each author, the number of articles published in different fields is sorted. Assuming that the top three fields are the main research topics/fields, and the rest are secondary topics/fields. An edge is defined as a directed edge of from the author's major topics/fields to his secondary topics/fields, weighted by the number of papers the author has published in the secondary field.
Then, the weighted directed graph is processed by the D-core algorithm. D-core algorithm is a variation of K-core algorithm. It changes undirected network to directed network. The minimum indegree and the minimum outdegree are adjusted separately. The result is subgraphs. Considering different nodes appear in different subgraphs, the nodes can be divided into four categories: green, red, blue and black.

The picture 1 shows the network of 2012.

![avatar](/img/acenet_2012.png)

Green nodes are hot topics, because the indegree and outdegree of these nodes is very high. This means these nodes are often large, indicating that these topics/fields are developing rapidly. These fields also brought great help to other fields. For example, in the 2012 Artificial Neural Network, SVM, Machine Learning and other fields, these fields have a strong relationship with each other and developed rapidly.

Blue nodes stand for these relatively well-developed topics. They are developed, so the annual dynamics of this field are relatively small, and the sum of indegree and outdegree is relatively small, resulting in a smaller point. Taking Data Compression in 2012 as an example, in the field of information theory, data compression is already a relatively mature research topic. Only a small number of people are focusing on this topic. However, this topic is important to WiFi, Wireless Network.

Red topics have a high indegree and a low outdegree. So this field may be a good and unpopular field of development. Breakthroughs in other topics help developing these topics, such as Weather Forecasting. Such topics can be collectively referred to emerging topics.

The rest nodes are black. These nodes are often niche topics. Such topics are often difficult to define because they may be new-born topics and may develop rapidly in a few years, such as the metaverse in 2012, Or they can be the almost unpopular areas that have been developed before, such as business process management. Therefore, manual analysis is required for these points. 

Used k-core algorithm, d-core algorithm and the directed graph to analyze the topics
Used Gephi and javascript to visualize the relationship between different topics
Analyzed the relationships of topics and authors


