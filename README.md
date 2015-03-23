Wikipedia/PNAS Data
===================

I use the Wiki and PNAS data from Data Access Layer(DAL) https://github.com/cioc/DAL, which is a library that makes it easy to use the datasets. 

For this project, I work with the Wikipedia and PNAS dataset, which are both text-based APIs containing many articles.

The following bit of simple code to show how to extract and display them.

```python
from DAL import create
#create a handle to the Wiki/PNAS dataset
corpus=DAL.create(dataset_name:str)
＃creates the articles DAL of the given type. Either ​"wikipedia"​or ​"pnas"​are supported.
corpus.all_articles()->list(int)
#returns a list of all article IDs.
corpus.byid(index:int)->dict(title:str,body:str)
#returns the given article in the corpus.
corpus.iter()->list(dict(title:str,body:str))
#iterates through all articles in the corpus.
```

Clean PNAS data
===============

I come up with parser to extract the vocabulary from the articles stored in XML format. Then I exclude extremely popular and rare words to keep the vocabulary reasonably small and I save it as pnasvocab.txt.

Online LDA on PNAS
==================

I train Latent Dirichlet Allocation(LDA) on the PNAS dataset previous vocabulary and parser. Taking Wikipedia articles as the test documents, I use the final estimated topics to compute the posterior and find topically similar articls. Finally, I print out the most prominent words in each topics.

