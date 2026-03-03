Developement in NLP is mostly better text representation, so computer can understand the meaning of the text.  

### BoW representations - Bag of Words 
We don't know the order-context -> words are comptely indpendent by meaning
We need lemamatization and stemming to reduce the vector dimesnionality, lowercasing, removing stop words (the, and, a, an...)
- Bin Binary representation (long vector, 1 if word is present, 0 otherwise)
- TF - Term Frequency (how many times a word appears in a document)
- TF-IDF - Term Frequency-Inverse Document Frequency (weights words based on their frequency in the document and their rarity across all documents)
TF-IDF formula:
TF-IDF(w, d) = TF(w, d) * log(N / DF(w))
Where:
    - TF(w, d) is the term frequency of word w in document d
    - N is the total number of documents
    - DF(w) is the number of documents containing word w
Implementation: tfifd vectiorizer - sckirt-learn library    

It's useful to create ngrams (sequences of n words) to capture some context and word order, like treating New York as a single token instead of two separate words.