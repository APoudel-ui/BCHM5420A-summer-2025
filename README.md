## Phylogenetic Analysis of *Lactobacillus* spp. Using nf-core/phyloplace Pipeline

  Introduction

Lactobacilli are bacteria that colonised human and animal body sites, such as the digestive tract and the female genital tract.
Lactobacilli are among the most common probiotic found in food (such as yogurt), 

This project aims to analyse genome of Lactobacillus using nf-core/phyloplace, a bioinformatics best-practice analysis pipeline that performs phylogenetic placement with EPA-NG1. This pipeline performs phylogenetic placement by individually mapping query sequences onto a reference tree based on likelihood. It avoids reconstructing a full phylogeny, making it ideal for short sequences (e.g., PCR amplicons, metagenomic fragments). It is also useful for  large sequence datasets. 
The final output includes a complete tree with both reference and query sequences, where queries are inserted at their most likely positions.

Research Question
How do my Lactobacillus query sequences relate phylogenetically to known Lactobacillus reference sequence within an established reference tree?
	(This will let us know whether my query isolates fall within known clades or form distinct lineages when placed on a curated phylogeny.)

Hypothesis 
Genomic analysis of Lactobacillus using nf core/phyloplace will enable accurate phylogenetic placement and reveal distinct clustering that reflect their evolutionary relationships.


Parameters

--queryseqfile	
    A fasta formatted file with sequences to place.
    
--refseqfile	
    Reference sequences, several popular formats supported e.g. aligned fasta and phylip. Unless when specifying an --hmmfile, the sequences needs to be aligned.
    
--refphylogeny	
    Reference phylogeny.
--model	Evolutionary model 
    used when estimating the phylogeny, e.g. “LG+F+R6”.


    Quickstart
nextflow run nf-core/phyloplace -r 1.0.0 \
  --queryseqfile '/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/SRR9860122.fasta,/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/ERR485020.fasta,/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/SRR10240887.fasta' \
  --refseqfile '/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fastq/PROKKA_06042025/PROKKA_06042025.fna' \
  --outdir /Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/output/phyloplace_results \
  -profile docker


    Pipeline Flowdiagram

```mermaid
flowchart TD
  A["Start: FASTA search of Lactobacillus (HMMER)"] --> B["Sequence Alignment (HMMER / Clustal Omega / MAFFT)"]
  B --> C["Phylogenetic Placement (EPA-NG)"]
  C --> D["Summary and Grafting (GAPPA)"]
  D --> E["Visualization (Heattree)"]
  E --> F["QC Report (MultiQC)"]
  F --> G["End: Final Output - Phylogenetic Tree & Summary Project Reports"]


