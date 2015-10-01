![alt tag](https://raw.github.com/jfortin1/TCGA_AB_Compartments/master/figures/try.png)

# HiC_AB_Compartments

Analysis of Hi-C data has shown that the genome can be divided into two compartments
called A/B compartments. These compartments are cell-type specific and are
associated with open and closed chromatin. In our recent Genome Biology paper, ([Fortin et al., 2015](http://www.genomebiology.com/2015/16/1/180)), we showed that we can estimate A/B compartments from 450k methylation array data as well as DNase hypersensitivity data. This GitHub repo contains the genome-wide A/B compartments computed for different Hi-C datasets, as well as the A/B compartments estimatad from methylation and DNase data. All the data are at at resolution 100kb. For the A/B compartmentes estimated for 12 different cancer types from TCGA, please visit the following GitHub repo: [TCGA A/B compartments](https://github.com/Jfortin1/TCGA_AB_Compartments).

Please cite our Genome Biology paper if using these data:

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

| Files        | Description           | 
| ------------- |-------------| 
| BLCA     | Bladder Urothelial Carcinoma | 
| BRCA | Breast invasive carcinoma |
| COAD | Colon adenocarcinoma |
| HNSC | Head and Neck squamous cell carcinoma |
| KIRC | Kidney renal clear cell carcinoma |
| KIRP | Kidney renal papillary cell carcinoma |
| LIHC | Liver hepatocellular carcinoma |
| LUAD | Lung adenocarcinoma |
| LUSC | Lung squamous cell carcinoma |
| PRAD | Prostate adenocarcinoma |
| THCA | Thyroid carcinoma |
| UCEC | Uterine Corpus Endometrial Carcinoma |

## Scripts

The code used to generate A/B compartments from 450k methylation array data is implemented in the `compartments()` function of the devel version of [minfi](https://github.com/kasperdanielhansen/minfi/blob/master/R/compartments.R) on GitHub.

## Visualization 

The script [visualization.R](https://github.com/Jfortin1/TCGA_AB_Compartments/blob/master/scripts/visualization.R) is a script to load the data into R and create a barplot of the eigenvector values (see image above), as well as a little function called `convert2GRanges()` that will convert the data to a GRanges object for convenience. Positive and negative values represent closed and open domains respectively. 

## Note about preprocessing

