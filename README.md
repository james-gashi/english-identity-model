# english-identity-model
A model that can identify the date in which text was written based on the style of the text.

## Data
- Data sourced from the free ebook source [Project Gutenburg](https://www.gutenberg.org/). Data includes text from prior to 1919. Google cloud link - https://console.cloud.google.com/storage/browser/deepmind-gutenberg;tab=objects?invt=AbuZ8A&prefix=&forceOnObjectsSortingFiltering=false
- British Library dataset, predominately 18th-19th century https://huggingface.co/datasets/TheBritishLibrary/blbooks
- Specifically Old English https://www.kaggle.com/datasets/alejopaullier/the-old-english-texts/data
- Corpus of Historical American English
- Middle English https://huggingface.co/datasets/PleIAs/Middle-English-PD

## Tools
- Tools to train and explore diachronic word embeddings from Big Historical Data - https://github.com/Living-with-machines/DiachronicEmb-BigHistData

## Papers
- Temporal Language Models for the Disclosure of Historical Text - https://repository.ubn.ru.nl/bitstream/handle/2066/228230/228230.pdf 
- Diachronic Text Evaluation - https://aclanthology.org/S15-2147/ (Abstract claims to do essentially what we are trying to except w/ newspapers 1700-2010)
