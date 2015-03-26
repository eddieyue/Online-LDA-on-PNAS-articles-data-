Wikipedia/PNAS Data
===================

I use the Wiki and PNAS data from Data Access Layer(DAL) https://github.com/cioc/DAL, which is a library that makes it easy to use the datasets. 

For this project, I work with the Wikipedia and PNAS dataset, which are both text-based APIs containing many articles.

The following bit of simple code to show how to extract and display them.

```python
from DAL import create
# Create a handle to the Wiki/PNAS dataset, ither ​"wikipedia"​or ​"pnas"​are supported.
corpus=DAL.create(dataset_name:str)

# For example, loading PNAS articles in DAL
corpus=DAL.create('pnas')

# Returns a list of all article IDs
corpus.all_articles()

# Returns the given article in the corpus
corpus.byid(index:int)->dict(title:str,body:str)

# Iterates through all articles in the corpus
corpus.iter()->list(dict(title:str,body:str))
```

Clean PNAS data
===============

I come up with parser to extract the vocabulary from the articles stored in XML format. Then I exclude extremely popular and rare words to keep the vocabulary reasonably small and I save the vocabulary as pnasvocab.txt and the whole process as PNAS parser and vocabulary.ipynb.

Online LDA on PNAS
==================

I train Latent Dirichlet Allocation(LDA) on the PNAS dataset previous vocabulary and parser. Taking Wikipedia articles as the test documents, I use the final estimated topics to compute the posterior and find topically similar articls. Finally, I print out the most prominent words in each topics and I save the whole process as Online LDA on PNAS.ipynb. 

