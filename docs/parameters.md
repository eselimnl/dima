## 3.1. Input file
DiMA only uses multiple sequence alignment (protein sequences; DNA should also work) in (aligned) FASTA (*.afa* or *.fas*) format. Any existing, published alignment tool can be used to produce the MSA, such as MAFFT or MUSCLE, as long as the aligned sequences are provided to DiMA as input in (aligned) FASTA format.  

### 3.1.1 MSA preparation workflow
(Figure-15)=
```{image} images/MSA_workflow.png
:alt: entropy_calculation
:class: bg-primary
:align: center
```
**Sequence Collection**

MSA for DiMA begins with the careful retrieval of sequences from at least one reliable data source. When working with multiple data sources, the retrieved sequences should be concatenated into a single FASTA file for consistency and ease of analysis. Sequences can be retrieved as full-genome data and subsequently separated using a BLASTp search. Alternatively, if the database supports it (e.g., NCBI Virus), sequences can be directly retrieved in their separated form. Adding metadata to the sequence headers is crucial, as it provides essential context for each sequence, aiding in downstream analysis.

**Sequence Cleaning and Deduplication**

Irrelevant sequences in your database can hinder analysis, and identifying them can be challenging. These sequences may not meet the specific criteria required for your study, such as host, geography, or other factors. A quick check involves verifying the species taxonomy lineage to ensure all records are correct. Sometimes, irrelevant sequences become apparent during alignment when a sequence doesn't align well with others, indicating it may be an outlier needing removal. While we assume the initial sequencing was done correctly, BLAST can help catch outliers by flagging hits that are significantly different. However, in cases where you skip BLAST, such as with flu viruses where protein sequences are directly downloaded from databases, you might miss the opportunity to remove these outliers.

To eliminate redundant data, run CD-HIT to remove 100% duplicate sequences, whether they are full-length duplicates or subsets of another sequence. You can also cluster sequences at a lower identity threshold, like 90%, to group similar sequences together. CD-HIT is confirmed to handle subset duplicates effectively, ensuring reliable deduplication.

**MSA**

After extracting individual protein sequences, you can proceed with the alignment process. MSA is a heuristic method, and while you could rely on a single alignment tool, it's often beneficial to test multiple tools to determine which provides the most reliable results for your specific dataset. However, consistency is key—if you use multiple tools, apply them uniformly across all proteins and ultimately choose the best alignment for further analysis.

In literature, it's common to see just one alignment tool being used, especially when dealing with relatively conserved viruses. However, for more diverse viruses, like HIV-1 or different subtypes of influenza, different tools might perform better for different proteins. If multiple tools are used, this choice must be justified clearly in any publication, supported by benchmarks against existing alignments.

**Alignment QC**
- Manual Inspection to Identify Mismatches: Alignment anchors or conserved blocks can guide manual inspection by providing reference points within the alignment. This helps ensure that regions between these anchors are correctly aligned. For misaligned sequences, search for similar sequences within the alignment to determine the correct positioning. Address issues block by block to systematically correct the alignment.
- Use of Auxilary Tools: Several auxiliary tools, such as GUIDANCE (Penn et al., 2010), SATe (Liu et al., 2009), HoT (Landan and Graur, 2008), Gblocks (Castresana, 2000), and SuiteMSA (Thompson et al., 2002), have been developed to facilitate this process. These tools assist in improving alignment quality by providing metrics for alignment confidence or by refining the alignment to reduce errors. However, they do not entirely eliminate the need for manual inspection.
- Dealing with Mismatches: Mismatches may indicate misalignment. If a mismatched sequence appears only in one sequence, use BLAST to check its validity. If it's an outlier (e.g., matching bacteria instead of the target organism), consider removing that part or the entire sequence, especially if it's at the beginning or end. For mismatches in the middle, it’s safer to delete the entire sequence, although careful inspection is needed.

## 3.2. Parameters
 ### 3.2.1. Sample name
  Name of sequence to be analysed. 
 ### 3.2.2. Low support threshold
  The support is defined as the number of sequences at a given *k-mer* position that do not harbor a gap and unknown and/or ambiguous nucleotide base and amino acid residue. Positions below a statistical support of 100 sequences (default) are defined as of low support. The user has the flexibility to set the threshold for low support.
 ### 3.2.3. K-mer length
  Select a *k-mer* window size that is appropriate for the analysis.\ 
While the minimum applicable size is 3, the maximum can equal to the alignment length of the uploaded input file. By default, DiMA uses a window size of nine (9; nonamer; 9-mer) to evaluate the viral diversity with respect to cellular immune response.
 ### 3.2.4. Header format to include metadata
  This optional functionality allows annotation of the distinct sequences at each *k-mer* position  with respective cognate sequence metadata, such as collection date, geographical location, isolation host. Simply, it parses the information on the sequence header (definition/description line). 


```{note}
Example of a definition line: >ATY74257.1 |2017-03-02|China: Kunming|Homo sapiens
```

Because the format of metadata varies between databases, DiMA has relied on the format of [NCBI Virus](https://www.ncbi.nlm.nih.gov/labs/virus/vssi/#/). 
