# Gaussian_LDA
Implementation of the paper - <a href="http://rajarshd.github.io/papers/acl2015.pdf">"Gaussian LDA for Topic Models with Word Embeddings"</a>

### Data Format

* Embedding file: Each line of the file should contain the embedding (dense vector representation) for a word. Each vector should have the same dimension and each dimension should be space separated. The experiments were carried with word2vec embeddings trained on an English Wikipedia dataset. However our model is agnostic to the choice of word embedding procedure and you could use any embeddings (for example trained <a href="http://nlp.stanford.edu/projects/glove/">GLove vectors</a>)
* Corpus train/test files: Here each line is a document with the words mapped as integers. The integer index of the word in your vocabulary should be equal to the position (line_number) of the word embedding in the embedding file. Please take care of 0-indexing.


### Create Embeded Vector
Suppose that you have located [glove pretrained vector file](https://nlp.stanford.edu/projects/glove/) in the parent directory.

```
mkdir vectors
python2 prepare_vectors.py ../glove/glove.6B.50d.txt ./data/20_news/vocab.txt ./vectors/vectors_news.50.txt
python2 prepare_vectors.py ../glove/glove.6B.50d.txt ./data/nips/vocab.txt ./vectors/vectors_nips.50.txt
```

### Running the script
My Environment:  Java SE Development Kit 10.0.2
Run the demonstration corpus (20_news and nips).

```
mkdir bin
./run_gaussian_lda.sh -n 10 -c data/20_news/corpus.train -i vectors/vectors_news.50.txt -d 50 -k 20
./run_gaussian_lda.sh -n 10 -c data/nips/corpus.train -i vectors/vectors_nips.50.txt -d 50 -k 20
```

### Looking the results

```
python2 top_nwords.py data/nips/corpus.train output/D50/I30/K30/GLDA/Jul_26_14_36/table_assignments.txt 30 data/nips/vocab.txt >> topic_topn.txt
```

Citation
```
@InProceedings{das-zaheer-dyer:2015,
  author    = {Das, Rajarshi  and  Zaheer, Manzil  and  Dyer, Chris},
  title     = {Gaussian LDA for Topic Models with Word Embeddings},
  booktitle = {Proceedings of the 53rd Annual Meeting of the Association for Computational Linguistics and the 7th International Joint Conference on Natural Language Processing (Volume 1: Long Papers)},
  publisher = {Association for Computational Linguistics},
  url       = {http://www.aclweb.org/anthology/P15-1077}
}
```





