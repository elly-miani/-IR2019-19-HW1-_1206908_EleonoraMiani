# [IR2019-19-HW1]_1206908_EleonoraMiani

All'interno della repository si trovano:
- Il file `[IR2019-19-HW1]_1206908_EleonoraMiani_Notebook.ipynb`, che contiene i **risultati sperimentali** e i
relativi **plot**, sia complessivi di ciascuna run che suddivisi per ciascun topic.
Vi si trova inoltre il codice usato per eseguire i **test ANOVA one-way** e di **Tukey**, con i relativi risultati statistici.
- Una cartella `Evaluation` ulteriormente suddivisa in base ai quattro sistemi utilizzati. Per ciascuno di questi vi sarà un file `.res` contenente i **file delle run**, un file `.eval` contenente i **risultati della valutazione**, e un file `.csv` che viene utilizzato dallo Jupyter Notebook per importare i dati ottenuti.

## Note aggiuntive sul sistema di IR

L'homework è stato svolto utilizzando il sistema di reperimento *Terrier*, e la collezione di documenti *TREC7*.

I comandi utilizzati sono i seguenti:

##### Per creare l'indice:

```
# creates /etc/collection.spec, that specifies which documents belong to the collection
$ sh bin/trec_setup.sh /Users/ellymiani/Desktop/HW1_ReI/TIPSTER/

# to begin indexing. configurations must be made on /etc/terrier.properties
# the index will be created in var/index
$ sh bin/trec_terrier.sh -i

# displays the number of documents, number of tokens, number of terms
$ bin/trec_terrier.sh --printstats
```

##### Per eseguire la run:


```
# -r makes a batch retrieval run
$ bin/trec_terrier.sh -r
```

##### Per calcolare le misure di valutazione:
```
# -e evaluates the results
$ bin/trec_terrier.sh -e -p
```

##### Le run eseguite, nell'ordine, sono le seguenti:

```
# prima run: Stoplist, PorterStemmer, BM25
termpipelines=Stopwords,PorterStemmer
trec.model=BM25
```
```
# seconda run: Stoplist, PorterStemmer, TF*IDF
termpipelines=Stopwords,PorterStemmer
trec.model=TF_IDF
```
```
# terza run: no Stoplist, PorterStemmer, BM25
termpipelines=PorterStemmer
trec.model=BM25
```
```
# quarta run: no Stoplist, No stemmer, TF*IDF
termpipelines=
trec.model=TF_IDF
```
