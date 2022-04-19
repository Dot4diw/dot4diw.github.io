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
[test@test SRR493961]$ grep 'TGAGGTAGTAGGTTGTATAGTT'  *.fastq | head
TGAGGTAGTAGGTTGTATAGTTATTCGTATGCCGTC
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTGTATCTCGTATGCC
TGAGGTAGTAGGTTGTATAGTTAAATCTCGTATGCC
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTACTCGTATGCCGTC
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTTATCTCGTATGCCG
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
TGAGGTAGTAGGTTGTATAGTTATCTCGTATGCCGT
```
###Step2.Count the number of reads containing let-7 conservative sequences
```bash
[test@test SRR493961]$ grep 'TGAGGTAGTAGGTTGTATAGTT' *.fastq | wc -l
582294
```
###Step3.Count the number of total reads in *.fastq file

```bash
[test@test SRR493961]$ wc -l  *.fastq
114581392 SRR493961.fastq # The total number of rows divided by 4 equals the number of reads</font>
```
###Step4.Extract the adapter sequence from *.fastq file
```bash
[test@test SRR493961]$ grep 'TGAGGTAGTAGGTTGTATAGTT' *.fastq | head -n 1000000 | sed 's/TGAGGTAGTAGGTTGTATAGTT//g' | sort |uniq -cd | sort -nr | head
 486541 ATCTCGTATGCCG #ADAPTER
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
[test@test SRR493961]$ grep 'ATCTCGTATGCCGT' *.fastq | wc -l ##More than 15 lengths can basically meet the requirements, about 20 is normal
13897349
```
