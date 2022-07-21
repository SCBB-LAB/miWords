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
8. python module multiprocessing, Bio, bayesian-optimization, RNA
9. bedops
10. Bedtools
```

## File description

```
1. M1.sh = Module 1 execution script. (Sequence having length less than 400 base)
2. M2.sh = Module 2 execution script. (Sequence having length more than 400 base)
3. program.py = Python script for detecting pre-miRNAs from sequences provided.
4. miWords.h5 = Trained model transformer part.
5. miWords.sav = Trained model XGBoost part.
6. test = dummy fasta sequence for Module 1.
7. t2 = dummy fasta sequence for Module 2.
8. tokenizer_penta.pickle = build tokenizer.
9. reve.py = Python script for sequence preprocessing.
10. hyper_param.py = Python script build model implementing hyperparameter tuning
11. file_format_GPU = file format of input for script predict_GPU.py. file containing seq_id, sequence (sequence length of >= 200 base), and dot bracket ("(">"M", ".">"O", ")">"N"). All in one line separated by tab for a single instance.
12. score.h5 = scoring profile CNN trained model (Download form (https://scbb.ihbt.res.in/miWords/score.h5)
```

## To build model implementing hyperparameter tuning

```
python3 hyper_param.py file_for_tuning

file_for_tuning: file containing label (0/1), sequence (sequence containing pre-miRNAs and non-pre-miRNAs), and dot bracket ("(">"M", ".">"O", ")">"N"). All in one line separated by tab for a single instance. 
```

## Running script

To detect the pre-miRNAs, In parent directory execute following command:
```
sh M1.sh test (Sequence having length less than 400 base module 1)
sh M2.sh t2 (Sequence having length more than 400 base module 2)

To line plot, switch to directory name "plot/merge" and execute following command:

python3 RPM/make-plot.py seq1.csv (filename) (generated plots are interactive)
```

## Output description

pre-miRNA detection module gives output in following format 
```
1. seq.txt = Chunks wise probability score of the sequence provided.
2. plot = folder containing "csv" files to construct line plot.
3. merge = folder containing "csv" files to construct line plot overlapping sequence.
4. param.txt = Hyparameters for sequence side of bi-modal
5. merge.fa = output of module 2 (Sequence, Struture Triplet, Position wise T-Score)
6. test.bed = output of module 2 (BED6 format) (Required for RPM module)
6. sequence_feature.tsv = Classification result of the sequence provided.
```

## RPM module

If provided with read data(sRNA-seq):

## Usage

```
To convert SAM to BED6 format
sam2bed <1.sam |cut -f1-6 >1.bed

python3 program.py <fasta file> <Output from Module 2> <read data in BED6 format>
Example: python3 program.py test test.bed 1.bed
```

## Output description

```
1. miWords_rpm.py = Python script for RPM module.
2. 1.bed = read alignment data in BED6 format (converted from SAM).
3. test = dummy fasta sequence utilized for Module 2
4. test.bed = output from module 2 (BED6 format)
5. test_rpm.txt = Final result (ID, Start, End, Strand, Sequence, Struture Triplet)
6. rpm.h5 = rpm profile CNN trained model (Download form (https://scbb.ihbt.res.in/miWords/rpm.h5)

To plot:
python3 RPM/make-plot_rpm.py seq1.csv (filename) (generated plots are interactive)
```

## Citation

Citation: Gupta S, Saini V, Kumar R, Shankar R* (2022) Sentences, Words, Attention: A “Transforming” Aphorism of miRNA Discovery. bioRxiv 2022. https://www.biorxiv.org/content/10.1101/2022.07.14.500029v1
