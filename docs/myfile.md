- {ref}`About<section-one>`
- {ref}`Browser compatibility<section-two>`
- {ref}`Workflow of DiMA<section-three>`
- {ref}`Input file and parameters<section-four>`
- {ref}`How to interpret the results<section-five>`
- {ref}`FAQs<section-six>`
- {ref}`Support<section-seven>`

# Protein Sequence Diversity Dynamics Analyser for Viruses (DiMA) 

(section-one)=
# About

Viral infectious diseases are a major public health threat. Protein sequence diversity is one of the major challenges in the design of diagnostic, prophylactic and therapeutic interventions against viruses. The diversity can be an outcome of a combination of underlying evolutionary processes (mutation, recombination, and assortment). A continuing goal is a greater understanding of viral proteome sequence diversity, the dynamics of substitutions, and effective strategies to overcome the diversity for drug or vaccine design.

Herein, we present Diversity Motif Analyser (DiMA), a tool designed to facilitate the quantification and dissection of viral protein sequence diversity dynamics. DiMA provides a quantitative measure of sequence diversity by use of Shannon’s entropy (PMID: [18698358](https://pubmed.ncbi.nlm.nih.gov/18698358/)), applied via a user-defined *k-mer* sliding window to a protein alignment. Additionally, DiMA further interrogates the diversity by dissecting the entropy at each aligned *k-mer* position to various diversity motifs (PMIDs: [32518710](https://pubmed.ncbi.nlm.nih.gov/32518710/), [23593157](https://pubmed.ncbi.nlm.nih.gov/23593157/)), based on the incidence of distinct *k-mer* sequences at the position. At a given position, index is the predominant sequence and all other distinct *k-mer*s are referred to as total variants to the index, sub-classified into major variant (the most common variant), minor variants (comprising of *k-mer*s with incidence lower than major and higher than unique), and unique variants (*k-mer*s seen only once in the alignment). Moreover, the description line of the sequences in the input alignment can be enriched for inclusion of meta-data as part of the analysis, such as spatio-temporal information, among others. DiMA outputs a JSON file that provides multiple facets of sequence diversity: sequence name, *k-mer* position, entropy, distinct *k-mer*s at the position, and their incidence, motif classification and metadata (if available). DiMA enables comparative sequence diversity dynamics analyses, within and between proteins of a virus species, and proteomes of different species.

DiMA is an outcome of many years of viral studies on several different species since 2007. These studies have been published in peer-reviewed journals (PMIDs: [17434154](https://pubmed.ncbi.nlm.nih.gov/17434154/), [18030326](https://pubmed.ncbi.nlm.nih.gov/18030326/), [18698358](https://pubmed.ncbi.nlm.nih.gov/18698358/), [19401763](https://pubmed.ncbi.nlm.nih.gov/19401763/), [21471731](https://pubmed.ncbi.nlm.nih.gov/21471731/), [22573867](https://pubmed.ncbi.nlm.nih.gov/22573867/), [23593157](https://pubmed.ncbi.nlm.nih.gov/23593157/), [26680743](https://pubmed.ncbi.nlm.nih.gov/26680743/), [29322922](https://pubmed.ncbi.nlm.nih.gov/29322922/), [29363421](https://pubmed.ncbi.nlm.nih.gov/29363421/), [31874646](https://pubmed.ncbi.nlm.nih.gov/31874646/), [34068495](https://pubmed.ncbi.nlm.nih.gov/34068495/) and [32518710](https://pubmed.ncbi.nlm.nih.gov/32518710/) and international conferences. Besides being available as a webserver, it can also be downloaded as a standalone client tool ([https://github.com/PU-SDS/DiMA](https://github.com/PU-SDS/DiMA)), particularly for big data analyses.

DiMA webserver has been under development since March 2020. It has been extensively tested with 18 protein datasets (9 structural and 9 non-structural) from six viral species. External validation of our tool has been performed by three individuals, with a total of 36 protein datasets (18 structural and 18 non-structural), originating from three viral species.

## Defining diversity motifs

For a given protein alignment, all sequences at each of the aligned *k-mer* positions are quantified for distinct sequences and ranked-classified into diversity motifs based on their incidences, as described in Hu et al. (2013) (Supplementary Figure 1, see extract below) (PMID: [23593157](https://pubmed.ncbi.nlm.nih.gov/23593157/)).  

```{image} images/motifs.jpg
:alt: diversitymotifs
:class: bg-primary
:width: 300px
:align: center
```
<br><br/>
**Figure 1: Definitions of diversity motifs.** The ‘‘Index’’ nonamer is the most prevalent sequence, present in 12 of the 20 isolates. The ‘‘Major’’ variant is the most common variant of the index (5/20). ‘‘Minor’’ variants are multiple different repeated sequences, each with incidences less than the major variant. ‘‘Unique’’ variants are those represented by a single aligned sequence. Distinct variant sequences at a given nonamer position are the different sequence at the position; in this example one of major, two of minor, and three of unique.

(section-two)=
# Browser compatibility

![browserc](images/browserc.png)

## Accesibility

The webserver is publicly available at:
[https://dima.bioinfo.perdanauniversity.edu.my](https://dima.bioinfo.perdanauniversity.edu.my)

(section-three)=
# Workflow 

![workflow](images/workfloww.jpg)
**Figure 1**\
**Input:** Viral protein sequences, typically obtained from publicly available databases (NCBI virus and GISAID, among others), aligned and submitted to DiMA in aligned FASTA (*.afa)* format.\
**Process:** DiMA provides a quantitative measure of sequence diversity by use of Shannon’s entropy, applied via a user-defined *k-mer* sliding window. Further, the entropy value is corrected for sample size bias by applying a statistical adjustment (Lipinski’s rule). Additionally, DiMA further interrogates the diversity by dissecting the entropy value at each *k-mer* position to various distinct *k-mer* sequences that are classified into diversity motifs (index, major, minor and unique; see Section 3 for the definition of the diversity motifs) based on their incidence.\
**Output:** The entropy values, diversity motifs, and each of the *k-mer* corresponding metadata is plotted to provide a panoramic overview of the protein sequence diversity. 

(section-four)=
# Input file and parameters

- **Input file**\
DiMA only uses multiple sequence alignment (protein sequences; DNA should also work) in (aligned) FASTA (*.afa* or *.fas*) format. Any existing, published alignment tool can be used to produce the MSA, such as MAFFT or MUSCLE, as long as the aligned sequences are provided to DiMA as input in (aligned) FASTA format.  
- **Parameters**
  - **Viral sequence name**\
  Name of protein to be analysed (such as Nucleoprotein, Matrix protein, or Polymerase protein). 
  - **Low support threshold**\
  The support is defined as the number of sequences at a given *k-mer* position that do not harbor gap and unknown and/or ambiguous residues. Positions below a statistical support of 30 sequences (default) are defined as of low support. The user has the flexibility to set the threshold for low support.
  - **Kmer length**\
  Select a *k-mer* window size that is appropriate for the analysis.\ 
While the minimum applicable size is 3, the maximum can equal to the alignment length of the uploaded input file. By default, DiMA uses a window size of nine (9; nonamer; 9-mer) to evaluate the viral diversity with respect to cellular immune response.
  - **Header format to include metadata**\
  This optional functionality allows annotation of the distinct sequences at each *k-mer* position  with respective cognate sequence metadata, such as collection date, country of isolation , isolation host. Simply, it parses the information on the sequence header (definition/description line). 


```{note}
Example of a definition line: >ATY74257.1 |2017-03-02|China: Kunming|Homo sapiens
```

Because the format of metadata varies between databases, DiMA has relied on the format of [NCBI Virus](https://www.ncbi.nlm.nih.gov/labs/virus/vssi/#/). 

(section-five)=
# How to interpret the results

- **DiMA Output**

![sections](images/sectionss.png)

- **Section 1 (Summary statistics)**

A summary of information about the query: request ID, submission parameters, the total number of sequences in the alignment, and the number of low support positions. 

![section1](images/section1.png)

- **Section 2 (Proteome diversity)**

Entropy values indicate the level of variability at the corresponding *k-mer* positions, with zero representing completely conserved positions. Plots provide a holistic view of the diversity and are responsive and interactive (one can easily hover and see the approximate entropy value of the hovered position). 

![section2](images/section2.png)
```{note}
For a benchmark, the peak absolute entropy of 9.2 and total variants of 98% were observed for HIV-1 clade B [(Hu et al., 2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0059994). 
```

The methodology for calculation of Shannon’s entropy at each *k-mer* position is as per [Khan et al., (2008)](https://journals.plos.org/plosntds/article?id=10.1371/journal.pntd.0000272).

- **Section 3 (Diversity motifs)**

All sequences at each of the *k-mer* positions in the protein alignments were quantified and quantified for distinct sequences and ranked-classified into diversity motifs based on their incidences, as explained above under the {ref}`About<section-one>` section.

Users can select a position from the “SELECTED POSITION” box, in the upper right corner to browse the motif distribution of the position.


```{image} images/section3.png
:alt: section3
:class: bg-primary
:width: 400px
:align: center
```
<br><br/>
- **Section 4 (Metadata)**

If the header format is provided in the analysis parameters (as described in the above {ref}`Parameters<section-four>`), DiMA will make a pie chart for each type of the metadata.  

The user should select a specific *k-mer* from the selected position for the metadata to appear. By default, the first peptide will be selected. In the example below, the index sequence is selected and host species distribution is shown in the plot.

![section4](images/section4.png)

- **Download**

Users can download the raw results file in JSON format from the most right bottom icon. 

(section-six)=
# FAQs

1. How to cite?

For now: **Shan et al., https://dima.bioinfo.perdanauniversity.edu.my/**

(section-seven)=
# Support
Please don’t hesitate to reach out to the developers for your questions, comments, or other feedback through mailing *bioinfo@perdanauniversity.edu.my*

## Team

- Shan Tharanga 
- Yongli Hu
- Olivo Miotto
- Eyyüb Selim Ünlü
- Muhammet A. Çelik
- Muhammed Miran Öncel
- Hilal Hekimoğlu
- Muhammad Farhan Sjaugi
- Mohammad Asif Khan
