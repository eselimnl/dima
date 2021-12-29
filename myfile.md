- {ref}`About<section-one>`
- {ref}`Browser compatibility<section-two>`
- {ref}`Workflow of DiMA<section-three>`
- {ref}`Input file and parameters<section-four>`
- {ref}`How to interpret the results<section-five>`
- {ref}`FAQs<section-six>`
- {ref}`Support<section-seven>`


(section-one)=
# About

Protein sequence diversity is one of the major challenges in the design of diagnostic, prophylactic and therapeutic interventions against viruses. DiMA is designed to facilitate the dissection of protein sequence diversity dynamics for viruses. DiMA provides a quantitative measure of sequence diversity by use of Shannon’s entropy, applied via a user-defined *k-mer* sliding window. Further, the entropy value is corrected for sample size bias by applying a statistical adjustment. Additionally, DiMA further interrogates the diversity by dissecting the entropy value at each *k-mer* position to various diversity motifs. The distinct *k-mer* sequences at each position are classified into the following motifs based on their incidence. Index is the predominant sequence, and all other distinct *k-mer*s are referred to as total variants, sub-classified into major variant (the predominant variant), minor variants (*k-mer*s with the incidence in between major and unique motifs) and unique variants (seen once in the alignment). Moreover, the description line of the sequences in the alignment can be formatted for inclusion of meta-data that can be tagged to the diversity motifs. DiMA enables comparative diversity dynamics analysis, within and between proteins of a virus species, and proteomes of different viral species.

(section-two)=
# Browser compatibility

![browserc](images/browserc.png)

(section-three)=
# Workflow of DiMA

![workflow](images/workflow.jpg)
**Figure 2**\
**Input:** Viral proteome sequences are obtained from publicly available databases (NCBI virus, GISAID, etc.) and submitted to DiMA as in aligned FASTA format.\
**Process:** DiMA applies a user-defined size of the *k-mer* sliding window approach. Kmer entropy is calculated by Shannon’s entropy formula defined for nonamers. Sample size bias is used to justify the entropy value (Default is 30 and sample size bias corrections are not being applied to low-support positions). 4 types of diversity motifs are created based on the incidence of the *k-mer* of a given position.\
**Output:** The entropy values, diversity motifs, and each of the *k-mer* corresponding metadata is plotted to provide a panoramic overview of the protein sequence diversity.

(section-four)=
# Input file and parameters

- **Input file**
DiMA only uses multiple sequence alignment (DNA or protein sequences) in FASTA format. Any alignment tool can be used to produce the MSA, such as MAFFT or MUSCLE as long as the input sequences provided to DiMA are in FASTA format. 
- **Parameters**
  - **Viral sequence name**\
  Name your protein analysis (such as Nucleoprotein, Matrix protein, Polymerase protein etc.) 
  - **Low support threshold**\
  The minimum required sequence support is to not be called “Low support” for each k-mer position. These positions are analyzed and tagged in the result to not misguide scientific interpretations.

```{note}
The default value is **30**.
```

  - **Kmer length**
  Select *k-mer* window size appropriate for the analysis.\ 
While the minimum applicable size is 3, the maximum is equal to the total number position in the uploaded alignment. By default, DiMA uses a window size of nine (9; nonamer) to evaluate the viral diversity with respect to cellular immune response.

  - **Header format to include metadata**
This optional functionality labels k-mers with corresponding metadata such as collection date, country origin, isolation host of the sequence. Simply, it parses the information on the sequence header (definition line).\
Example: *accession|collection date|country|isolation host*\
Because the format of metadata varies between databases, DiMA has relied on the format of NCBI Virus. 

(section-five)=
# How to interpret the results

- **Result presentation**

![sections](images/sectionss.png)

- **Section 1 (Summary statistics)**

Find a summary of information about your query: request ID, submission parameters, the total number of sequences in the alignment, and the number of low support positions. 
![section1](images/section1.png)

- **Section 2 (Proteome diversity)**

Entropy values indicate the level of variability at the corresponding k-mer positions, with zero representing completely conserved positions. Plots are responsive and dynamic, one can easily hover and see the approximate entropy value of the hovered position. 
![section2](images/section2.png)
```{note}
For a benchmark, the peak absolute entropy of 9.2 and total variants of 98% were observed for HIV-1 clade B [(Hu et al., 2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0059994). 
```

- **Section 3 (Diversity motifs)**

All sequences at each of the *k-mer* positions in the protein alignments were quantified and ranked based on the incidences of distinct sequences (as part of diversity motifs) present at the position, as described in [Hu et al. (2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0059994).
```{image} images/diversitymotifs.jpg
:alt: diversitymotifs
:class: bg-primary
:width: 300px
:align: center
```

Users can select a position from the “SELECTED POSITION” box located in the upper right corner.

```{image} images/section3.png
:alt: section3
:class: bg-primary
:width: 400px
:align: center
```

- **Section 4 (Metadata)**

If the header format is provided in the analysis parameters, DiMA will make a pie chart for each type of metadata.\
The user should select a *k-mer* from the selected position. In the example below, the index sequence is selected and host species distribution is shown in the plot.

![section4](images/section4.png)

- **Download**

Download the result file in JSON format from the most right bottom icon. 

(section-six)=
# FAQs

(section-seven)=
# Support
Please don’t hesitate to reach out to the developers for your questions, comments, or other feedback through mailing *bioinfo@perdanauniversity.edu.my*

## Contributions

- 
- 
