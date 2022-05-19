(Figure-4)=
```{image} images/result_example-1.jpg
:alt: result
:class: bg-primary
:align: center
:width: 800
```
<a></a> 
: **Figure 4. Sample output from DiMA analysis.**
```{note}
Sample results are accesible for a self-exploration: 
- [MERS virus Spike protein nucleic acid sequences](https://dima.bezmialem.edu.tr/results/97a93eb4-6add-4824-b88d-02ff79af6acf), [MERS virus Spike protein amino acid sequences](https://dima.bezmialem.edu.tr/results/387bc2ce-f9ae-4a99-a50e-fad3355fcf72) 
- [Lassa virus Nucleoprotein nucleic acid sequences](https://dima.bezmialem.edu.tr/results/1419764f-ea40-4a68-890c-696e73013f0a), [Lassa virus amino acid sequences](https://dima.bezmialem.edu.tr/results/7d4e04b3-21f5-440e-a0b9-a46bf927a35b)

```

# 4.1. Summary 

Summary information ([Figure 4.1](Figure-4)) that is general to the input alignment and specific to a given *k-mer* position.
- alignment length
- download results
- query name
- support threshold
- position support
- distinct variants
- position entropy
- selected position

# 4.2. Sequence diversity

Entropy values indicate the level of variability at the corresponding *k-mer* positions, with zero representing completely conserved positions. Plot [(Figure 4.2)](Figure-4) provide a holistic view of the diversity and are responsive and interactive (one can easily hover and see the approximate entropy value of the hovered position). 

```{note}
For a benchmark, the peak absolute entropy of 9.2 and total variants of 98% were observed for HIV-1 clade B [(Hu et al., 2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0059994). 
```

The methodology for calculation of Shannon’s entropy at each *k-mer* position is as per [Khan et al., (2008)](https://journals.plos.org/plosntds/article?id=10.1371/journal.pntd.0000272).

# 4.3. Diversity motifs

All sequences at each of the *k-mer* positions in the protein alignments were quantified for distinct sequences and ranked-classified into diversity motifs [(Figure 4.3-4)](Figure-4) based on their incidences, as explained above under the [About](about.md) section.

Users can select a position from the “SELECTED POSITION” box [(Figure 4.1)](Figure-4), in the upper right corner to browse the motif distribution of the position.

# 4.4. Sequence Metadata

If the header format is provided in the analysis parameters (as described in the above [Parameters](parameters.md), DiMA will make a pie chart [(Figure 4.5)](Figure-4) for each type of the metadata.  

The user should select a specific *k-mer* from the selected position for the metadata to appear. By default, the first peptide will be selected. In the example below, the index sequence is selected and host species distribution is shown in the plot.

# 4.5. Data Synthesis and Further Analysis

Data from DiMA can be synthesised and analysed further in various ways, such as:

1. scatter plot of the relationship between entropy and incidence (frequency) of total variants; 
2. scatter plot of motif incidence (for each diversity motif) against total variants; 
3. frequency distribution violin plots of the diversity motifs; and 
4. distribution of conservation level for k-mer positions in the protein, and 
5. a table indicating  the minimum and maximum total variants at each entropy boundary values.

Examples of such synthesis and analyses are demonstrated in [Hu et al. (2013)](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0059994) and [Abd Raman et al. (2020)](https://pubmed.ncbi.nlm.nih.gov/32518710/).


# 4.6. Download

The DiMA output, top panel [(Figure 4.1)](Figure-4) allows for downloading of the analysis results in JSON and XLSX formats. The JSON file contains the complete analysis results as key-value pairs, which can be viewed using a public JSON viewer tool (such as [https://jsonformatter.org/json-viewer](https://jsonformatter.org/json-viewer)). Additionally, the XLSX file provides for easier viewing through an MS Excel application or equivalent that supports the format. The concatenated list of HCS based on a user-defined index incidence threshold can also be downloaded (JSON format) and viewed in a text editor or JSON viewer.