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
