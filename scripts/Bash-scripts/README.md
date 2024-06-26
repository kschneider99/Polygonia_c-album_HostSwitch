Presented Bash scripts were run separately for Switch A and Switch B.
  Provided scripts include the code for Switch B, however, exaclty the same commands were used for quality checks,trimming, mapping and abundance estimation of samples in Switch A
  (Note: In the scripts Switch A is referred to as Switch_1; Switch B is referred to as Switch_2!)

  The quality of the raw reads was checked using FastQC and MultiQC (Quality_pre.sh, MulitQC.sh) before adapters were removed using Trimmomatic (Trimming.sh). After trimming quality was again checked (Quality_post.sh, MulitQC.sh).
  Mapping was done using the STAR. Before mapping an index had to be created (STAR_index.sh). Mapping was done using a 2-pass approach (STAR_Pass1.sh, STAR_Pass2.sh).
  Mapping success was assessed using Flagstat (Flagstat.sh).
  A count matrix was created using Featurecounts (FeatureCounts.se).
  Downstream analysis was done using edgeR (HostSwitch_PCA_DGE.R and HostSwitch_PCA_Performance.R).

      Bash-scripts
      - FastQC_pre.sh - quality check of raw fastq files
      - Trimming.sh - trimming RNA-Seq reads
      - FastQC_post.sh - quality check of fastq files after trimming
      - MultiQC.sh -  creating summary of fastqc reports before and after trimming
      - STAR_index.sh - creating index for Mapping
      - STAR_Pass1.sh -  mapping trimmed reads to reference
      - STAR_Pass2.sh -  mapping trimmed reads to reference (splice junctions awareness)
      - Flagstat.sh - quecking mapping success
      - FeatureCounts.sh - abundance estimation
      Note: Scripts were run on Uppmax, so packages/modules had to be loaded using "module load bioinfo-tools"
