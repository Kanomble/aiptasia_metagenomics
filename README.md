# aiptasia_metagenomics
Python scripts to work on exaiptasia diaphana metagenomic data

## How to work with the notebook: `extract_datasets_pipeline`

The notebook `scripts/extract_datasets_pipeline.ipynb` collects public
Exaiptasia/Aiptasia microbiome datasets from NCBI. It searches within the BioProject database,
fetches detailed BioProject metadata, links each BioProject to BioSample and
SRA records, extracts run-level SRR metadata, and writes the resulting tables to
`results/`.

To use it, create the conda environment and open the notebook from the
repository root:

```bash
conda env create -f environment_short.yml
conda activate aiptasia_metagenomics
jupyter notebook scripts/extract_datasets_pipeline.ipynb
```

Before running the cells, set `Entrez.email`/`setup_entrez(...)` to your own
email address as required by NCBI. Then run the notebook from top to bottom. The
main outputs are:

- `results/exaiptasia_microbiome_studies.csv`
- `results/bioproject_to_biosample.table`
- `results/bioproject_to_sra.table`
- `results/bioproject_to_sra_details.table`
- `results/biorpoject_to_srr_metadata.tsv`

The final section contains an optional `download_and_compress_srr(...)` helper
for downloading SRR FASTQ files with `fasterq-dump`. Update the local
`fasterq-dump` path in that function before using it.
