# SentiWE 
This is an open source implementation of our framework to obtain cross-lingual sentiment word embeddings by unsupervised self-learning iterations.
The package includes a script to build cross-lingual sentiment word embeddings as described in the paper, as well as evaluation tools in bilingual lexicon construction and cross-lingual sentiment analysis.
# Requirements
* Python 3
* Numpy
* SciPy
* CuPy (optional, only required for CUDA support)
# Usage
In order to build your own cross-lingual sentiment word embeddings, you should first train monolingual word embeddings for each language using your favorite tool (e.g. [word2vec](https://github.com/tmikolov/word2vec) or [fasttext](https://github.com/facebookresearch/fastText)) and then map them to a common space with our software as described below. Having done that, you can evaluate the resulting cross-lingual sentiment embeddings using our included tools as discussed next.
## Mapping
You can generate the cross-lingual sentiment word embeddings by our SentiWE model with the code as follows:
```
python UCL-SWE.py
```
You can also obtain the cross-lingualword embeddings by [VecMap](https://github.com/lishiqimagic/vecmap) model with the code as follows:
```
python VecMap.py
```
## Evaluation
### 1. Bilingual Lexicon Construction
The CSLS retrieval algorithm was used to select the target language words with the nearest CSLS value for each word in the source language as translation words to construct a bilingual dictionary. Then, the MUSE bilingual dictionaries provided by Facebbook were used as the benchmark to compare the bilingual dictionaries constructed by the model and calculate the accuracy:
```
python WordSimilarity.py
```
### 2. Cross-lingual Sentiment Analysis
Based on the cross-lingual word embeddings generated by the model, the annotated text of the source language is used to train the sentiment classification model and the emotion polarity of the target language is predicted. Accuracy, Precision and F1 Measure are adopted as evaluation indicators:
```
python CLSA_SVM.py
```
