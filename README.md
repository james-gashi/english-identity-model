# english-identity-model
A model that can identify the date in which text was written based on the style of the text.

## Problem Statement
Language is dynamic, evolving over time with shifts in vocabulary, syntax, and style. These changes are influenced by cultural, social, and historical factors, making the study of linguistic evolution an intriguing area for research. Understanding when a piece of text was likely written can provide valuable insights into literary trends, historical contexts, and cultural analysis.  Our project aims to develop a machine learning model capable of estimating the date range of an English text based solely on its linguistic features. By analyzing stylistic and linguistic patterns, such as vocabulary trends, morphosyntax, and phrase frequencies, our model will learn to associate textual characteristics with specific historical periods, ultimately aiming to classify a given text/excerpt with a date range. 

## Data
Data sourced from the free ebook source [Project Gutenburg](https://www.gutenberg.org/)
- Link to download zip and metadata for texts found [here.](https://www.gutenberg.org/cache/epub/feeds/)
    - Texts: txt-files.tar.zip
    - Metadata: pg_catalog.csv
- Retrieved all available texts: 75,627
- Data cleaning exploration and cleaning in `data_exploration.ipynb` and `data_cleaning.ipynb` respectively.
- Final dataset: `uniform_excerpts_2.csv`
    - Random sampling old texts for uniform distribution
    - Avoids problems with intro’s prefaces from modern day
    - Excerpts 400-600 chars long
    - Remove text with apparent OCR issues if too many unrecognizable chars
    - Filter out any text that has multiple authors, translator, original language not in English
    - Includes texts ranging from 1400s to 1900s
    - 6,000 total entries

## Tools
- Tools to train and explore diachronic word embeddings from Big Historical Data - https://github.com/Living-with-machines/DiachronicEmb-BigHistData

## Papers
- Temporal Language Models for the Disclosure of Historical Text - https://repository.ubn.ru.nl/bitstream/handle/2066/228230/228230.pdf 
- Diachronic Text Evaluation - https://aclanthology.org/S15-2147/ (Abstract claims to do essentially what we are trying to except w/ newspapers 1700-2010)

## Models

### Naive-Bayes
This model was built using nltk's naive bayes classifier. In this model we manually added features we deemed likely to be important to the model. We had a training, validation, and test split. We would train our model on the training data, and test its performance on the unseen validation data. We did a loop of tweaking the features and testing the validaion accuracy to find the set of features that caused the model to perform its best. We then tested the final model on the testing dataset. We created lists of words that were only found in certain eras of english texts and used those as features in the model. This bag of words approach did really well and got to about a .45 accuracy, well above our baseline of .17. We also tried a bigram model. The bigram model did exceptionally well and had about a .7 accuracy. The naive bayes was especially helpful because its a white box like model, and showed us what features are important for the next steps of our project. We saw the model did really well at classifying texts from the 1400s, 1500s, and 1900s, and was most confused between the 16,17, and 1800s texts. This is likely because vocabulary didn't change that much during those eras. It was also helpful because it ran way faster than even the DistilBERT model. Training the bigram and testing it took less than 30 seconds on our personal machines, and even faster without using bigram features. Some other features we tried to use were sentence length and word length, however these features turned out not to be helpful at all. The code/results can be reproduced by simply running all the cells in the naive_bayes_model.ipynb jupyter notebook. The notebook depends on the nltk, seaborn, matplotlib, pandas, collections and numpy libraries. The data used to train the model is located in the data folder, the relative path should already be correct in the notebook. The data was preprocessed from the project gutenberg dataset, and the final processed version of our dataset is the "uniform_excerpts_2.csv". That csv file should be ready to use and is the fully cleaned version of the dataset that we used for the project. The team member in charge of this section of the codebase was Zach Conroy.

### BERT

### DistilBERT
Description
Methods
Results
## Conclusion
