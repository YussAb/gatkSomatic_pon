# Mutect2 Panel of Normals Workflow
Nextflow implementation for Mutect2 Panel of Normals subworkflow, based on latest [Mutect2 Best Practices guidelines](https://software.broadinstitute.org/gatk/documentation/article?id=24057)


## Quick Start

Required Arguments:

| argument       | value | 
|:--------------:|:-----| 
| `normal_bam_folder` | a path to the input folder with `bam` and `.bai` files| 
| `ref`   | a path to the unzipped fasta reference file, used to map the bam files|
| `ref_index`   | a path to `fasta.fai` index of the reference reference file, used to map the bam files|
| `ref_dict`| a path to the `.dict` file generated from the `fasta` reference file|
| `interval_list`| a path to the interval list file, with coordinate ranges defined per line as `chr:start-end`, must have suffix `.list`|
| `af_only_gnomad_vcf`| a path to the external resource unzipped vcf file [found here](http://bioinfo5pilm46.mit.edu/software/GATK/resources/) from the Genome Aggregation Database (gnomAD).|
| `af_only_gnomad_vcf_idx`| a path to the external resource unzipped vcf file index generated with `gatk IndexFeatureFile` .|
  
To test the pipeline with your input folder of bam files you can run:

```nextflow
# Clone the repository
git clone https://github.com/cgpu/Mutect2PanelofNormalsWorkflow-nf

# cd into the repo folder 
cd Mutect2PanelofNormalsWorkflow-nf

# Execute nextflow run command with example input parameters
nextflow main.nf \ 
--normal_bam_folder path/to/input/folder/  \ 
--ref ref.fasta \ 
--ref_index ref.fasta.fai \ 
--ref_dict  ref.dict\ 
--interval_list WES_interval.list \ 
--af_only_gnomad_vcf  af-only-gnomad.raw.sites.hg19.vcf \ 
--af_only_gnomad_vcf_idx  af-only-gnomad.raw.sites.hg19.vcf.idx \ 
-with-docker broadinstitute/gatk:latest
```

