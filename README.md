# etl-gphl-sequencing-alert

**_TODO_** This README needs work. And we should make sure all our ETL scripts
have the same README format.

Repo containing the Epi/HAI ETL for a  alert file uploaded to the raw Epi/HAI 
data bucket in CAPE.

The ETL script will extract the tabular data and convert it to a common format
that will then be written into the clean data bucket for later query.

## Raw File Format

This file is given as a `.pdf` containing various text and two tables that will be
processed by this ETL script. 
The script assumes the 4th line of the pdf contains only the date of the report.
The script assumes the format of the two tables; if the tables do not have the 
correct format, the script will fail.

The script filters for only the following genes and their subtypes:
NDM, KPC, IMP, OXA, VIM, CMY

### Table Header Set

Table 1: 
    Columns: WGS_ID, Accession_ID, MLST_ST
Table 2:
    Columns: \<WGS_IDs...\>
    Rows: \<Genes...\>

## Cleaned Format

Results in a table with the columns:
Accession_ID, WGS_ID, MLST_ST, \<Genes...\>

## Failure Modes

The script will fail if the tables do not have the specified columns and rows.