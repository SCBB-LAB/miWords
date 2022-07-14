# miWords

Sentences, Words, Attention: A “Transforming” Aphorism of miRNA Discovery

miRNAs are prime regulatory small RNAs (sRNAs) having ~21 bases length which post-transcriptionally regulate most of the genes and stand critical for most of the processes of eukaryotic cells including their development and specialization. miRNAs can be found in the intronic as well as intergenic regions. Mature miRNAs are derived from longer precursor miRNA molecules (pre-miRNAs) which are double-stranded RNAs (dsRNAs) with terminal hairpin loop.

Here, we present miWords is a novel deep learning method specifically designed for pre-miRNA detection. The model is an attention based genomic language processing transformer and context scoring deep-learning approach to accurately identify pre-miRNAs in plants that can automatically learn suitable features from the raw data, without manual feature engineering.


## Web server

miWords can be used directly from [this](https://scbb.ihbt.res.in/miWords) web server. This server implements trained models and can process both individual sequences or fasta files. The server generates a table deciphering T-Score for every sequence provided.

## Requirements

```
1. Python3.8.1 or higher
2. Numpy
3. keras
4. tensorflow
5. plotly
6. pandas
7. RNAfold (ViennaRNA package download it from here: "https://www.tbi.univie.ac.at/RNA/")
8. python module multiprocessing, Bio, bayesian-optimization 
```

## File description

```
1. M1.sh = Module 1 execution script.
2. program.py = Python script for detecting pre-miRNAs from sequences provided.
3. model.h5 = Trained model transformer part.
4. xgb_model.sav: Trained model XGBoost part.
5. test = fasta sequence.
6. tokenizer_penta.pickle = build tokenizer.
7. reve.py = Python script for sequence preprocessing.
8. hyper_param.py = Python script build model implementing hyperparameter tuning
```

## Output description

pre-miRNA detection module gives output in following format 
```
1. test.txt = Chunks wise probability score of the sequence provided.
```

## Running script

To predict the pre-miRNAs, In parent directory execute following command:
```
sh M1.sh test
```

## Package installation

The latest version of the package can be downloaded from the GitHub [repository](https://github.com/SCBB-LAB/miWords).

## Citation

Citation: Gupta S, Saini V, Kumar R, Shankar R* (2022) Sentences, Words, Attention: A “Transforming” Aphorism of miRNA Discovery. bioRxiv 2022. 
