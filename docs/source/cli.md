## 5.1. Considerations for CLI

Web service of DiMA is capable of handling files up to 100 MB. Analysis with bigger data is available by using [DiMA-CLI](https://github.com/PU-SDS/DiMA) locally. Here, we provide some instructions for such purposes. You can download the sample data, MERS-CoV Spike protein, [here](https://drive.google.com/file/d/1CeEyb4arWkKzDvQi2cqtDGfKApD0SrlW/view?usp=sharing). 

## 5.2. Installation

Installing the latest version is possible with `pip install dima-cli`. Python version >=3.7 <3.11 is required.  

## 5.3. Basic Usage

- The standard way to run the tool:

`dima-cli -i aligned_sequences.afa -o results.json`

- To print the full list of arguments with short explanations: 

`dima-cli --help`

- To recieve the results in tabular format:

`dima-cli -i aligned_sequences.afa -t xlsx -o results.xlsx`

- To run a DNA analysis:

`dima-cli -i aligned_sequences_nt.afa -a nucleotide -o results.json`

- To recieve the HCS along with the results:

`dima-cli -i aligned_sequences.afa -o results.json -c hcs.json`

## 5.4. Advanced Usage Examples

Customazing the parameters may be neccesary, especially for the big data analyses. Adjusting the [parameters](https://github.com/PU-SDS/DiMA#command-line-arguments) is primarily reasonable for: inclusion of metadata by parsing of the headers, setting a support threshold for positions, prefering different k-mer sizes. Example usage:

`dima-cli -i aligned_sequences_nt.afa -l 9 -f "accession|host|geography|year" -a protein -t json -c hcs.json -e 100 -o results.json`

