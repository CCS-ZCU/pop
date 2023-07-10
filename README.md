#  pop

This repository serves as a supplementary material for the article "**‘The more populism types you know, the better political scientist you are?’ Machine-learning based meta-analysis of populism types in the political science literature**", accepted for publication in * Journal of Contemporary European Studies*. It contains scripts, overview data and figures. The scripts are in Python 3 programming language and have a form of Jupyter notebooks. All our analyses aim at being fully reproducible and we invite other scholars to reuse our code for their analyses. However, since the input dataset of PDFs is protected by copy rights, we cannot give you access to it.

---
## Authors
* Vladimír Naxera [![](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0001-5945-7193)
* Vojtěch Kaše [![](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0002-6601-1605)
* Ondřej Stulík [![](https://orcid.org/sites/default/files/images/orcid_16x16.png)](https://orcid.org/0000-0003-3334-3918)


## License
CC-BY-SA 4.0, see attached LICENCE.md

---
# Getting started

* download or clone the repository
* obtain access to the dataset of PDF files (we cannot make them available by default) and put them to `data/large_data/articles` folder
* open and run the Jupyter notebook scripts one by one according to the numbering and description below:
  * **1_metadata_exploration.ipynb**: collects metadata for individual articles and maps them on the PDF files from `data/large_data/articles`
  * **2_textblocks_extraction.ipynb**: extracts text layer from the PDFs in `data/large_data/articles` and save them as pickle files in `data/large_data/articles_textblocks`
  * **3_filteredtext_extraction.ipynb**: combines text passages from textblocks into raw full text files in `data/large_data/articles_filteredtexts` 
  * **4_exploring_trends.ipynb**: explores varies metadata trends from `data/article_metadata.json`
  * **5_nlp_processing.ipynb**: applies NLP pipeline to textual data and extracts lemmatized text to `data/large_data/articles_lemmata_min`
  * **6_generating_pop_concs.ipynb**: identifies all instances of "populism" or "populist" or "populists" or "populisms" using `"^populis|\spopulis"` regular expression and uses them to extract concordances and sentences containing the `populis*` term.
  * **7_exploring_concs+sents.ipynb**: generates labeled concordances by mapping predefined populism types (right-wing, left-wing, authoritatian) on the concordance data and save them to `data/concs_labeled_min.pickle`
  * **8_conc_classification.ipynb**: uses the labeled concordances to train a document classification model using *Multinomial Logistic Regression* (other document classification algorithms are explored here, including *Multinomial Naive Bayes*, *Random Forests*, and *Extremely Randomized Trees*). The results of the classification task are introduced using confusion matrices and network graphs. 
  * **9_wmd.ipynb**: calculates *Word Mover Distance* (WMD) between all pairs of labeled concordances and save the results into `data/large_data/distance_matrix_min.pickle`.
  * **10_wmd_analysis.ipynb**: explores the WMD data from `data/large_data/distance_matrix_min.pickle` by generating scatter plot figures by reprojecting the pairwise distances into 2D space using *T-distributed Stochastic Neighbor Embedding* (TSNE). 

---
# Software
* Python 3
* Jupyter notebooks app/JupyterLab/JupyterHub
* Python 3 additional libraries listed in `requirements.txt`