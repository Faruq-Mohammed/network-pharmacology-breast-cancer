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
  Filtering (Relevance ≥ 5, Degree ≥ 50)
        ↓
  STRING Database → PPI Network
        ↓
  Cytoscape Network Analysis → Top 10 Hub Genes
        ↓
     ┌──────────────────────┐
     │                      │
  MCODE Clustering     CytoHubba Analysis
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
network-pharmacology-anxiety/
│
├── README.md
│
├── 01_data_collection/
│   ├── GeneCards_Anxiety_raw.csv              # Raw export from GeneCards
│   └── GeneCards_Anxiety_filtered.csv         # Filtered: Relevance ≥ 5, Degree ≥ 50
│
├── 02_ppi_network/
│   ├── string_input_genes.txt                 # Gene list submitted to STRING
│   ├── string_ppi_export.tsv                  # PPI network exported from STRING
│   └── anxiety_ppi_cytoscape.cys              # Full Cytoscape session file
│
├── 03_network_analysis/
│   ├── top10_hub_genes.csv                    # Top 10 genes by degree centrality
│   └── figures/
│       └── protein_protein_interaction.png              # Degree-sorted circle layout
│
├── 04_mcode_analysis/
│   ├── mcode_top3_clusters.csv                # Top 3 cluster results
│   ├── mcode_seed_genes.csv                   # 3 seed genes extracted
│   └── figures/
│       ├── mcode_cluster1.png
│       ├── mcode_cluster2.png
│       └── mcode_cluster3.png
│
├── 05_cytohubba_analysis/
│   ├── cytohubba_MCC_top10.csv
│   ├── cytohubba_MNC_top10.csv
│   ├── cytohubba_EPC_top10.csv
│   ├── cytohubba_Degree_top10.csv
│   ├── intersection_hub_genes.txt             # Genes common across all 4 algorithms
│   └── figures/
│       ├── cytohubba_mcc.png
│       ├── cytohubba_mnc.png
│       ├── cytohubba_epc.png
│       ├── cytohubba_degree.png
│       └── venn_intersection.png
│
├── 06_enrichment_analysis/
│   ├── final_hub_genes.txt                    # MCODE seeds + CytoHubba intersection
│   ├── GO_BP_enrichment.xlsx                  # Biological Process
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
  - Relevance Score ≥ 5
  - Degree ≥ 50

### Step 2 — PPI Network Construction
- **Tool:** [STRING Database](https://string-db.org/)
- Filtered gene list submitted to STRING
- Protein-protein interaction network exported and imported into **Cytoscape**

### Step 3 — Network Analysis in Cytoscape
- Network topology analyzed using **NetworkAnalyzer**
- Top 10 hub genes identified based on **degree centrality**
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
| GeneCards (after filtering) | *XX genes* |
| PPI Network Size | *XX nodes, XX edges* |
| Top Hub Genes (Degree) | *Update with your genes* |
| MCODE Seed Genes | *Update with your genes* |
| CytoHubba Intersection | *Update with your genes* |
| Key KEGG Pathways | *Update with your pathways* |

> Fill in the table above with your actual results before publishing.

---

## Figures

| Figure | Description |
|---|---|
| `03_network_analysis/figures/ppi_circle_layout.png` | PPI network — degree-sorted circle layout |
| `04_mcode_analysis/figures/` | Top 3 MCODE clusters |
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

1. Download `01_data_collection/GeneCards_Anxiety_filtered.csv`
2. Submit gene list to [STRING Database](https://string-db.org/) → Export network
3. Import network into Cytoscape → Run NetworkAnalyzer
4. Apply MCODE plugin → Extract top 3 cluster seed genes
5. Apply CytoHubba plugin (MCC, MNC, EPC, Degree) → Find intersection
6. Submit combined gene list to [Enrichr](https://maayanlab.cloud/Enrichr/)

---

## Author

**Faruq Mohammed**
B.Pharm, M.Pharm (ongoing)
Research Interests: Computer-Aided Drug Design (CADD) · Bioinformatics · Pharmacology · Phytochemical Research · Alternative Medicine · and Pharmaceutical Technology.

- 📧 Email: faruqmdtashriq@gmail.com
- 🔗 LinkedIn: https://www.linkedin.com/in/faruq-mohammed-tashriq/
- 🐙 GitHub: https://github.com/Faruq-Mohammed/

---

## License

This project is licensed under the [MIT License](LICENSE).
