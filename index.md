---
layout: lesson
root: .
---
An AWS instance is a virtual machine that runs on AWS *physical* servers. An AWS instance is created by combining two main components: (1) a software environment, typically an operating system such as Windows, Linux or MacOS, and (2) a virtualised (software-emulated) hardware platform that is mainly defined by the number of processors and the amount of memory to be made available to the operating system.  

A software enviroment is called an Amazon Machine Image (AMI) in AWS terminology, and there is plenty of them to choose from. Some are configured as database servers, others as web servers, either with Windows or Linux, among many others. The virtualisation of hardware platforms allows AWS to run any instance on any *physical* server with enough capacity. This makes it possible to better use physical resources and hence offer competitive prices to users, among many other benefits that derive from virtualisation: representing and managing physical resources as software.

You will create your instance by combining the Cloud-SPAN AMI with a virtualised hardware platform that, together, are *Free-tier* eligible, meaning that you will **not** incur billing costs for 12 months since you open your AWS account. You will learn about the AWS Free tier and other billing aspects relevant to your AWS account in the next lesson [AWS Costs Explained](https://cloud-span.github.io/create-aws-instance-3-costs-explained/). 

The Cloud-SPAN AMI is configured with Linux Ubuntu 20.04, 'omics data, and the following 'omics analysis tools:

|SOFTWARE       |VERSION      |   DESCRIPTION|
|---------------|-------------|---------------|
| fastqc       | 0.11.9      |    Quality control tool for high throughput sequence data.|
| trimmomatic  | 0.39          |  A flexible read trimming tool for Illumina NGS data.|
| bwa          | 0.7.17-r1188  |  Mapping DNA sequences against reference genome.|
| samtools     | 1.13          |  Visualization and interactive exploration of large genomics datasets.|
| bcftools      |1.14-3        |  Utilities for variant calling and manipulating VCFs and BCFs.|
| cutadapt     | 3.5           |  Similar to bcftools|

AWS uses public-key cryptography to secure access to AWS instances. You will be shown how to use this and other related technologies to configure, use and manage your AWS instance remotely and securely from your laptop or desktop machine.
