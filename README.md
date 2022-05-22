# NGS Data Analysis - Project

## Structure of the repository

- src directory contains all scripts used for data analysis. It includes:
	- Downloading data from SRA using fastq-dump
	- Quality Control using fastp
	- Alignment to the reference genome using samtools
	- Post-alignment processes using samtools
	- Variant calling using samtools and bcf tools
	- Filtering Variants using perl script provided by bcftools

	There is also subdirectory addons, which contains:
		- script for changing chromosome names in contigs
		- script for downloading reference genome
		- script for merging reference genome

- data directory contains all the data that was used and processed during the analysis. Includes:
 	- raw data in FASTQC format
 	- cleaned data in FASTQC format
 	- Referece genome with contigs and indexes
 	- Aligned reads to the genome in BAM format

- vcfs directory contains raw variants data obtained after variant calling step

- final_data directory contains data in VCF format obtained in the last stage of the analysis after the variant calling and filtering variants. It also contains prepared input data for VEP (Variant Effect Predictor) tool, and also output data from VEP.

- logs directory contains messages and outputs from softwares

## Tree of the directory structure

```{bash}
.
├── Project overview.txt
├── RAPORT.md
├── README.md
├── data
│   ├── alignment
│   │   ├── SRR064545.bam
│   │   ├── SRR064545.sorted.bam
│   │   ├── SRR064545.sorted.bam.bai
│   │   ├── SRR064546.bam
│   │   ├── SRR064546.sorted.bam
│   │   ├── SRR064546.sorted.bam.bai
│   │   ├── SRR064547.bam
│   │   ├── SRR064547.sorted.bam
│   │   └── SRR064547.sorted.bam.bai
│   ├── qc_data
│   │   ├── SRR064545_1.fastq.gz
│   │   ├── SRR064545_2.fastq.gz
│   │   ├── SRR064545qc_fastp.html
│   │   ├── SRR064546_1.fastq.gz
│   │   ├── SRR064546_2.fastq.gz
│   │   ├── SRR064546qc_fastp.html
│   │   ├── SRR064547_1.fastq.gz
│   │   ├── SRR064547_2.fastq.gz
│   │   └── SRR064547qc_fastp.html
│   ├── raw_data
│   │   ├── SRR064545_1.fastq.gz
│   │   ├── SRR064545_2.fastq.gz
│   │   ├── SRR064546_1.fastq.gz
│   │   ├── SRR064546_2.fastq.gz
│   │   ├── SRR064547_1.fastq.gz
│   │   └── SRR064547_2.fastq.gz
│   └── reference_genome
│       ├── SRR064545.sai
│       ├── SRR064546.sai
│       ├── SRR064547.sai
│       ├── Saccharomyces.reference.genome.fa.gz
│       ├── Saccharomyces.reference.genome.fa.gz.amb
│       ├── Saccharomyces.reference.genome.fa.gz.ann
│       ├── Saccharomyces.reference.genome.fa.gz.bwt
│       ├── Saccharomyces.reference.genome.fa.gz.fai
│       ├── Saccharomyces.reference.genome.fa.gz.pac
│       ├── Saccharomyces.reference.genome.fa.gz.sa
│       ├── Saccharomyces_cerevisiae.genome.fa.gz
│       ├── contigs
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.I.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.II.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.III.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.IV.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.IX.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.Mito.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.V.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.VI.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.VII.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.VIII.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.X.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XI.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XII.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XIII.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XIV.fa.gz
│       │   ├── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XV.fa.gz
│       │   └── Saccharomyces_cerevisiae.R64-1-1.dna.chromosome.XVI.fa.gz
│       └── index.txt
├── final_data
│   ├── SRR064545.final.vcf
│   ├── SRR064545.vep.input.txt
│   ├── SRR064545.vep.output.txt
│   ├── SRR064545.vep.stats.png
│   ├── SRR064546.final.vcf
│   ├── SRR064546.vep.input.txt
│   ├── SRR064546.vep.output.txt
│   ├── SRR064546.vep.stats.png
│   ├── SRR064547.final.vcf
│   ├── SRR064547.vep.input.txt
│   ├── SRR064547.vep.output.txt
│   └── SRR064547.vep.stats.png
├── logs
│   ├── BWAAlignmentLogs.txt
│   ├── BWAIndexLogs.txt
│   ├── DownloadDataLogs.txt
│   ├── QC.logs.txt
│   ├── SRR064545.flagstat_logs.txt
│   ├── SRR064545.stat_logs.txt
│   ├── SRR064546.flagstat_logs.txt
│   ├── SRR064546.stat_logs.txt
│   ├── SRR064547.flagstat_logs.txt
│   └── SRR064547.stat_logs.txt
├── src
│   ├── 01.DownloadSRAData.sh
│   ├── 02.QC.sh
│   ├── 03.ReferenceGenomeAlignment.sh
│   ├── 04.PostAlignmentProcesses.sh
│   ├── 05.VariantCalling.sh
│   ├── 06.FilteringVariants.sh
│   └── addons
│       ├── ChangeChromNames.sh
│       ├── DownloadReferenceGenome.sh
│       └── MergeGenome.sh
└── vcfs
    ├── SRR064545_variants.vcf
    ├── SRR064546_variants.vcf
    └── SRR064547_variants.vcf

11 directories, 90 files
```