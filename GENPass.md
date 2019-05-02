---
layout: page
title: Password Analysis and Dictionary Attack
subtitle: We analyzed several leaked password datasets and used machine learning to create a more general password dictionary.
---

# Abstract

The password has become today's dominant method of authentication. While brute-force attack methods such as HashCat and John the Ripper have proven unpractical, the research then switches to password guessing. State-of-the-art approaches such as the Markov Model and probabilistic context-free grammar (PCFG) are all based on statistical probability. These approaches require a large amount of calculation, which is time-consuming. Neural networks have proven more accurate and practical in password guessing than traditional methods. However, a raw neural network model is not qualified for cross-site attacks because each dataset has its own features. Our work aims to generalize those leaked passwords and improves the performance in cross-site attacks.

In this paper, we propose GENPass, a multi-source deep learning model for generating ``general" password. GENPass learns from several datasets and ensures the output wordlist can maintain high accuracy for different datasets using adversarial generation. The password generator of GENPass is PCFG+LSTM (PL). We are the first to combine a neural network with PCFG. Compared with Long short-term memory (LSTM), PL increases the matching rate by 16\%-30\% in cross-site tests when learning from a single dataset. GENPass uses several PL models to learn datasets and generate passwords. The results demonstrate that the matching rate of GENPass is 20\% higher than by simply mixing datasets in the cross-site test. Furthermore, we propose GENPass with probability (GENPass-pro), the updated version of GENPass, which can further increase the matching rate of GENPass.

# Problem Description

When we talk about password guessing, we are not going to find a way to crack a specific password. We try to improve the matching rate between the training and testing sets. There are two types of tests in password guessing. One is called a one-site test, in which the training and testing sets are the same. The other is called a cross-site test, in which the training and testing sets are different. We have mentioned that all the previous work can only train and generate passwords based on one dataset, so their performance in cross-site tests is poor. However, a cross-site attack is the main technique for a hacker to crack a database.

On the other hand, many real passwords have been exposed but each dataset is not large enough for deep learning models. We believe if these datasets are combined together, the model can predict password more like a human.

In our work, we try to generate a “general" password list from several datasets to improve the performance of password guessing in cross-site tests. So we first define what is “general".

# Our model
## PCFG+LSTM(PL)
A regular password guessing method called PCFG divides a password by units. For instance, `password123' can be divided into two units `L8' and `D3'. This produces high accuracy because the passwords are always meaningful and are set with template structures (e.g., iloveyou520, password123, abc123456). Meanwhile, neural networks can detect the relationship between characters that PCFG cannot. Thus, we combine the two methods to obtain a more effective one.
### Preprocessing

A password is first encoded into a sequence of units. Each unit has a char and a number. A char stands for a sequence of letters (L), digits (D), special chars (S), or an end character (‘\(\setminus\)n’), and the number stands for the length of the sequence (e.g., $Password123 will be denoted as S1 L8 N3 ‘\(\setminus\)n’). Detailed rules are shown in Table [\[table1\]](#table1).

A table is generated when we preprocess the passwords. We calculate the number of each string’s occurrence. For example, we calculated all the L8 strings in Myspace, and found that “password" occurred 58 times, “iloveyou" occurred 56 times and so on.

|         Data Type          |          Symbols           |
| :------------------------: | :------------------------: |
|          Letters           | ABCDEFGHIJKLMNOPQRSTUVWXYZ |
|           Digits           |          0123456789        |
|       End character        |             \n             |
|       Special Chars        |         otherwise          |

<span id="table1" label="table1">\[table1\]</span>Different string types


![avatar](/img/acenet_2012.png)

Green nodes are hot topics, because the indegree and outdegree of these nodes is very high. This means these nodes are often large, indicating that these topics/fields are developing rapidly. These fields also brought great help to other fields. For example, in the 2012 Artificial Neural Network, SVM, Machine Learning and other fields, these fields have a strong relationship with each other and developed rapidly.

Blue nodes stand for these relatively well-developed topics. They are developed, so the annual dynamics of this field are relatively small, and the sum of indegree and outdegree is relatively small, resulting in a smaller point. Taking Data Compression in 2012 as an example, in the field of information theory, data compression is already a relatively mature research topic. Only a small number of people are focusing on this topic. However, this topic is important to WiFi, Wireless Network.

Red topics have a high indegree and a low outdegree. So this field may be a good and unpopular field of development. Breakthroughs in other topics help developing these topics, such as Weather Forecasting. Such topics can be collectively referred to emerging topics.

The rest nodes are black. These nodes are often niche topics. Such topics are often difficult to define because they may be new-born topics and may develop rapidly in a few years, such as the metaverse in 2012, Or they can be the almost unpopular areas that have been developed before, such as business process management. Therefore, manual analysis is required for these points. 

I used Gephi and javascript to visualize the relationship between different topics

To further study the relationship between these topics, I use gSpan algorithm to find the most frequent subgraphs in the network. To make the algorithm faster, I divide the whole picture to several small parts.

The result shows there are three most frequent modes.

1. One hot node(green node) has strong connection with several not-hot nodes(nodes which are not green).
![avatar](/img/acenet_fre_1.png)

2. Several not-hot nodes(usually 4) have a relatively strong connection with each other.
![avatar](/img/acenet_fre_2.png)

3. Two hot nodes and several not-hot nodes around them.
![avatar](/img/acenet_fre_3.png)

# Conclusion

By analyzing the relationships of these topics and authors, we think:

* The combination of multiple hot topics is not as much as the frequent sub-graphs with a single hot topic as the core and two hot topics as the core. This is different from the previous expectations. The reasons may be as follows: 
1. across multiple There are fewer researchers on hot topics. Most of the hot topics have a huge amount of information, and it is difficult for a scholar to master several hot topics at the same time, which leads to the rare frequent subgraphs with more than three hot areas. 
2. even if there are researchers who span multiple hot topics, the weighting performance between the two topics will be neglected because the number is very small. 
3. the segmentation of the topic of the topic network caused some information loss.
* The probability of a combination of multiple not-hot topics is high. The reason is that there are always a few not-hot topics that are relevant, such as several not-hot topics derived from the same hot field, or several well-developed areas that are gradually merging and forming new research topics. At the same time, the research level of such topics is relatively complete, and it is easier for scholars to master multiple topics at the same time. This also shows that there is a greater possibility of strong links between these not-hot topics.

* In order to better demonstrate the research, we visualize the findings of this paper, as shown below. This picture shows the relationship between the topics of 2012. Among them, the orange points are hot topics(green ones in the previous picture), the green points are new-born topics(red ones in the previous picture), the blue points are mature topics, the black points are isolated topics, the hot topic is on the same plane, and the not-hot topic is on the same plane. The size of the node is similar to the previous picture, indicating the popularity of the topic. In addition to the relationship between different topics, the size of points also includes the development of the same topic in the previous year and next year. In order to show the relationship between the topics, we divide it into small pieces. The red side of the figure shows the relationship between two hot topics, the yellow side indicates the relationship between hot topics and not-hot topics, and the green side indicates the relationship between not-hot topics. From the figure we can see that the red edges of each part are sparse, while the yellow edges of the corresponding areas are denser, while the green edges are very dense. This confirms that the relationship among hot topics is relatively weak, but the relationship with not-hot topics is strong. The relationship between not-hot topics is far stronger than the strength of the relationship between hot topics. We analyze the network constructed by only the unpopular topics (that is, the network constructed by the green node and the green edge), and find that the number of edges whose starting point or ending point is a mature topic occupies 47.42% of the total number of edges. 
![avatar](/img/acenet_conclusion.png)

* Although the current discipline integration is a trend, at least there is little topic integration in the CS field. Most of the CS field is a hot field but most hot topics will not have a strong connection with other hot topics. This is because they are not developed topics. However, in the future, when many topics are developed, there will be a discipline fusion in CS.

# Acknowledge

> [Acemap](https://www.acemap.info/)

> [Implementation of gSpan](https://github.com/betterenvi/gSpan)

> [Visulization Gephi](https://gephi.org/)

> [Visulization Plotly](https://plot.ly/)
