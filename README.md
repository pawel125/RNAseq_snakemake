# Snakemake workflow for RNAseq raw data processing

The snakemake is created to easily be run on computing clusters with SLURM. For `qsub` `run_rnaseq_workflow.sh` will need to be adjusted.

## Requirements

* conda
* python environment with snakemake and pandas
* SLURM workload manager
* trim_galore
* samtools
* STAR aligner
* FastQC
* FastQ Screen (properly configured)
* MultiQC
* featureCounts (http://bioinf.wehi.edu.au/featureCounts/)

## Usage:

1. clone this repository
2. create conda environment called snakemake, or adjust the name of environment with installed snakemake in the `run_rnaseq_workflow.sh` file. If snakemake is visible globally, comment out line 16
3. install requirements or remove onwanted programs from `workflow/Snakefile`
4. update `samples.tsv` file
5. update `workflow/cluster.yml` to fit your cluster configuration
6. prepare STAR genome indices and RSeQC ref_file. Update both variables at the top of Snakefile.
7. run `./run_rnaseq_workflow.sh`

`samples.tsv` is a TSV formatted file with 3 mandatory columns: 
* library_name - clean name for the final bam file
* read_file - R1/R2 for paired end
* fastq_gz - path to fastq.gz file, might be messy but must not contain white spaces

## Limitations

* paired-end experiments only
