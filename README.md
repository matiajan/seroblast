# seroblast


A simple BASH script for identification of Streptococcus suis serotype from draft genome

Database of serotype-specific sequences is modified from SsuisSerotyping_pipeline (https://github.com/streplab/SsuisSerotyping_pipeline). Unlike SsuisSerotyping_pipeline, the seroblast is dependent only on local blast installation.

1. install blast locally

for Ubuntu and Debian users

sudo apt install ncbi-blast+

others https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download

2. create /blastdb directory and put file Ssuis/Ssuis_Serotyping8v2-NK-V2v3.fasta here

3. build blast database in /blastdb

makeblastdb -in Ssuis/Ssuis_Serotyping8v2-NK-V2v3.fasta -parse_seqids -blastdb_version 5 -title "SsuisSerotype" -dbtype nucl

4. edit line 5 in Ssuisseroblast8v2.NK-V2v4 script to locate blast database in your correct path (for example /home/$HOME/blastdb) and make the script executable

chmod +x Ssuisseroblast8v2.NK-V2v4

5. run Ssuisseroblast8v2.NK-V2v4 from directory containing your S. suis draft genomes named *.fasta

6. read output Ssuisseroblast8v2.NK-V2v4 (tab separated columns). The columns are: "sample	serotype	cps_gene	cps_evalue	cps_score	cps_ppos	modifying_gene	cps_evalue	cps_score	cps_ppos	cpsk	cpsk_evalue	cpsk_score	cpsk_ppos	recN	recN_evalue	recN_score	recN_ppos". As a modifying_gene we understand gene potentially able to modify antigenic structure of capsular polysaccaride.
