# Goal
The goal of our project is to explore how good Turkers are at predicting events within categories that they think they are very knowledgeable about. 

# Project Components

Our project comprises of 6 main stages. 

## Stage 1: 3 points
First, we ask Turkers what categories that they are knowledgeable about. We do not preselect categories and support raw text inputs. We will try to manually consolidate categories here to the best of our ability. Then, we turn back to Turkers.

## Stage 2: 4 points
Using Word2Vec (or another algorithm that helps us understand category-title similarity), we find words submitted by Turkers that have high similarity scores provided by the algorithm. We then again use Turkers to validate or invalidate which categories are similar or the same. For example, if two Turkers independently submitted "Soccer" and "Futbōl", then Turkers should be able to identify that these two words represent the same concept. 

## Stage 3: 2 points
Once we have a large enough set of categories that a reasonable number of Turkers feel that they are knowledgeable about, we will research events that are currently occuring in those categories that have limited outcomes. We will select for events that occur within a timeframe of 1-5 weeks so that we can actually validate Turker's predictions. For example, within the category "Soccer", we might generate the event "Liverpool wins world championship" with the options "Yes" and "No." 

## Stage 4: 2 points
We send out a HIT to many Turkers with the events and collect data about how Turkers predict which outcomes will occur across the different categories. 

## Stage 5: 3 points
We create aggregate predictions based on Turkers' individual predicitions using the surprising majority, weighted majority, and the majority vote algorithms.

## Stage 6: 4 points
We wait until the events have all occured and record the true outcomes of the events. Given the truth of what actually happened, we'll be able to assess how aggregrating crowd wisdom can provide prediction power for events within certain categories. 