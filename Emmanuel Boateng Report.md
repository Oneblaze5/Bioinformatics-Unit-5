This report was created by Emmanuel Boateng

# Session 1: Annotation of coding sequences
---

## 1.1 How i solved the exercises:


###  EX1: I unzipped the reference proteome and used makeblastdb to format it into searchable protein database. The process made 15719 sequences.

```bash
makeblastdb -dbtype prot -in uniprot_Atha.fasta
```




### EX2: I performed a blastp search using the ARF6 protein sequence and blastx search using the corresponding transcript sequence against the formatted database. The outputs were saved to test.faa.blast and test.fna.blast. 

```bash
blastp -query test.faa -db uniprot_Atha.fasta -out test.faa.blast
blastx -query test.fna -db uniprot_Atha.fasta -out test.fna.blast
```




### EX3: I examined the default pairwise alignment format, which shows specific faa matches between the query and subject.

```bash
blastp -query test.faa -db uniprot_Atha.fasta -out test.faa.blast
blastx -query test.fna -db uniprot_Atha.fasta -out test.fna.blast
```


### EX4:  Blastp and blastx were compared and they showed identical top hits.

### EX5: I ran psiblast for 3 iterations to create a PPSM saved in profile.out.

```bash
psiblast -query test.faa -db uniprot_Atha.fasta -num_iterations 3 -out_pssm profile.out
```


### EX6: I created multiple sequence alignment using clustalo then  built an HMM with hmmbuild and searched for the proteome using hmmsearch to identify family members.

```bash
clustalo -i family.fasta -o test_aligned.aln --outfmt=fasta
hmmbuild test.hmm test_aligned.aln
hmmsearch test.hmm uniprot_Atha.fasta > hmm_report.txt
```


### EX7: I identified structural homologs in the PDB using HHpred web server. I found high-probability matches to ARD DNA-binding domains.

### EX8: I used eggNOG mapper to identify and  the protein belongs to ARF6 group and is categorized under transcription category (K)

### EX9: I used QuickGO to compare leaf development across species. Arabidopsis showed more experimental evidence with 137 products which is more than Prunus with 4 products and Zea mays with 5 products.

### EX10: I retrieved the 3D structure from AlfaFold Database using ID Q9ZTZ8. It showed high confidence (pLDDT > 90) in core domain and lower confidence in disoredered regions.

## 1.2 Problems  faced:

### 1:Docker running was given a no name, so i have to watch the recorded session to correct the error

### 2: Git Synchronization gave an error as  my token has expired, i then created a  new token to enable me push assignment to my repo.

### 3: Clustalo on test.faa falied so resorted to chatgtp and it recommended me to create another file with related sequences derived from BLAST results so that i can comapare the two sequences.

### 4: AlphaFold engine wasn't working as expected , was showing no results at first then it worked normally.
### 5: I went back to  the recorded session and relied on Chatgtp whenever i got stuck.

## References

### BLAST Help/FAQ, visited 03/01/2026.

### QuickGO Term GO:0048366, visited 03/01/2026.

### AlphaFold Protein Structure Database, visited 03/03/2026.
