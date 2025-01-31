# GNRS (Graph nonreference sequences)
Pangenome of human nonreference sequences from population-scale long-read sequencing   

---
```
 ___________         ____         __         ____________         __________
|  _________|       |    \       |  |       |  ________  |       |   ____   | 
|  |                |  |\ \      |  |       |  |      |  |       |  |    |__|
|  |                |  | \ \     |  |       |  |      |  |       |  |        
|  |   _____        |  |  \ \    |  |       |  |______|  |       |  |_______  
|  |  |__   |       |  |   \ \   |  |       |   ___   ___|       |_______   |
|  |     |  |       |  |    \ \  |  |       |  |   \  \           __     |  |          
|  |     |  |       |  |     \ \ |  |       |  |    \  \         |  |    |  |           
|  |_____|  |       |  |      \ \|  |       |  |     \  \        |  |____|  |            
|___________|       |__|       \____|       |__|      \__\       |__________|   

```
---
## Description 
In order to make sure the results are reproduceable, the pipeline is performed using framework [**Snakemake**](https://snakemake.readthedocs.io/en/stable/) coupled with the environment conducted by [**Anoconda**](https://www.anaconda.com/). And the pipeline can be used in other cohort with long-read sequencing.

The workflow of GNRS on the population-scale long-read sequencing are below:
![image](https://user-images.githubusercontent.com/42490165/187627086-e860577c-1152-4070-a7b9-af615337131a.png)


### Schematic representation of GraphNRS
* a, Long-read sequencing data from different platforms are de novo assembled and polished. 
* b, The NRSs are anchored to GRCh38. Placed NRSs are clustered to select the representative NRSs, and unplaced NRSs are clustered after filtering out contaminants and centromeric repeats. Then, we merge the placed and the unplaced NRSs to obtain the nonredundant NRSs of the whole population. 
* c, vg is used to construct the graph pangenome, and NRS genotyping is performed for each NRS of the individual.

---
### Requirements
	
	1. wtdbg2 v2.5
	2. MarginPolish v1.3.0
	3. Hifiasm v0.16.1-r375
	4. NextPolish v1.4.0 
	5. QUAST v5.0.2
	6. AGE v0.4
	7. Kalign v3.3
	8. Jasmine v1.1.0
	9. vg toolkit v1.33.1
	10. GraphAligner v1.0.13
	11. snakemake v7.2.1

---
### Configure the environment
Install the software and configure the environment:
* [**wtdbg2 v2.5**](https://github.com/ruanjue/wtdbg2)
* [**MarginPolish v1.3.0**](https://github.com/UCSC-nanopore-cgl/MarginPolish)
* [**Hifiasm v0.16.1-r375**](https://github.com/chhylp123/hifiasm)
* [**NextPolish v1.4.0**](https://github.com/Nextomics/NextPolish)
* [**QUAST v5.0.2**](https://github.com/ablab/quast)
* [**AGE v0.4**](http://sv.gersteinlab.org/age/)
* [**Kalign v3.3**](https://github.com/TimoLassmann/kalign)
* [**Jasmine v1.1.0**](https://github.com/mkirsche/Jasmine)
* [**vg toolkit v1.33.1**](https://github.com/vgteam/vg)
* [**GraphAligner v1.0.13**](https://github.com/maickrau/GraphAligner)
* [**snakemake v7.2.1**](https://snakemake.readthedocs.io/en/stable/)

Please note the comments in the pipeline. Change the sample path in the configuration file.


---
### Quick start for the pipeline
usage: snakemake -p -s GNRS.pipeline.py --configfile GNRS.pipeline.yaml --cores

Our pipeline works for any species with a reference genome. We tested the pipeline on yeast dataset.
* S288C reference genome: [**GCF_000146045.2**](https://www.ncbi.nlm.nih.gov/assembly/GCF_000146045.2/)
* ONT: Whole genome sequencing of 741-7-Nanopore [**SRR18365591**](https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18365591/SRR18365591)
* CLR: Whole genome sequencing of JSC20-1_Pacbio [**SRR18365586**](https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18365586/SRR18365586)
* HiFi: HiFi-Seq of S288C [**SRR18210286**](https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18210286/SRR18210286)
* NGS: Whole genome sequencing of 741-7-NGS [**SRR18365940**](https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18365940/SRR18365940)
* NGS: BGISEQ of S288C [**SRR17374239**](https://sra-downloadb.be-md.ncbi.nlm.nih.gov/sos2/sra-pub-run-34/SRR017/17374/SRR17374239/SRR17374239.1)

The results of the tests are in the output folder.

---
### Datasets generated from GNRS
We provided the NRS callsets of the 539 individuals produced by GNRS from three different long-read sequencing platforms. (i.e. PacBio CLR, PacBio HiFi, and ONT). 
The sequences and genotypes of the NRSs are publicly available at the National Genomics Data Center (NGDC), China National Center for Bioinformation (CNCB) with project accession number [**PRJCA007976**](https://ngdc.cncb.ac.cn/bioproject/browse/PRJCA007976). 
The sequences and genotypes of the placed NRSs are available with accession number [**GVM000324**](https://ngdc.cncb.ac.cn/gvm/getProjectDetail?project=GVM000324). 
And the sequences of the unplaced NRSs are under the accession number [**GWHBHSK00000000**](https://ngdc.cncb.ac.cn/gwh/Assembly/24529/show).




---
### Citation
Wu Z, Li T, Jiang Z, Zheng J, Gu Y, Liu Y, Liu Y, Xie Z. Human pangenome analysis of sequences missing from the reference genome reveals their widespread evolutionary, phenotypic, and functional roles. Nucleic Acids Res. 2024 Feb 14:gkae086. doi: 10.1093/nar/gkae086. Epub ahead of print. PMID: 38364871.


---
### Contact
For advising, bug reporting and requiring help, please post on [Github Issue](https://github.com/Kmanjor/GNRS/issues) or contact tli.aioniya@gmail.com.



