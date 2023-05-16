---
layout: lesson
root: .
---
An AWS instance is a virtual machine that runs on AWS *physical* servers. An AWS instance is created by combining two main components: (1) a **software environment**, typically an operating system (such as Windows, Linux or MacOS), and data and software applications of interest to end users; and (2) a virtualised (software-emulated) **hardware platform** that is mainly defined by the number of processors and the amount of main memory to be made available to the operating system.  

A software enviroment is called an **Amazon Machine Image** (AMI) in AWS terminology, and there is plenty of them to choose from. Some are configured as database servers, others as web servers, either with Windows or Linux, among many others. The virtualisation of hardware platforms allows AWS to run any instance on any *physical* server with enough capacity. This makes it possible to better use physical resources and hence offer competitive prices to users, among many other benefits that derive from virtualisation: representing and managing physical resources as software.

This lesson will guide you to create and manage **your own AWS instance**. You will create your AWS instance by combining one of the Cloud-SPAN AMIs with a virtualised hardware platform. Virtualised hardware platforms are called **instance types** in AWS terminology. The table below shows the combination of Cloud-SPAN AMI and instance type that is used to  create the AWS instances for each Cloud-SPAN workshop:

> ## Cloud-SPAN AWS instances workshop configuration
>
> | Workshop      | Cloud-SPAN AMI |  Intance type --- costs as at May 2023|
> |---------------|-------------|---------------|
> | [Prenomics](https://cloud-span.github.io/prenomics00-intro/)    | Genomics AMI: 30GB secondary storage, **free**, as AWS Free tier is 30 GB-month for 1 year | **t3.small**: US $0.0208/hour, 2 processors, 2GB main memory|
> | [Genomics](https://cloud-span.github.io/00genomics/)    | Genomics AMI  | **t3.small** |
> | [Metagenomics](https://cloud-span.github.io/metagenomics00-overview/)  | Metagenomics AMI with Benchmarking data: 240GB secondary storage | **t3.2xlarge**: US $0.3648/hour, 8 processors, 32GB main memory |
> | [Metagenomics for Environmental Scientists](https://cloud-span.github.io/nerc-metagenomics00-overview/)  | Metagenomics AMI with Environmental data: 240GB secondary storage  | **t3.2xlarge**|
{: .callout}

If you create your AWS instance with any of the Cloud-SPAN combinations in that table, **you will incur some cost**. The cost of an AWS instance is divided into two components: **storage cost** and **compute cost**. The storage cost is determined by the size of the AMI in GB of secondary storage. The compute cost is determined by the number of processors and main memory of the instance type that is used. If you use the **Genomics AMI - t3.small** combination, you will only incur the compute cost ($0.0208 * 24hours =  $0.4992 daily) --- you **will not incur storage** cost because it will be covered by the AWS Free-tier, which includes 30GB-month for 12 months from opening your AWS account, see details in the next lesson [AWS Costs Explained](https://cloud-span.github.io/create-aws-instance-3-costs-explained/). You can also eliminate the compute cost through using the **Genomics AMI - t2.micro** combination to create your AWS instance, as the instance type t2.micro is included in the Free-tier. We have used such combination and performance is reasonable in general; only a few analyses will be somewhat slow but you can plan to run such analyses overnight.

We don't recommend using smaller instance types with the Metagenomics AMIs as the datasets used are relatively large and processing them does require more resources. You may be able to get some AWS credit to reduce or avoid the cost of your Metagenomics instance, see the episode [The AWS Cloud Credit for Research](https://cloud-span.github.io/create-aws-instance-3-costs-explained/02-research-credits/index.html) in the next lesson.

AWS uses public-key cryptography to secure access to AWS instances. You will be shown how to use this and other related technologies to configure, use and manage your AWS instance remotely and securely from your laptop or desktop machine.

> ## **Genomics AMI** software configuration 
> The Cloud-SPAN Genomics AMI is configured with Linux Ubuntu 20.04, 'omics data, and the following 'omics software analysis tools:
>
> |SOFTWARE       |VERSION      |   DESCRIPTION|
> |---------------|-------------|---------------|
> | bcftools      |1.14-3       | Utilities for variant calling and manipulating VCFs and BCFs.|
> | bwa          | 0.7.17-r1188 | Mapping DNA sequences against reference genome.|
> | cutadapt     | 3.5          | Similar to bcftools|
> | fastqc       | 0.11.9       | Quality control tool for high throughput sequence data.|
> | samtools     | 1.13         | Visualization and interactive exploration of large genomics datasets.|
> | trimmomatic  | 0.39         | A flexible read trimming tool for Illumina NGS data.|
{: .solution}

> ## **Metagenomics AMIs** software configuration
> Both Cloud-SPAN Metagenomics AMIs are configured with Linux Ubuntu 20.04 and the 'omics software analysis tools below, but are configured with different data.
>
> |SOFTWARE       |VERSION      |   DESCRIPTION|
> |---------------|-------------|---------------|
> | bwa     	  | 0.7.17-r1188| mapping DNA sequences against reference genome.	|
> | checkm  	  | 1.2.1	    | set of tools for assessing the quality of genomes recovered from isolates, single cells, or metagenomes.	|
> | fastqc 	      | 0.11.9	    | quality control tool for high throughput sequence data. |
> | flye  	      | 2.9.1-b1780	| assembler for single molecule sequencing reads, such as those produced by PacBio and Oxford Nanopore Technologies	|
> | kraken  	  | 2.1.2	    | a system for assigning taxonomic labels to short DNA sequences, usually obtained through metagenomic studies	|
> | kraken-biom   | 1.0.1 	    | creates BIOM-format tables 	|
> | medaka  	  | 1.7.2	    | a tool to create a consensus sequence from nanopore sequencing data	|
> | metabat2 	  | 2:2.15	    | binning tool to reconstruct single genomes from metagenome assemblies 	|
> | metaquast 	  | 5.2.0 	    | evaluates and compares metagenome assemblies based on alignments to close references	|
> | nanoplot 	  | 1.40.2	    | plotting tool for long read sequencing data and alignments	|
> | pilon  	      | 1.24	    | integrated software tool for comprehensive microbial genome assembly improvement and variant detection |
> | prokka  	  | 1.14.5	    |  software tool to annotate bacterial, archaeal and viral genomes quickly and produce standards-compliant output files	|
> | samtools 	  | 1.16.1-33   | Visualization and interactive exploration of large genomics datasets	|
> | seqkit        | 2.3.0	    | a cross-platform and ultrafast toolkit for FASTA/Q file manipulation 	|	
{: .solution}

