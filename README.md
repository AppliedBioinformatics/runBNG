# runBNG
* A bash wrapper to run BioNano tasks on Linux clusters. 
* Users of BioNano systems do not have to rely on Windows anymore

## Functions 
At present, runBNG offers 12 mainly used functions in Bionano analyses, which are 
* converting a fasta file into a cmap file, 
* checking the quality of the raw molecule maps,
* filtering out unqualified single molecule maps depending on the aims of research 
* merging multiple bnx files from the same sample with a same bnx version
* checking the quality of consensus maps, 
* checking repeats in the raw molecules, 
* checking the mapping quality when single molecule maps and reference are available 
* denovo assembly, 
* hybrid scaffolding, 
* dual-hybrid scaffolding,
* structural variation detection and 
* alignment between different cmap files.

## Detailed usages 
```
------------------------------------------------------------------------------------------------------
Program:  runBNG
Version:  2.0
Author:   Yuxuan Yuan (yuxuan.yuan@outlook.com) 
------------------------------------------------------------------------------------------------------
Synopsis: This pipeline aims to help complete key Bionano optical mapping analyses using command line

Usage:    runBNG <command> [options]

Command:  fa2cmap       convert a given fasta format file into a cmap file
          cmapstats     check stats of a cmap file
          bnxmerge      merge different bnx files into one
          bnxstats      check stats of a bnx file
          bnxfilter     filter a bnx file 
          MQR           get a molecule quality report for the BioNano data
          repeatCheck   check repeats using Bionano raw data
          denovo        de novo assemble Bionano single molecule maps
          compare       compare two different cmap files
          hybrid        perform Bionano hybrid scaffolding using one enzyme 
          dual          perform Bionano hybrid scaffolding using two enzymes 
          SV            structural variation detection

options:  -h/-help   show this message and exit
-----------------------------------------------------------------------------------------------------
```

##  Dependencies
* please ensure your system satisfies the configuration below: 
<pre>
  •Ubuntu LTS or CentOS 6.4 or above or other equivalent Linux system
  •python v2.7.5 or greater 
  •perl v5.10.x, v5.14.x or v5.16.x
  •gcc 4.4.7 or greater 
  •glibc 2.15 or greater </pre>
* Please download the latest Bionano Solve (Linux version). To determine which accelerator type should be used when selecting BioNano tools, please use the command "grep avx /proc/cpuinfo" or "grep sse2 /proc/cpuinfo" and search for the word ‘avx’ or ‘sse2’. If both types exist, use AVX as it is faster than SSE2.
 <pre>
   BioNano sovle can be downloaded at:
   
   http://www.bnxinstall.com/solve/BionanoSolveInstall.html</pre>
* Please ensure BioNano RefAligner and BioNano Assembler are executable. Please ensure BioNano scripts are readable.

After all required dependencies are set, you can use 'runBNG' to start your analyses.  

A manual detailing how to set and use 'runBNG' has been provided in the [Manual](https://github.com/AppliedBioinformatics/runBNG/blob/master/Manual.md).

We have also supplied a testing dataset ([Examples](https://github.com/AppliedBioinformatics/runBNG/tree/master/Examples)). You may use this dataset to test this software.

Any problem in using 'runBNG' can be raised in the [Issues](https://github.com/AppliedBioinformatics/runBNG/issues).

## Citation
Yuxuan Yuan, Philipp E. Bayer, HueyTyng Lee, David Edwards; runBNG: A software package for BioNano genomic analysis on the command line. Bioinformatics 2017 btx366. doi: 10.1093/bioinformatics/btx366

Thanks for using 'runBNG'! 
