[![install with bioconda](https://img.shields.io/badge/install%20with-bioconda-brightgreen.svg?style=flat)](http://bioconda.github.io/recipes/strucvis/README.html) ![Conda](https://img.shields.io/conda/dn/bioconda/strucvis)

# LICENSE
strucVis : Display small RNA depth of coverage on a predicted RNA
    secondary structure

Copyright (C) 2016-2024 Michael J. Axtell

This program is free software: you can redistribute it and/or modify it
    under the terms of the GNU General Public License as published by the
    Free Software Foundation, either version 3 of the License, or (at your
    option) any later version.

This program is distributed in the hope that it will be useful,
        but WITHOUT ANY WARRANTY; without even the implied warranty of
        MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
        GNU General Public License for more details.

You should have received a copy of the GNU General Public License
        along with this program.  If not, see <http://www.gnu.org/licenses/>.

AUTHOR
    Michael J. Axtell, Penn State University mja18@psu.edu

REQUIREMENTS
- perl5 (available at /usr/bin/env perl)
- samtools (installed in your PATH)
- RNAfold (installed in your PATH)
- ps2pdf (installed in your PATH .. this is part of the ghostscript package)

# Install using conda

## Linux, Intel-based Mac OSX
1. Ensure conda is installed on your device.
2. Set up channels to include bioconda, following instructions at <https://bioconda.github.io>
3. `conda create --name strucvis strucvis`

## Silicon-based Max OSX
Do steps 1 and 2 as above. Then:
```
conda create --name strucvis
conda activate strucvis
conda config --env --set subdir osx-64
conda install strucvis
```

USAGE

`strucVis -b [bam] -g [genome] -c [Chr:start-stop] -s [strand 'plus' or 'minus'] -p [image_output] -n [Locus name]`

INPUTS
```
    -b : path to sorted and indexed BAM alignment file of small RNAs

    -g : path to FASTA formatted reference genome. Must be indexed using
    samtools faidx.

    -c : Coordinates of interest in format Chr:start-stop.

    -s : Strand of interest. Either 'plus' or 'minus'.

    -p : Output pdf file name. Omit the .pdf suffix, it will be added for you.

    -n : Name of locus. Prints name in the pdf file and on the plain text
    alignments. If not provided, defaults to 'Unnamed Locus'

SWITCHES
    -x : Suppress the printing of detailed file information on the
    post-script file

    -v : Print the version and quit

    -h : Print help message and quit
```

OUTPUT

- A pdf image showing the predicted RNA secondary structure with each nucleotide color-coded to represent the depth of sRNA alignments. ![strucVis_image](./Cluster_1885.ps.pdf)
- A plain-text file showing the predicted RNA secondary structure using dot-bracket notation, with sRNA alignments shown underneath.

```
Genome: ../EXP-2024-6/Arabidopsis_thalianaTAIR10.fa
Alignments: ../EXP-2024-6/SS/run1/merged_alignments.bam
Location: 4:11962937-11963045 minus
PDF file name: ShortStack_1716486683/strucVis/Cluster_1885.ps.pdf
Locus Name: Cluster_1885
UACUUUUUAUCUUCUUGAAAAUUUGUUACUAAUUUGGAAUGAAUUAGCUAAAUGGCUAAGCUAAUUUAUACCAAAUUAAUAGCAAAGUUUGAAGAACAUGAACAAUGUA
.....(((((.(((((.(((.(((((((.((((((((.(((((((((((.........))))))))))).)))))))).))))))).))).))))).)))))....... (-34.50)
....................AUUUGUUACUAAUUUGGAAUG.................................................................... len:21 al:47
....................AUUUGUUACUAAUUUGGAAUGAA.................................................................. len:23 al:1
....................AUUUGUUACUAAUUUGGAAUGAAU................................................................. len:24 al:2
....................AUUUGUUACUAAUUUGGAA...................................................................... len:19 al:1
....................AUUUGUUACUAAUUUGGAAUa.................................................................... len:21 al:1
....................AUUUGUUACUAAUU........................................................................... len:14 al:3
....................AUUUGUUACUAAUUUGGAAUu.................................................................... len:21 al:2
....................AUUUGUUACUAAUUUGuAAUG.................................................................... len:21 al:1
....................AUUUGUUACUAAUUUGGAAUGAu.................................................................. len:23 al:1
......................UUGUUACUAAUUUGGAAUG.................................................................... len:19 al:1
.......................................UGAAUUAGCUAA.......................................................... len:12 al:1
.................................................................UUAUACCAAAUUAAUAGC.......................... len:18 al:1
.................................................................UUAUACCAAAUUAAUAGCu......................... len:19 al:2
.................................................................UUAUACCAAAUUAAUAGCAu........................ len:20 al:1
.................................................................UUAUACCAAAUUAAUAGCAAAaUUU................... len:25 al:1
.................................................................UUAUACCAAAUUAAUAGCAAu....................... len:21 al:1
.................................................................UUAUACCAAAUUAAUAGCAAA....................... len:21 al:3
..................................................................UAUACCAAAUUAAUAGCAAAG...................... len:21 al:1
....................................................................UACCAAAUUAAUAGCAAAGUU.................... len:21 al:6
....................................................................UACCAAAUUAAUAGCAAAGU..................... len:20 al:1
......................................................................CCAAAUUAAUAGCAAAGUUUG.................. len:21 al:1
```



