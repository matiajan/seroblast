# seroblast


A simple BASH script for identification of Streptococcus suis serotype from draft genome

Database of serotype-specific sequences is modified from SsuisSerotyping_pipeline (https://github.com/streplab/SsuisSerotyping_pipeline). Unlike SsuisSerotyping_pipeline, the seroblast is dependent only on local blast installation.

1. install blast locally

for Ubuntu and Debian users

sudo apt install ncbi-blast+

others https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download

2. create /blastdb directory and put file Ssuis_Serotyping3v3.fasta here

3. build blast database in /blastdb

makeblastdb -in Ssuis_Serotyping3v3.fasta -parse_seqids -blastdb_version 5 -title "SsuisSerotype" -dbtype nucl

4. edit line 5 in seroblast4.1 script to locate blast database in your correct path (for example /home/$HOME/blastdb) and make the script executable

chmod +x seroblast4.1

5. run seroblast4.1 from directory containing your S. suis draft genomes named *.fasta

6. read output serotypes.tsv (tab separated columns). The columns are: sample, serotype identified, cps gene identified, evalue, score, ppos for cps gene identified, cpsk allele identified, evalue, score, ppos for cpsk allele
