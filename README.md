## Phylogenetic Analysis of *Lactobacillus* spp. Using nf-core/phyloplace Pipeline

Introduction:
Lactobacilli are bacteria that colonised human body sites, particularly the digestive tract and the female genital tract. Thisorganism also play role in food industry. This project aims to analyse genome of Lactobacillus using nf-core/phyloplace, a bioinformatics best-practice analysis pipeline that performs phylogenetic placement with EPA-NG1. 

Research Hypothesis: 
The genomic analysis of Lactobacillus using nf-core/phyloplace will enable accurate phylogenetic placement and reveal distinct clustering that reflect their evolutionary relationships.

Flow Diagram

```mermaid
flowchart TD
    A["Start:10 FASTA search of Lactobacillus (HMMER)"] --> B["Sequence Alignment (HMMER / Clustal Omega / MAFFT)"]
    B --> C["Phylogenetic Placement (EPA-NG)"]
    C --> D["Summary and Grafting (GAPPA)"]
    D --> E["Visualization (Heattree)"]
    E --> F["QC Report (MultiQC)"]
    F --> G["End: Final Output - Phylogenetic Tree & Summary Project Reports"]


