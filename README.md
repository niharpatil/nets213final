# INSTRUCTIONS FOR HITS
## Phrase HIT
For each listed phrase, say which topic the phrase fits best into. In addition, say how well that phrase fits, and how many people you think know that topic.

## Survey HIT
Answer each of the questions that are listed. If you don't feel comfortable saying yes, then you can just leave the question blank. 
You must answer the last question.

# Topic Aggregation/Quality Control (From HIT 1 to HIT 3)
The idea of this project is to first aggregate the knowledge of Turkers to see what they have insight on, and then make predictions/bets based on their responses to questions in those topics. This first task consists of aggregating the knowledge of Turkers into a workable format. This task consists of two HITs and multiple coding portions. 

The first HIT (HIT 1) asks Turkers to list up to 4 words that they are knowledgeable in, ordered from most knowledgeable to least knowledgeable. We are particular in this readme about the distinction between “words” and “topics. “Words” is what the Turkers submitted as their answers to HIT 1, while “topics” are the high level topics that they represent. This distinction is relevant, as potentially there could be some Turkers who list the word “soccer” and some who list the word “futbol”. These represent the same high level topic of American soccer/European futbol, but the words used to describe them are different. 

Back to HIT 1: we compile the Turker responses into a list of unique words submitted by the Turkers, where each unique word has some notion of importance/relevance based on how many Turkers submitted it and where it fell in their list of 4 words. This is the first coding portion of the quality control module, which is found in the src folder as word_aggregation.

We now need to determine which words listed represent the same high level topic. That is, turkers could list “soccer” and “futbol” and we need to verify that those are the same topic. 

This will be done in two steps: using word2Vec and a second HIT (HIT 2). 

# Quality Control of Topics (HIT 2)
We will use word2Vec on our words from the first HIT to get some idea of their semantic meaning. We will then use k-means to cluster these into some amount of topics. Using this, we can hand label the topics. All of this code is present in the word_topic_clustering file. The second HIT is for placing the words that we cannot describe with word2Vec into topics. This can occur in 2 main cases:
  - When the input has multiple words
  - When the input has a far distance from any topic centroid
We then use the second hit to place these HITS into a topic. The code for the using the output of this HIT is in the source folder.

# Betting Based on Knowledge (Aggregation of votes) (HIT 3)

Now we have a list of topics with their respective weights from HIT 1, HIT 2, and the corresponding code. We will now look at the 6 topics that Turkers are most knowledgeable about, using the metric of knowledge that was described before. In each of these 6 topics, we will manually find/write a single question that relates to current events. These questions will be prediction based, that is we will ask Turkers to make a prediction about some upcoming event. The idea is that we can place bets on these events based on our aggregated crowd answers. For example, if one of the top topics is soccer, we could ask “Is Liverpool going to beat Barcelona?”. We will most likely only ask binary questions, as aggregation techniques are most successful when applied to binary questions.

HIT 3 consists of actually asking these 6 questions to Turkers and getting back the results. We will design the HIT as described in the mockup sections. The Turkers will be able to answer as many of the 6 questions as they want, but they must answer at least one. In addition to giving their own prediction, we will ask Turkers to say what they predict other people will say for the same question. Both of these metrics are used in the next step for aggregating the crowd answers. The input/output of this HIT can be found [here](https://github.com/niharpatil/nets213final/tree/master/data).

We now aggregate the answers of the crowd to achieve our own predictions for each of the 6 events. This is the next coding section, found in the src folder as hit3_aggregation. In this file, we perform multiple different aggregation techniques. This includes majority voted, the EM algorithm, surprising majority, and potentially others. Each of these methods takes in the output of HIT 3, and returns a prediction for each of 6 events present in HIT 3. We will compare and contrast the results of these methods (all present in betting_aggregation in src folder), and measure their performance once the future events asked about in HIT 3 complete. For the future we will add more styles of aggregation to the betting folder.
