# GEO Differential Expression Analysis with pyDESeq2

This repository contains a Jupyter Notebook for performing **Differential Expression Analysis (DEG)** on GEO datasets using **pyDESeq2** in Python.

## **Table of Contents**

* [Overview](#overview)
* [Requirements](#requirements)
* [Usage](#usage)
* [Workflow](#workflow)
* [Output](#output)
* [References](#references)

## **Overview**

This project demonstrates a complete workflow to:

1. Download GEO datasets using `GEOparse`.
2. Create a gene × sample expression matrix.
3. Build a sample metadata table (conditions like CONTROL vs TREATED).
4. Perform differential expression analysis using `pyDESeq2`.
5. Generate a volcano plot for visualization.

## **Requirements**

* Python 3.8+
* Required Python packages:

```bash
pip install GEOparse pandas numpy matplotlib pyDESeq2
```

## **Usage**

1. Clone the repository:

```bash
git clone https://github.com/yourusername/geo-DEG-analysis-pyDESeq2.git
cd geo-deg-analysis-pyDESeq2
```

2. Open the Jupyter Notebook:

```bash
jupyter notebook GEO_DEG_analysis.ipynb
```

3. Update the **GEO ID** in the notebook to your dataset:

```python
GSE_ID = "GSEXXXXX"
```

4. Run all notebook cells step by step. The notebook will:

* Download the GEO dataset
* Pivot samples to create an expression matrix
* Build a cleaned metadata table
* Perform DEG analysis using pyDESeq2
* Generate a volcano plot

## **Workflow**

1. **Download GEO dataset**
   Uses `GEOparse.get_GEO()` to retrieve the GSE series.

2. **Pivot expression data**
   Converts all samples into a `genes × samples` DataFrame using `pivot_samples('VALUE')`.

3. **Build metadata table**
   Extracts sample conditions from `gse.phenotype_data`, cleans the column, and formats it for pyDESeq2.

4. **Run pyDESeq2**
   Normalizes counts, calculates log2 fold changes, and computes statistical significance for each gene.

5. **Visualize results**
   Generates a volcano plot (`log2FC` vs `-log10(p-value)`) highlighting significant DEGs.

## **Output**

* `DEG_results.csv` → Table with log2 fold changes, p-values, and adjusted p-values.
* `volcano_plot.png` → Volcano plot of differentially expressed genes.

## **References**

* [GEOparse GitHub](https://github.com/guma44/GEOparse)
* [pyDESeq2 GitHub](https://github.com/owkin/PyDESeq2)
* [GEO (Gene Expression Omnibus)](https://www.ncbi.nlm.nih.gov/geo/)

## **Notes**

* Ensure your GEO dataset is **RNA-seq counts** or compatible microarray data.
* You can adapt this workflow for any GEO dataset by changing the `GSE_ID` variable.
