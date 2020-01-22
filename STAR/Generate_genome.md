# How to do that

Haha, you are as lazy as I am.

So basically, what I did is just copy and paste the command lines in that documentation. If you want, just follow the thing I did. Hope it is a right way to do.

## Choose a SRR data
Firstly, you will need to download dataset by using sra (which will be written shortly). The id I used is SRR7191196.

## Download the dataset
```
fasterq-dump SRR7191196
```
If you want to download a lot of files, maybe this documentation (%TODO: upload the jupyter notebook) would be helpful.

## FASTQC (maybe will be mention in the notebook as well)
The reason to do FASTQC is to see the quality of the dataset (I think, correct me if I am wrong as I am new in this stage).

# THE "STAT" PART 
*what you really want*
## Genome indices
So before using this software, you will need to generate the genome indices. If you don't know how, don't worry, I don't know either. I think these commands below might be useful.

```
# Go to your workplace
cd yourworkplace

# create a genome indices folder
mkdir genome

# download Human dna lib (I think)
wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_33/GRCh38.primary_assembly.genome.fa.gz
gunzip GRCh38.primary_assembly.genome.fa.gz

# generate genome indices
STAR --runThreadN 80 --runMode genomeGenerate --genomeDir ./genome --genomeFastaFiles GRCh38.primary_assembly.genome.fa --sjdbGTFfile gencode.v33.primary_assembly.annotation.gtf --sjdbOverhang 100
```
~~change 14.14 22 Jan from summer school web `STAR --runThreadN 50 --runMode genomeGenerate --genomeDir ./genome --genomeFastaFiles ./GRCh38.primary_assembly.genome.fa
`~~
%TODO: delete Genome indices after
*This might take a while which depends how many cores you have.*

~~In these commands, we installed kind of gene library (`Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz`) I think it is a way to get indices and it can be done by using STAR.~~

Sorry, I used a wrong version. The updated one can be found from [GENcode](https://www.gencodegenes.org/human/) (the last file in Fasta files).

## Use GTF file to do something "cool"

After that you can try to see what will happen by implementing this
```
STAR --runThreadN 50 --genomeDir /mnt/Tank/junfan/project/STAR/genome --sjdbGTFfile /mnt/Tank/junfan/project/STAR/Homo_sapiens.GRCh38.79.gtf --sjdbOverhang 100 --readFilesIn SRR7191196_1.fastq SRR7191196_2.fastq 
```
Questions:
- [ ] It seems that the readFiles should be two files, so are those input files corresponding to _1 and _2 fastq files we got?

