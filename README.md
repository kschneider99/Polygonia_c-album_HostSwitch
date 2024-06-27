# Plasticity for the win: Flexible transcriptional response to host plant switches in the comma butterfly (_Polygonia c-album_)
## K Schneider, RA Steward, M Celorio-Mancera, N Janz, D M, CW Wheat, S Nylin


## Abstract
Generalist plant-feeding insects are characterized by a broad host repertoire that can comprise several families or even different orders of plants. The genetic and physiological mechanisms underlying the use of such a wide host range are still not fully understood.  Earlier studies indicate that the consumption of different host plants is associated with host-specific gene expression profiles. It remained, however, unclear if and how larvae can alter these profiles in the case of a changing host environment. Using the polyphagous comma butterfly (Polygonia c-album) we show that larvae can adjust their transcriptional profiles in response to a new host plant. The switch to some of the host plants, however, resulted in a larger transcriptional response and, thus, seems to be more challenging. At a physiological level, no correspondence for these patterns could be found in larval performance. This suggests that a high transcriptional but also phenotypic flexibility are essential for the use of a broad and diverse host range. We furthermore propose that host switch tests in the laboratory followed by transcriptomic investigations can be a valuable tool to examine not only plasticity in host use but also subtle and/or transient trade-offs in the evolution of host plant repertoires. 

### Experimental Setup and Methods
For this study, two switch experiments were combined, which differed in the used host plants. 
**Switch A**: _Urtica dioica_ (Ud or N in the datasheets and scripts), _Salix caprea_ (Sc or S), _Ulmus glabra_ (Ug or E)
**Switch B**: _Urtica dioica_, _Salix caprea_, _Ribes_uva_crispa_(Ru or G)
(Note that Switch A can be referred to Switch 1 or S1 in some scripts or files. Same for Swith B (Switch 2, S2))
Larvae of _Polygonia c-album_ were reared on either of the three different host plants until they reached their 4th instar. Upon reaching this developmental stage they were transferred to one of the alternative host plants (_Switch_). As a control some individuals were also switched to the same host plants species (_Control_, e.g. _Ud-Ud_). 

### Differential gene expression analysis
To measure the transcriptional repsonse to a switch, larval midguts were collected 2 and 17 hours after the individuals were moved to a new host plant.
RNA was extracted, library preparation (with Poly-A-selection) and sequencing was done at the NGI SciLifelab in Stockholm. RNA libraries were sequenced with 2x101bp paired-end sequencing on an Illumina TruSeq platform.
Raw reads were first quality checked, adapters were removed and quality was checked again (scripts FastQC_pre, FastQC_post, MultiQC and Trimming in /Polygonia_c-album_HostSwitch/scripts/Bash-scripts/). After trimming samples were renamed to also include information about the host plants and the sampling timepoints. The list of corresponding sample names can be found in /Polygonia_c-album_HostSwitch/scripts/Bash-scripts/Sample_names_S1 and /Polygonia_c-album_HostSwitch/scripts/Bash-scripts/Sample_names_S2.
Reads were aligned to a previously published reference genome of Polygonia c-album (Celorio-Mancera et al. 2021) using a using a STAR 2-pass approach (Bash-scripts: STAR_index, STAR_Pass1, STAR_Pass2). 
Abundance estimations were done using featureCounts (script: /Polygonia_c-album_HostSwitch/scripts/Bash-scripts/FeatureCounts; generated count matrices: /Polygonia_c-album_HostSwitch/scripts/Count_matrices). 

Downstream analysis was performed in R using EdgeR (script: /Polygonia_c-album_HostSwitch/scripts/R-scripts/HostSwitch_DGE.Rmd). 
First datasets were split by the sampling timepoints (lines 112-159) and separate differential gene expression lists were created for each timepoint in an experiment (lines 161-216).
The data were filtered and normalized (lines 219-284). For a preliminary understanding of the effect of treatment and to check for any major outliers, we ran principal component analysis (PCA) and produced Heatmaps of the 5000 most variable genes (lines: 318-1096). For this data were first transformed using a pseudo-log transformation (lines: 304-312). 
For global assessment of gene expression in response to host switches, the effect of individual host plants and their interaction on the number of differentially expressed genes was tested (start line 1099). For this model matrices were designed (lines 1101-1150) for each effect. Dispersion was estimated (lines 1153-1175). Models were fit using quasi-likelihood fit (lines: 1178-1200) and differences among the groups were identified with a quasi-likelihood tests (lines: 1203-1274). Overlaps in the differentially expressed genes were visualized using Venn diagrams (lines: 1276-1357). 
To test for the gene expression differences between the switches we did pairwise comparisons between the treatments (for this each Host1*Host2 combination were defined as an own group; starting line: 1360)
As before we desgined model matrices (lines 1363-1391), estimated dispersion (lines 1393-1406), fitted models (lines 1409-1427) and ran quasi likelihood tests (lines 1585-1659) using defined contrasts (lines 1429-1582). Visualization fo significantly differentially expressed genes was done using Upset plots (lines 1662-2057).
Significantly differentially expressed genes (FDR <0.05) were further classified in either of 4 categories:
1. Differences in the gene expression after the host switch correspond to differences found between the controls, indicating an adjustment to the new host
2. No differences in gene expression after the switch despite differences between the controls, corresponding to the gene expression profiles on Host 1
3. Differences in gene expression after the switch but no differences between the controls
4. Differences in gene expression after the switch that are opposite to differences between controls.
Furthermore, a gene set enrichment analysis for the significantly differentially expressed genes per category were performed (visualization and topGo: lines 2074-4106). 
The functional annotation used for the gene set enrichment analysis can be found in /Polygonia_c-album_HostSwitch/Annotation/. 
The output of the gene set enrichment analysis can also be found in /Polygonia_c-album_HostSwitch/Annotation/GO_term_output

### Performance assay
Additionally the effect of host switches on the larval performance was assessed by measuring the daily weight gain (script: /Polygonia_c-album_HostSwitch/scripts/R-scripts/HostSwitch_Performance_assay; data sheet:/Polygonia_c-album_HostSwitch/Performance_data).


## Data availability

RNA-seq data used for this study have been archived on the European Nucleotide Archive (ENA) under the accession number PRJEB72698. 
Reads were mapped to P. c-album genome available from the European Nucleotide Archive (accession number ERZ1744298). A copy of the genome is also publicly available at C. Wheat’s github repository Celorio-Mancera et al. (2021) in which the genome is reported: https://github.com/bioinfowheat/Polygonia_calbum_genomics. The gene annotation and functional annotation used in our analyses as well as raw count matrices and all bash and R scripts have been provided. 


## Code Availability

Provided bash and R scripts used for the analysis include: 
  -	Quality assessment, trimming and mapping of reads
  -	Abundance estimation to produce count table
  -	Differential gene expression analysis in edgeR:
    -	Filtering and normalizing data (line 219)
    -	Effect of individual hosts and their interaction on the number of differentially expressed genes (line 1099)
    -	Effect of host switch on the number of differentially expressed genes (line 1364)
    -	Further categorization and gene set enrichment analysis of significantly differentially expressed genes (line 2064)
  -	Effect of host switch on the larval performance 
