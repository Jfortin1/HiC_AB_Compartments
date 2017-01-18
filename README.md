![alt tag](https://raw.github.com/jfortin1/TCGA_AB_Compartments/master/figures/try.png)

# HiC_AB_Compartments

Analysis of Hi-C data has shown that the genome can be divided into two compartments
called A/B compartments. These compartments are cell-type specific and are
associated with open and closed chromatin. In our recent Genome Biology paper, ([Fortin et al., 2015](http://www.genomebiology.com/2015/16/1/180)), we showed that we can estimate A/B compartments from 450k methylation array data as well as DNase hypersensitivity data. This GitHub repo contains the genome-wide A/B compartments computed for different Hi-C datasets, as well as the A/B compartments estimated from methylation array and DNase-Seq data. All the data are at at resolution 100kb, for hg19. For the A/B compartmentes estimated for 12 different cancer types from the Cancer Genome Atlas (TCGA), please visit the following GitHub repo: [TCGA A/B compartments](https://github.com/Jfortin1/TCGA_AB_Compartments).

Citation for using these data:

Jean-Philippe Fortin, Kasper D. Hansen. *Reconstructing A/B compartments as revealed by Hi-C using long-range correlations in epigenetic data*. Genome Biology,16:180, 2015, doi:10.1186/s13059-015-0741-y



## Data format
The data are saved as tab-delimited text files. The first three columns represent the genomic coordinates of the bin, the fourth column reports the value of the eigenvector for the bin, and the fifth column categorizes the bin as "open" or "closed" (A and B compartment respectively). 
```{}
chr    start    end    eigen    domain
chr1	500000	599999	-0.448558697994734	open
chr1	600000	699999	-0.317063576958963	open
chr1	700000	799999	-0.0518659472420911	open
chr1	800000	899999	0.0711965336724111	closed
chr1	900000	999999	0.098443079780858	closed
chr1	1000000	1099999	-0.051011778069161	open
chr1	1100000	1199999	-0.318273718360445	open
chr1	1200000	1299999	-0.53951736779136	open
chr1	1300000	1399999	-0.585600098287715	open

```

## Description of the files

| Files        | Description  | Reference Dataset
| ------------- |-------------| ------------- |
| hic_compartments_100kb_ebv_2013.txt     | Calculated A/B compartments for GM12878 dataset | [1] | 
| hic_compartments_100kb_ebv_2014.txt | Calculated A/B compartments for Hi-C GM12878 dataset | [2] |
| hic_compartments_100kb_imr90_2013.txt | Calculated A/B compartments for Hi-C IMR90 dataset | [3] |
| hic_compartments_100kb_imr90_2013.txt | Calculated A/B compartments for Hi-C IMR90 dataset | [2] |
| dnase_compartments_100kb_ebv.txt | Estimated A/B compartments from DNase EVBV dataset | [4] |
| dnase_compartments_100kb_imr90.txt | Estimated A/B compartments from DNase IMR90 dataset | [5] |
| meth_compartments_100kb_ebv.txt | Estimated A/B compartments from Methylation EBV dataset | [6] |
| meth_compartments_100kb_fibro.txt | Estimated A/B compartments from Methylation Fibroblast dataset | [7] |


## Scripts

The code used to generate A/B compartments from 450k methylation array data is implemented in the `compartments()` function of the devel version of [minfi](https://github.com/kasperdanielhansen/minfi/blob/master/R/compartments.R) on GitHub.

## Visualization 

The script [visualization.R](https://github.com/Jfortin1/TCGA_AB_Compartments/blob/master/scripts/visualization.R) is a script to load the data into R and create a barplot of the eigenvector values (see image above), as well as a little function called `convert2GRanges()` that will convert the data to a GRanges object for convenience. Positive and negative values represent closed and open domains respectively. 

## Note about preprocessing

## References

[1] Selvaraj S, Dixon JR, Bansal V, Ren B. Whole-genome haplotype
reconstruction using proximity-ligation and shotgun sequencing. Nat
Biotechnol. 2013;31:1111–18. doi:10.1038/nbt.2728.

[2] Rao SSP, Huntley MH, Durand NC, Stamenova EK, Bochkov ID,
Robinson JT, et al. A 3D map of the human genome at kilobase resolution
reveals principles of chromatin looping. Cell. 2014;159:1665–80.
doi:10.1016/j.cell.2014.11.021

[3] Dixon JR, Selvaraj S, Yue F, Kim A, Li Y, Shen Y, et al. Topological
domains in mammalian genomes identified by analysis of chromatin
interactions. Nature. 2012;485:376–80. doi:10.1038/nature11082.

[4] Degner JF, Pai AA, Pique-Regi R, Veyrieras JB, Gaffney DJ, Pickrell JK,
et al. DNase sensitivity QTLs are a major determinant of human
expression variation. Nature. 2012;482:390–4. doi:10.1038/nature10808

[5] Bernstein BE, Stamatoyannopoulos JA, Costello JF, Ren B, Milosavljevic
A, Meissner A, et al. The NIH roadmap epigenomics mapping consortium.
Nat Biotechnol. 2010;28:1045–8. doi:10.1038/nbt1010-1045

[6] Heyn H, Moran S, Hernando-Herraez I, Sayols S, Gomez A, Sandoval J,
et al. DNA methylation contributes to natural human variation. Genome
Res. 2013;23:1363–72. doi:10.1101/gr.154187.112.

[7] Wagner JR, Busche S, Ge B, Kwan T, Pastinen T, Blanchette M. The
relationship between DNA methylation, genetic and expression
inter-individual variation in untransformed human fibroblasts. Genome
Biol. 2014;15:37. doi:10.1093/bioinformatics/bth088.

