# Network Pharmacology Analysis of Breast Cancer
### Hub Gene Identification and Pathway Enrichment via PPI Network Analysis

---

## Overview

This project presents a systematic **network pharmacology workflow** to identify key hub genes and critical biological pathways associated with **Breast Cancer**. By integrating disease gene databases, protein-protein interaction (PPI) network analysis, clustering algorithms, and enrichment tools, this study uncovers central molecular targets that may serve as candidates for therapeutic intervention.

---

## Workflow Summary

```
GeneCards (Breast cancer)
        ↓
  Filtering (Relevance score ≥ 15, Gifts score ≥ 60)
        ↓
  STRING Database → PPI Network
        ↓
  Cytoscape Network Analysis → Top 30 Hub Genes
        ↓
     ┌──────────────────────┐
     │                      │
  MCODE Clustering     CytoHubba Analysis of top 10 genes
  (Top 3 Clusters)    (MCC, MNC, EPC, Degree)
  3 Seed Genes         Intersection Genes
     │                      │
     └──────────┬───────────┘
                ↓
     GO & KEGG Enrichment Analysis
            (Enrichr)
```

---

## Repository Structure

```
network-pharmacology-breast-cancer/
│
├── README.md
│
├── 01_data_collection/
│   ├── GeneCards_Breast_cancer_raw.csv              
│   └── GeneCards_Breast_cancer_filtered.csv         
│
├── 02_ppi_network/
│   ├── string_input_genes.txt                 
│   ├── string_ppi_export.tsv                  
│   └── breast_cancer_ppi_cytoscape.cys              
│
├── 03_network_analysis/
│   ├── top30_hub_genes.txt                    
│   └── figures/
│       └── protein_protein_interaction.png              
│
├── 04_mcode_analysis/                
│   ├── mcode_seed_genes.txt  
│
├── 05_cytohubba_analysis/
│   ├── cytohubba_MCC_top10.csv
│   ├── cytohubba_MNC_top10.csv
│   ├── cytohubba_EPC_top10.csv
│   ├── cytohubba_Degree_top10.csv
│   ├── intersection_hub_genes.txt            
│   └── figures/
│       ├── cytohubba_mcc.png
│       ├── cytohubba_mnc.png
│       ├── cytohubba_epc.png
│       ├── cytohubba_degree.png
│       └── venn_intersection.png
│
├── 06_enrichment_analysis/
│   ├── final_hub_genes.txt                   
│   ├── GO_BP_enrichment.xlsx                 
│   ├── KEGG_pathway_enrichment.xlsx
│   └── figures/
│       ├── GO_BP_barplot.png
│       └── KEGG_barplot.png
│
└── results/
    └── final_summary.docx
```

---

## Detailed Methodology

### Step 1 — Disease Gene Collection
- **Database:** [GeneCards](https://www.genecards.org/)
- **Disease:** Breast Cancer
- **Filters Applied:**
  - Relevance Score ≥ 15
  - Gifts score ≥ 60

### Step 2 — PPI Network Construction
- **Tool:** [STRING Database](https://string-db.org/)
- Filtered gene list submitted to STRING
- Protein-protein interaction network exported and imported into **Cytoscape**

### Step 3 — Network Analysis in Cytoscape
- Network topology analyzed using **NetworkAnalyzer**
- Top 30 hub genes identified based on **degree centrality**
- **Degree-sorted circle layout** created for visualization

### Step 4 — MCODE Clustering
- **Plugin:** MCODE (Molecular Complex Detection)
- Top 3 molecular clusters identified
- **3 seed genes** extracted from the highest-scoring clusters

### Step 5 — CytoHubba Hub Gene Identification
- **Plugin:** CytoHubba
- **Algorithms used:** MCC, MNC, EPC, Degree
- Top 10 genes extracted from each algorithm independently
- **Intersection** of all four algorithm results identified as the most robust hub genes

### Step 6 — GO and KEGG Enrichment Analysis
- **Tool:** [Enrichr](https://maayanlab.cloud/Enrichr/)
- **Input genes:** MCODE seed genes + CytoHubba intersection genes (combined)
- **Analyses performed:**
  - Gene Ontology (GO): Biological Process (BP)
  - KEGG Pathway Analysis

---

## Key Results

| Analysis Step | Result |
|---|---|
| GeneCards (after filtering) | *195 genes* |
| PPI Network Size | *195 nodes, 1145 edges* |
| MCODE Seed Genes | *EGFR,JUN,PTK2* |
| CytoHubba Intersection | *PIK3R1,EGFR,PIK3CA,SRC* |
| Key KEGG Pathways | *Breast cancer* |


---

## Figures

| Figure | Description |
|---|---|
| `03_network_analysis/figures/protein_protein_interaction.png` | PPI network — degree-sorted circle layout |
| `05_cytohubba_analysis/figures/venn_intersection.png` | CytoHubba Venn intersection |
| `06_enrichment_analysis/figures/` | GO and KEGG enrichment bar plots |

---

## Tools & Software

| Tool / Software | Version | Purpose |
|---|---|---|
| GeneCards | — | Disease gene collection |
| STRING Database | v12 | PPI network construction |
| Cytoscape | 3.10.4 | Network visualization and analysis |
| MCODE Plugin | — | Molecular complex detection |
| CytoHubba Plugin | — | Hub gene identification |
| Enrichr | — | GO and KEGG enrichment analysis |

---

## How to Reproduce This Analysis

1. Download `01_data_collection/GeneCards_Breast_cancer_filtered.csv`
2. Submit gene list to [STRING Database](https://string-db.org/) → Export network
3. Import network into Cytoscape → Run NetworkAnalyzer
4. Apply MCODE plugin → Extract top 3 cluster seed genes
5. Apply CytoHubba plugin (MCC, MNC, EPC, Degree) → Find intersection
6. Submit combined gene list to [Enrichr](https://maayanlab.cloud/Enrichr/)

---

## Author

**Faruq Mohammed**
B.Pharm, M.Pharm (ongoing) · 
Research Interests: Computer-Aided Drug Design (CADD) · Bioinformatics · Pharmacology · Phytochemical Research · Alternative Medicine · and Pharmaceutical Technology.

- 📧 Email: faruqmdtashriq@gmail.com
- 🔗 LinkedIn: [Faruq Mohammed](https://www.linkedin.com/in/faruq-mohammed-tashriq/)
- 🐙 GitHub: [Faruq Mohammed](https://github.com/Faruq-Mohammed/)

---

## License

This project is licensed under the [MIT License](LICENSE).
