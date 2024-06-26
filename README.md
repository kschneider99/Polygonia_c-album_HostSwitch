Abstract

Generalist plant-feeding insects are characterized by a broad host repertoire that can comprise several families or even different orders of plants. The genetic and physiological mechanisms underlying the use of such a wide host range are still not fully understood.  Earlier studies indicate that the consumption of different host plants is associated with host-specific gene expression profiles. It remained, however, unclear if and how larvae can alter these profiles in the case of a changing host environment. Using the polyphagous comma butterfly (Polygonia c-album) we show that larvae can adjust their transcriptional profiles in response to a new host plant. The switch to some of the host plants, however, resulted in a larger transcriptional response and, thus, seems to be more challenging. At a physiological level, no correspondence for these patterns could be found in larval performance. This suggests that a high transcriptional but also phenotypic flexibility are essential for the use of a broad and diverse host range. We furthermore propose that host switch tests in the laboratory followed by transcriptomic investigations can be a valuable tool to examine not only plasticity in host use but also subtle and/or transient trade-offs in the evolution of host plant repertoires. 



Data availability


RNA-seq data used for this study have been archived on the European Nucleotide Archive (ENA) under the accession number PRJEB72698. 
Reads were mapped to P. c-album genome available from the European Nucleotide Archive (accession number ERZ1744298). A copy of the genome is also publicly available at C. Wheat’s github repository Celorio-Mancera et al. (2021) in which the genome is reported: https://github.com/bioinfowheat/Polygonia_calbum_genomics. The gene annotation and functional annotation used in our analyses as well as raw count matrices and all bash and R scripts have been provided. 


Code Availability


Provided bash and R scripts used for the analysis include: 
-	Quality assessment, trimming and mapping of reads
-	Abundance estimation to produce count table
-	Differential gene expression analysis in edgeR: 
o	Filtering and normalizing data (line 219)
o	Effect of individual hosts and their interaction on the number of differentially expressed genes (line 1099)
o	Effect of host switch on the number of differentially expressed genes (line 1364)
o	Further categorization and gene set enrichment analysis of significantly differentially expressed genes (line 2064)
-	Effect of host switch on the larval performance 
