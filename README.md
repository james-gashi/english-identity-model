# english-identity-model
A model that can identify the date in which text was written based on the style of the text.

## Problem Statement
Language is dynamic, evolving over time with shifts in vocabulary, syntax, and style. These changes are influenced by cultural, social, and historical factors, making the study of linguistic evolution an intriguing area for research. Understanding when a piece of text was likely written can provide valuable insights into literary trends, historical contexts, and cultural analysis.  Our project aims to develop a machine learning model capable of estimating the date range of an English text based solely on its linguistic features. By analyzing stylistic and linguistic patterns, such as vocabulary trends, morphosyntax, and phrase frequencies, our model will learn to associate textual characteristics with specific historical periods, ultimately aiming to classify a given text/excerpt with a date range. 

## Data
Data sourced from the free ebook source [Project Gutenburg](https://www.gutenberg.org/)
- Link to download zip and metadata for texts found [here.](https://www.gutenberg.org/cache/epub/feeds/)
- Retrieved all available texts:  75,627
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
