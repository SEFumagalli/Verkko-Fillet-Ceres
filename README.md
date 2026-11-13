## **Verkko-Fillet on USDA CERES**

**This file contains the Gyr methodology, code, and logistic reasoning for employing the Verkko-Fillet pipeline on *USDA-CERES*.** 
**The Verkko-Fillet pipeline is an easy-to-use, Python-based toolkit for cleaning graph paths generated from Verkko assembler.**
**Note: Verkko-Fillet is originally employed via Jupyter Notebook. Here, I modified the scripts to run via a bash file and produce merged reports.**

* This pipeline is described here: https://doi.org/10.1101/2025.10.01.679366 
* The GitHub repository containing the source code is located here: https://github.com/marbl/verkko-fillet (Juhyun Kim)
* Associated website with detailed walkthrough: https://verkko-fillet.readthedocs.io/en/latest/

\------------------------------------------------------------------------------------------------------------------------------------------------------

### **Description of the Verkko-Fillet pipeline**

A Python-based pipeline for post-Verkko graph and assembly cleaning. The bash script run_verkko_fillet.sh initiates the Verkko-Fillet run.

Before running see Details and Modifications files, these will walkthrough the changes made and scripts included. 

**Example Usage:**

```

python3 run_verkko_fillet.py --verkko_directory <verkko_assembly_directory_path> \
    --main\_directory <directory_with_verkko_assembly> \
    --rDNA_fasta <rDNA.fasta> \
    --ref_fasta <referece.fasta> \
    --phase_datatype <phasing_type> \
    --exp_chr_num <expected_chr_number> \
    --gaps <gaps?> \
    --mashmap_id_threshold 95 \
    --rDNA_fasta_fai <rDNA.fai> \
    --new_row <"$dict">	
    
    
```

**Paramter Description:**

* `--verkko_directory` Directory of verkko assembly run (required)
* `--main_directory` Directory outside of verkko assembly run (required)
* `--rDNA_fasta` The fasta listing the reference rDNA sequences (required)
* `--ref_fasta` A fasta genome for the reference (required)
* `--phase_datatype` Phasing data type - hic (form of Hi-C) , trio (Illumina), or trio_hic (Hi-C and Illumina) (required)
* `--exp_chr_num` Expected number of chromosomes - count sex chromosomes separately - better to overestimate than underestimate (required)
* `--gaps` Signal to Verkko-Fillet to find gaps (only run this on select assemblies - usually after first Verkko-Fillet run) -- True or False (required)
* `--mashmap_id_threshold` Alter the mashmap id threshold - default: 95 (required)
* `--rDNA_fasta_fai` Checks for Verkko created assembly.rDNA.fasta - if missing (required)
* `--new_row` add row/s to translation_hap* files via dictionary - this is used during a rerun (not required)

\----------------------------------------------------------------------------------------------------------------------------------------------------------
