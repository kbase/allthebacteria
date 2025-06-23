# AllTheBacteria

A standardized, large-scale collection of uniformly assembled prokaryotic genomes, spanning **2.4 million bacterial** and **815 archaeal** assemblies. Extends the original 661K genomes (Blackwell et al. 2021) by incorporating comprehensive assembly, annotation, and metadata assets.

---

## Overview

* **Scope**:

  * **Bacteria**: \~2.44 million assemblies (Release 0.2 + Incremental Aug 2024) ([allthebacteria.readthedocs.io][1])
  * **Archaea**: \~815 assemblies (July 2024 release) ([allthebacteria.readthedocs.io][1])
* **Releases**:

  * **Release 0.2** (Mar 2024): 1.93M assemblies, contending from Nov 2018
  * **Incremental releases** (e.g. Aug 2024): new datasets added
  * Aggregated builds available for ease of use ([allthebacteria.readthedocs.io][1])
* **Access**:

  1. **Data and files** – hosted on [OSF](https://osf.io/xv7q9), AWS, and ENA ([allthebacteria.readthedocs.io][1])
  2. **Documentation** – this repo and ReadTheDocs
  3. **Methods/code** – reproducible pipelines for assembly, annotation, and QC ([allthebacteria.readthedocs.io][1])

---

## Data Components

* **Assembly FASTAs**:

  * Individual `.fa.gz` assemblies on AWS S3
  * Batch archives (`.tar.xz`) on OSF with Miniphy compression ([allthebacteria.readthedocs.io][2])
* **Metadata & QC**:

  * Flat files + consolidated SQLite DB containing INSDC, Sylph, CheckM2, assembly stats, and contamination reports ([allthebacteria.readthedocs.io][3])
* **Annotations & Features**:

  * Gene & protein annotations (e.g., AMRFinderPlus, BGC detection), microbial typing, and LexicMap index for rapid sequence alignment ([allthebacteria.readthedocs.io][4])

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/AllTheBacteria/AllTheBacteria.git
cd AllTheBacteria
```

### 2. Download Datasets

* **Flat metadata** (Release 0.2 + Aug 2024): from OSF
* **Individual FASTA** (for specific samples):

  ```bash
  aws s3 cp --no-sign-request \
    s3://allthebacteria-assemblies/SAMD00000344.fa.gz .
  ```
* **Batch TARs** (for large-scale usage): via OSF batching scripts

### 3. Explore Metadata & QC

* View TSV and SQLite metadata tables
* Identify samples with PASS status via `status.202408.tsv.gz`

### 4. Download Assemblies

* **Small subset**: individual AWS FASTAs
* **Large batches**: OSF TAR.XZ archives + Miniphy

### 5. Perform Annotation & AMR Analysis

* AMR outputs via AMRFinderPlus in versioned directories
* Use provided Snakemake workflows to reproduce or update annotated datasets

### 6. Sequence Querying via LexicMap

* Query against nucleotide index on AWS or download locally for large-scale alignment ([allthebacteria.readthedocs.io][5], [allthebacteria.readthedocs.io][2], [allthebacteria.readthedocs.io][3], [allthebacteria.readthedocs.io][4])

---

## Reproducibility & Contributing

* **Methods**: source code pipelines are maintained here — assembly, QC, annotation, alignment
* **Batch downloads**: use the `"osf_get_files_for_project.py"` script to ingest OSF project files ([allthebacteria.readthedocs.io][6])
* **Migration history**: track renaming from EBI FTP to OSF-compatible naming ([allthebacteria.readthedocs.io][7])
* **Contributions**:

  * Submit PRs for bug fixes or new annotation workflows
  * Engage via issues for feature requests or collaboration

---

## Future Directions

* Scheduled **incremental annual releases** to keep pace with new assembly submissions
* **Aggregated dataset bundles** for ease of downstream use, avoiding release fragmentation
* Ongoing enhancement of annotation richness, QC rigor, and user-friendliness

---

## References

* Blackwell et al. (2021) PLOS Biology, 661K bacterial genomes
* ReadTheDocs for full [overview, metadata, assembly, annotation guides](https://allthebacteria.readthedocs.io/en/latest/overview.html)


[1]: https://allthebacteria.readthedocs.io/en/latest/overview.html?utm_source=chatgpt.com "Overview — AllTheBacteria documentation"
[2]: https://allthebacteria.readthedocs.io/en/latest/assemblies.html?utm_source=chatgpt.com "Assemblies — AllTheBacteria documentation"
[3]: https://allthebacteria.readthedocs.io/en/latest/sample_metadata.html?utm_source=chatgpt.com "Metadata and QC — AllTheBacteria documentation"
[4]: https://allthebacteria.readthedocs.io/en/latest/amr.html?utm_source=chatgpt.com "Antimicrobial Resistance — AllTheBacteria documentation"
[5]: https://allthebacteria.readthedocs.io/en/latest/lexicmap.html?utm_source=chatgpt.com "Sequence alignment with LexicMap — AllTheBacteria documentation"
[6]: https://allthebacteria.readthedocs.io/en/latest/osf_downloads.html?utm_source=chatgpt.com "Batch downloading from OSF — AllTheBacteria documentation"
[7]: https://allthebacteria.readthedocs.io/en/latest/ebi2osf.html?utm_source=chatgpt.com "Migration from EBI FTP to OSF — AllTheBacteria documentation"
