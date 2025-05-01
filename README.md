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
- Data exploration and cleaning in `data_exploration.ipynb` and `data_cleaning.ipynb` respectively.
- Final dataset: `uniform_excerpts_2.csv`
    - `text`, `text_number` and `label` columns representing the excerpt from the text, corresponding text ID number, and era labels respectively.
    - Includes texts ranging from 1400s to 1900s
    - Random sampled old texts to achieve a uniform distribution of 6,000 total entries, 1,000 entries per era.
    - Filter out intros and outros from modern day.
    - Excerpts standardized to 400-600 characters long
    - Remove text with apparent OCR issues if there were too many unrecognizable characters.
    - Filter out any text with multiple authors, a translator, and original language not in English.
- Final dataset example entries given below:
![](images/data_screenshot.png)

## Tools
- Tools to train and explore diachronic word embeddings from Big Historical Data - https://github.com/Living-with-machines/DiachronicEmb-BigHistData

## Papers
- Temporal Language Models for the Disclosure of Historical Text - https://repository.ubn.ru.nl/bitstream/handle/2066/228230/228230.pdf 
- Diachronic Text Evaluation - https://aclanthology.org/S15-2147/ (Abstract claims to do essentially what we are trying to except w/ newspapers 1700-2010)

## Models

### Naive-Bayes

### BERT

### DistilBERT
**Description**
This model is built on the lightweight and efficient DistilBERT transformer architecture, the model leverages contextual embeddings to learn stylistic and lexical patterns across time. DistilBERT is smaller and faster than BERT, which was pretrained on the same corpus in a self-supervised fashion, using the BERT base model as a teacher. We opted to use the uncased version of the model, in which upper and lower case is treated equally. The reason we used DistilBERT due to its speed and performance retentions. DistilBERT is 60% faster than BERT retains 97% of BERT performance, which was important as one training iteration using a CURC job took ~1 hour.

**Methods**
We fine-tuned the distilbert-base-uncased model on out dataset of ~6,000 excerpts. Texts were tokenized using DistilBertTokenizerFast with padding/truncation to a max length of 256 tokens. The model was trained using an 80/10/10 train/val/test split with a learning rate of 1e-4, weight decay of 0.05, and trained for 6 epochs using cross-entropy loss. The below training an validation loss is plotted, showing overfitting on our training data. Despite attempts to lower learning rate and increase weight-decay, we still saw this overfitting with suffered performance. 
![](images/DistilBERT_training_loss.png)

**Results**
The DistilBERT model achieved a test accuracy of 0.79, outperforming baseline and Naive Bayes approaches. 
![](images/DistilBERT_acc.png)
It performed especially well in classifying excerpts from the 1400s–1500s and the 1900s. However, it showed weaker performance distinguishing between the 1600s, 1700s, and 1800s—likely due to the same reasons discussed during Naive Bayes.
![](images/DistilBERT_conf_matrix.png)
Overall, we were pleased with the results from DistilBERT, but feel slight tweaks could fix the problem of overfitting and lead to better accuracy.

## Conclusion
