---
layout: post
title: Capture The ADAPTER From Raw Human FASTQ Sequencing Data
subtitle: Capture the Adapter
categories: [BIOINFORMATICS]
tags: [NOTES, BIOINFORMATICS]
---


# Capture The ADAPTER From Raw Human FASTQ Sequencing Data

### Setep1.Using grep to capture let-7 conserved sequences
```bash
[test@test SRR493961]$<font face="Hack" color=blue >grep</font> 'TGAGGTAGTAGGTTGTATAGTT'  *.fastq | <font face="Hack" color=blue >head</font>
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATTCGTATGCCGTC
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>GTATCTCGTATGCC
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>AAATCTCGTATGCC
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ACTCGTATGCCGTC
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>TATCTCGTATGCCG
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
<font face="Hack" color=blue >TGAGGTAGTAGGTTGTATAGTT</font>ATCTCGTATGCCGT
```
###Step2.Count the number of reads containing let-7 conservative sequences
```bash
[test@test SRR493961]$ <font face="Hack" color=blue >grep</font> 'TGAGGTAGTAGGTTGTATAGTT' *.fastq | <font face="Hack" color=blue >wc -l</font>
<font face="Hack" color=blue >582294</font>
```
###Step3.Count the number of total reads in *.fastq file

```bash
[test@test SRR493961]$<font face="Hack" color=blue >wc -l</font> *.fastq
<font face="Hack" color=blue >114581392</font> SRR493961.fastq   <font face="Hack" color=darkblue># The total number of rows divided by 4 equals the number of reads</font>
```
###Step4.Extract the adapter sequence from *.fastq file
```bash
[test@test SRR493961]$  <font face="Hack" color=blue >grep</font> 'TGAGGTAGTAGGTTGTATAGTT' *.fastq | <font face="Hack" color=blue >head</font>  -n <font face="Hack" color=red >1000000 </font> | <font face="Hack" color=blue >sed</font> 's/TGAGGTAGTAGGTTGTATAGTT//g' | <font face="Hack" color=blue>sort</font> | <font face="Hack" color=blue>uniq</font> <font color=red>-cd</font> |  <font face="Hack" color=blue>sort</font> <font color=red>-nr</font> |  <font face="Hack" color=blue >head</font>
 <font color=red>486541</font> <font color=blue>ATCTCGTATGCCGT</font>    <font face="Hack" color=darkblue>#ADAPTER</font>
  36264 AATCTCGTATGCCG
  18340 TATCTCGTATGCCG
   5491 ACTCGTATGCCGTC
   4861 TCTCGTATGCCGTC
   3347 ATCGTATGCCGTCT
   2886 CTCGTATGCCGTCT
   2433 ATTCGTATGCCGTC
   1853 AAATCTCGTATGCC
   1774 GATCTCGTATGCCG
```
###Step5.Verify the accuracy of the adapter sequence
```bash
[test@test SRR493961]$  <font face="Hack" color=blue >grep</font> 'ATCTCGTATGCCGT' *.fastq |  <font face="Hack" color=blue >wc -l</font>   <font face="Hack" color=darkblue>##More than 15 lengths can basically meet the requirements, about 20 is normal</font>
<font face="Hack" color=blue >13897349</font>
```
