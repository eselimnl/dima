![workflow](images/workfloww.jpg)

: **Figure 2. Workflow schema.** ***Input:*** Viral protein sequences, typically obtained from publicly available databases (NCBI virus and GISAID, among others), aligned and submitted to DiMA in aligned FASTA (*.afa)* format. ***Process:*** DiMA provides a quantitative measure of sequence diversity by use of Shannon’s entropy, applied via a user-defined *k-mer* sliding window. Further, the entropy value is corrected for sample size bias by applying a statistical adjustment (Lipinski’s rule). Additionally, DiMA further interrogates the diversity by dissecting the entropy value at each *k-mer* position to various distinct *k-mer* sequences that are classified into diversity motifs (index, major, minor and unique; see Section 3 for the definition of the diversity motifs) based on their incidence. ***Output:*** The entropy values, diversity motifs, and each of the *k-mer* corresponding metadata is plotted to provide a panoramic overview of the protein sequence diversity. 

# 2.1. Entropy algorithm 

```{image} images/entropy_algorithm.svg
:alt: entropy_calculation
:class: bg-primary
:height: 1600px
:width: 1000px
:align: center
```
<a></a> 
: **Figure 3. Entropy algorithm.** Bla bla bla


# 2.2. Frontend/Backend Frameworks

Python FastAPI utilized for DiMA webserver Backend. 
ReactJS utilized for DiMA webserver Frontend.

