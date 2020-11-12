# Movie Genre Classification based on Posters

A person can quickly grasp a movie's genre(s) from its poster.  
It can be assumed that some simple attributes of a poster are correlated with its genres. Therefore, we will extract visual features based on colors and structural cues from poster images and use them for poster classification into genres.  
Furthermore, the visual features are strongly correlated with each other, to form an image.  
This leads to a structured learning task. This problem is not a binary classification task, nor a conventional multiclass classification task. Actually, a movie may belong to several genres, thus this task is a multi-label classification task.  
To solve this task, we will use Conditional Random Field (CRF), that has been adapted to image classification (rather than segmentation).  
During our experiments, we tried several feature descriptors, but eventually, used the most low-level visual feature there is, a simple HSV (Hue, Saturation, Value) pixel tensor.  
The dataset we used contains 19,000 posters classified into 8 different genres. ([IMDB API](https://www.imdb.com/interfaces/))  
Our results reveal that there is no strong benefit from structured models for this task.


## Data Preprocessing:
All preprocessing functions were implemented with usage of basic libraries. (numpy, pandas, re)
To read images, we used imageio library, and to manipulate it (resize, transform to HSV) we used skimage).
## Baseline:
We used sklearn implementation of Naive Bayes, and used sklearn evaluation methods (KFold to cross-validate, f1_score)
Implemented collection of results from each different model (OneVsRest), to handle multilabel task.
## Basic ,Advanced and Creative part:
In the Aux functions:
- There are auxiliary function for this part.
In the Cluster and ClusterGraph classes part:
- The ClusterGraph class represents the cluster graph on which we run the loopy belief propagation algorithm (function LBP)
- and the gradient ascent algorithm (function gradient_ascent).
- The Cluster class represents a cluster in the cluster graph.
In the Experiments part:
- In this part we run inference of the basic, advanced and the creative parts on the data and calculate the f1 score for each one.