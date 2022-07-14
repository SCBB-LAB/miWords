# miWords

Sentences, Words, Attention: A “Transforming” Aphorism of miRNA Discovery

miRNAs are prime regulatory small RNAs (sRNAs) having ~21 bases length which post-transcriptionally regulate most of the genes and stand critical for most of the processes of eukaryotic cells including their development and specialization. miRNAs can be found in the intronic as well as intergenic regions. Mature miRNAs are derived from longer precursor miRNA molecules (pre-miRNAs) which are double-stranded RNAs (dsRNAs) with terminal hairpin loop.
miWords is a novel deep learning method specifically designed for pre-miRNA detection. The model is an attention based genomic language processing transformer and context scoring deep-learning approach to accurately identify pre-miRNAs in plants that can automatically learn suitable features from the raw data, without manual feature engineering.


## Web server

miWords can be used directly from [this](https://scbb.ihbt.res.in/miWords) web server. This server implements trained models and can process both individual sequences or fasta files. The server generates a table deciphering T-Score for every sequence provided.

## Package installation

The latest version of the package can be downloaded from the GitHub [repository](https://github.com/SCBB-LAB/miWords).


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
