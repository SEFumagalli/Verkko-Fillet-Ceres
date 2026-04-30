## **Verkko-Fillet on USDA CERES**

**This file contains the Gyr methodology, code, and logistic reasoning for employing the Verkko-Fillet pipeline on *USDA-CERES*. The Verkko-Fillet pipeline is an easy-to-use, Python-based toolkit for cleaning graph paths generated from Verkko assembler. Note: Verkko-Fillet is originally employed via Jupyter Notebook. Here, we modified the scripts to run via a bash file.**

* This pipeline is described here (soon to be published in Cell Genomics): https://doi.org/10.1101/2025.10.01.679366 
* The GitHub repository containing the source code is located here: https://github.com/marbl/verkko-fillet (Juhyun Kim)
* Associated website with detailed walkthrough: https://verkko-fillet.readthedocs.io/en/latest/

File Author: *Sarah E. Fumagalli*; sefumagal@gmail.com

\---

### **Description of the Verkko-Fillet pipeline**

A Python-based pipeline for post-Verkko graph and assembly cleaning. The bash script run\_verkko\_fillet.sh initiates the Verkko-Fillet run.

**Example Usage:**

```

python3 run\_verkko\_fillet.py \\

&#x09;--verkko\_directory verkko2.2.1\_hifi-duplex\_tporec/ \\

&#x09;--main\_directory Gyr/assembly/ \\

&#x09;--rDNA\_fasta Cattle\_rDNA.fasta \\

&#x09;--ref\_fasta ARS-UCD2.0\_chr.fasta \\

&#x20;	--phase\_datatype trio\_hic \\

&#x20;       --exp\_chr\_num 31 \\

&#x09;--gaps False \\

&#x09;--mashmap\_id\_threshold 95 \\

&#x09;--rDNA\_fasta\_fai $rDNA\_fai \\

&#x09;--new\_row "$dict"	
```

**Paramter Description:**

* `--verkko\_directory` Directory of verkko assembly run
* `--main\_directory` Directory outside of verkko assembly run
* `--rDNA\_fasta` The fasta listing the reference rDNA sequences
* `--ref\_fasta` A fasta genome for the reference
* `--phase\_datatype` Phasing data type - hic (form of Hi-C) , trio (Illumina), or trio\_hic (Hi-C and Illumina)
* `--exp\_chr\_num` Expected number of chromosomes - count sex chromosomes separately - better to overestimate than underestimate
* `--gaps` Signal to Verkko-Fillet to find gaps (only run this on select assemblies - usually after first Verkko-Fillet run) -- True or False
* `--mashmap\_id\_threshold` Alter the mashmap id threshold - default: 95 
* `--rDNA\_fasta\_fai` Checks for Verkko created assembly.rDNA.fasta - if missing
* `--cluster` If you are using a cluster with slurm this will cause conkord.py to submit an sbatch command for snakemake with the number of cores provided

\---
