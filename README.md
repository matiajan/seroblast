# seroblast
simple BASH script for identification of S. suis serotype from draft genome

Database of serotype-specific sequences is modified from SsuisSerotyping_pipeline. Unlike SsuisSerotyping_pipeline, the seroblast is dependent only on local blast installation.

Translation to English will follow.

1. install blast 

2. create /blastdb directory and put file Ssuis_Serotyping3v3.fasta here
 
3. build blast database in /blastdb

makeblastdb -in Ssuis_Serotyping3v3.fasta -parse_seqids -blastdb_version 5 -title "SsuisSerotype" -dbtype nucl

3. edit line 5 in seroblast4.1 script to locate blast database in your correct path (/home/$HOME/blastdb)

4. run seroblast4.1 from directory containing your S. suis draft genomes named *.fasta

5. read output serotypes4.1.tsv (tab separated columns). The columns are: sample, serotype identified, cps gene identified, evalue, score, ppos for cps gene identified, cpsk allele identified, evalue, score, ppos for cpsk allele  
