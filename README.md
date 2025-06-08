## Phylogenetic Analysis of *Lactobacillus* spp. Using nf-core/phyloplace Pipeline

Introduction:

Lactobacilli are bacteria that colonised human body sites, particularly the digestive tract and the female genital tract. Thisorganism also play role in food industry. This project aims to analyse genome of Lactobacillus using nf-core/phyloplace, a bioinformatics best-practice analysis pipeline that performs phylogenetic placement with EPA-NG1. 

Research Hypothesis: 

The genomic analysis of Lactobacillus using nf-core/phyloplace will enable accurate phylogenetic placement and reveal distinct clustering that reflect their evolutionary relationships.

Parameters

--queryseqfile	
    A fasta formatted file with sequences to place.
    
--refseqfile	
    Reference sequences, several popular formats supported e.g. aligned fasta and phylip. Unless when specifying an --hmmfile, the sequences needs to be aligned.
    
--refphylogeny	
    Reference phylogeny.
--model	Evolutionary model 
    used when estimating the phylogeny, e.g. “LG+F+R6”.


    Pipeline Flowdiagram

```mermaid
flowchart TD
  A["Start: FASTA search of Lactobacillus (HMMER)"] --> B["Sequence Alignment (HMMER / Clustal Omega / MAFFT)"]
  B --> C["Phylogenetic Placement (EPA-NG)"]
  C --> D["Summary and Grafting (GAPPA)"]
  D --> E["Visualization (Heattree)"]
  E --> F["QC Report (MultiQC)"]
  F --> G["End: Final Output - Phylogenetic Tree & Summary Project Reports"]

Quickstart
nextflow run nf-core/phyloplace -r 1.0.0 \
  --queryseqfile '/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/SRR9860122.fasta,/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/ERR485020.fasta,/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fasta/SRR10240887.fasta' \
  --refseqfile '/Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/fastq/PROKKA_06042025/PROKKA_06042025.fna' \
  --outdir /Users/ajy_25yahoo.com/Desktop/Advance_BioInformatic_Project_Test/output/phyloplace_results \
  -profile docker

