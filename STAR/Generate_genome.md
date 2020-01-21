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

# THE "STAT" PART *what you really want*
So before using this software, you will need to generate the genome indices. If you don't know how, don't worry, I don't know either. I think there is a command might be useful to you.

```
# Go to your workplace
cd yourworkplace
# create a genome indices folder
mkdir genome
# download Human dna lib (I think)
wget ftp://ftp.ensembl.org/pub/release-79/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
gunzip Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
STAR --runThreadN 50 --runMode genomeGenerate --genomeDir ./genome --genomeFastaFiles ./Homo_sapiens.GRCh38.dna.primary_assembly.fa 
```
*This might take a while which depends how many cores you have.*


Here is the bash command

After that you can try to see what will happen by implementing this
```
STAR --runThreadN 50 --genomeDir /mnt/Tank/junfan/project/STAR/genome --sjdbGTFfile /mnt/Tank/junfan/project/STAR/Homo_sapiens.GRCh38.79.gtf --sjdbOverhang 100 --readFilesIn SRR7191196_1.fastq SRR7191196_2.fastq 
```
