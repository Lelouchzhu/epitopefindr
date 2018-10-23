# EpitopeFinder: Minimal Overlaps from BLAST Alignments 
Version: 0.2.0  
Date: October 22, 2018 
Concept: Ben Larman, Daniel Monaco, Brandon Sie  
Author: Brandon Sie  (contact: brandonsie at gmail)  

# Pipeline Overview: 
The purpose of this tool is to describe the alignments among a set of peptide sequences by reporting the overlaps of each peptide's alignments to other peptides in the set. One can imagine inputting a list of peptides enriched by immunoprecipitation to identify corresponding epitopes. 

This script takes a .fasta file listing peptide sequences of interest and calls BLASTp from within R to identify alignments among these peptides. Each peptide's alignments to other peptides are then simplified to the minimal number of "non overlapping" intervals* of the index peptide that represent all alignments to other peptides reported by BLAST. (*By default, each interval must be at least 7 amino acids long, and two intervals are considered NOT overlapping if they share 6 or fewer amino acids). After the minimal overlaps are identified for each peptide, these overlaps are gathered into aligning groups based on the initial BLAST. For each group, a multiple sequence alignment logo (motif) is generated to represent the collective sequence. Additionally, a spreadsheet is written to list the final trimmed amino acid sequences and some metadata. 

# Setup:
1. Install [R (version 3.4.2+)](https://www.r-project.org/).  
2. Install [BLAST+ (version 2.7.1+)](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download).
3. Install the following R packages from CRAN: `tools`, `data.table`, `magrittr`, `seqinr`, `stringr`, `pdftools`, `readr`, `microseq`.  
4. Install the following R packages from Bioconductor: `rBLAST`, `EBImage`, `msa`.  
5. Clone this GitHub repo. Source `/epitope_script/`. 
6. Call `epitopeFinder(proj.id = [path to your input fasta file])` Output data will be written to `/epitope_script/../output/`.

----------------------------------------------------------------------
# Changelog
* 2018-10-23 (Version 0.2.1): Output directory bugfixes.
* 2018-10-22 (Version 0.2.0): Github version tracking begins. Vectorized some operations to get rid of for loops.
----------------------------------------------------------------------
