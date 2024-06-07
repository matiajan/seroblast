# seroblast


A simple BASH script for identification of Streptococcus suis serotype from draft genome

Database of serotype-specific sequences is modified from SsuisSerotyping_pipeline (https://github.com/streplab/SsuisSerotyping_pipeline). Unlike SsuisSerotyping_pipeline, the seroblast is dependent only on local blast installation.

1. install blast locally

for Ubuntu and Debian users

sudo apt install ncbi-blast+

others https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download

2. create /blastdb directory and put file Ssuis/Ssuis_Serotyping6-NK-V3.fasta here

3. build blast database in /blastdb

makeblastdb -in Ssuis/Ssuis_Serotyping6-NK-V3.fasta -parse_seqids -blastdb_version 5 -title "SsuisSerotype" -dbtype nucl

4. edit line 5 in seroblast6.3.1 script to locate blast database in your correct path (for example /home/$HOME/blastdb) and make the script executable

chmod +x seroblast6.3.1

5. run seroblast6.3.1 from directory containing your S. suis draft genomes named *.fasta

6. read output serotypesV6.3.1.tsv (tab separated columns). The columns are: sample	serotype	cps_gene	cps_evalue	cps_score	cps_ppos	cpsk	cpsk_evalue	cpsk_score	cpsk_ppos	recN	recN_evalue	recN_score	recN_ppos
