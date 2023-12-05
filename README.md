# single-cell-transcriptomics-study
Programatically prepare the data matrix for a single cell transcriptomics study: GSE137829
# Clean and Export Gene Expression Data

This script processes raw gene expression text files and exports cleaned CSV versions.

## Usage

The script expects raw text files (.txt) containing gene expression data in the input directory. It will:

- Read in each text file
- Clean the DataFrame
    - Replace column periods with underscores
    - Set index name to 'Gene'  
    - Set column name to 'Cell ID'
- Export cleaned data to a CSV file

## Code Overview

- Use os.listdir() to get list of .txt files  
- Loop through each file
- Read in file using pandas
- Clean DataFrame
- Construct output CSV filename
- Export DataFrame to CSV

## Input File Format

Input files must be tab-delimited text files with:  

- Gene names in the first column
- Cell expression values in following columns 
- No header row

## Output  

The script exports cleaned CSV versions of the input files.

- Replaces periods in column names with underscores
- Adds 'Gene' as index name  
- Adds 'Cell ID' as column name
- Removes .txt from file name and adds .csv extension

## Requirements

- pandas  
- os


# Mapping Probe IDs to HGNC IDs

## Overview

This script maps probe IDs from a gene expression data matrix to HGNC gene IDs using an annotation mapping file and the MyGene.Info API.

## Input Files  

- GSE35609.xlsx - Gene expression data matrix with probe IDs as row index
- GPL6885-11608.txt - Annotation mapping file with Probe Set ID, Gene Symbol and Entrez Gene ID columns

## Steps  

1. Read in data matrix and mapping file as Pandas DataFrames
2. Keep only needed columns from mapping file  
3. Use MyGene.Info API to retrieve HGNC IDs for Entrez Gene IDs
4. Merge HGNC IDs with mapping DataFrame
5. Export mapping file as CSV
6. Create dict mapping Probe IDs to HGNC IDs
7. Map data matrix index to HGNC IDs using mapping dict 
8. Export updated data matrix as CSV

## Output Files  

- probe_to_hgnc_mapping.csv - Mapping file with Probe ID, Gene Symbol, Entrez ID and HGNC ID
- data_matrix_with_hgnc_ids.csv - Data matrix indexed by HGNC IDs  

## Requirements

- Pandas 
- mygene

## Usage  

```
python map_probe_to_hgnc.py
```

Run script to generate output files.
