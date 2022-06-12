## 3.1. Input file
DiMA only uses multiple sequence alignment (protein sequences; DNA should also work) in (aligned) FASTA (*.afa* or *.fas*) format. Any existing, published alignment tool can be used to produce the MSA, such as MAFFT or MUSCLE, as long as the aligned sequences are provided to DiMA as input in (aligned) FASTA format.  
## 3.2. Parameters
 ### 3.2.1. Sample name
  Name of sequence to be analysed. 
 ### 3.2.2. Low support threshold
  The support is defined as the number of sequences at a given *k-mer* position that do not harbor a gap and unknown and/or ambiguous nucleotide base and amino acid residue. Positions below a statistical support of 30 sequences (default) are defined as of low support. The user has the flexibility to set the threshold for low support.
 ### 3.2.3. K-mer length
  Select a *k-mer* window size that is appropriate for the analysis.\ 
While the minimum applicable size is 3, the maximum can equal to the alignment length of the uploaded input file. By default, DiMA uses a window size of nine (9; nonamer; 9-mer) to evaluate the viral diversity with respect to cellular immune response.
 ### 3.2.4. Header format to include metadata
  This optional functionality allows annotation of the distinct sequences at each *k-mer* position  with respective cognate sequence metadata, such as collection date, geographical location, isolation host. Simply, it parses the information on the sequence header (definition/description line). 


```{note}
Example of a definition line: >ATY74257.1 |2017-03-02|China: Kunming|Homo sapiens
```

Because the format of metadata varies between databases, DiMA has relied on the format of [NCBI Virus](https://www.ncbi.nlm.nih.gov/labs/virus/vssi/#/). 
