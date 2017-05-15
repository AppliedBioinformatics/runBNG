# runBNG
A bash wrapper helps to run BioNano tasks on clusters.

## Functions 
At present, runBNG offers 11 mainly used functions in BioNano analyses, which are 
* converting a fasta file into a cmap file, 
* checking the quality of the raw molecule maps,
* filtering out unqualified single molecule maps depending on the aims of research 
* merging multiple bnx files from the same sample with a same bnx version
* checking the quality of consensus maps, 
* checking repeats in the raw molecules, 
* checking the mapping quality when single molecule maps and reference are available 
* denovo assembly, 
* hybrid scaffolding, 
* structural variation detection and 
* alignment between different cmap files.

## Detailed usages 
<pre>
Description: This pipeline aims to complete key BioNano optical mapping analyses using command line.

Version: 1.02

Usage: runBNG [fa2cmap] [cmapstats] [bnxmerge] [bnxstats] [bnxfilter] [MQR] [repeatCheck] [denovo] [compare] [hybrid] [SV]
        fa2cmap         convert a given fasta format file into a cmap file.
        cmapstats       check stats of a cmap file.
        bnxmerge        merge different bnx files into one.
        bnxstats        check stats of a bnx file.
        bnxfilter       filter unqualified molecule maps.
        MQR             get a molecule quality report for the BioNano data.
        repeatCheck     check repeats using BioNano raw data.
        denovo          de novo assemble BioNano single molecule.
        compare         compare two different cmap files.
        hybrid          perform BioNano hybrid scaffolding.
        SV              structural variation detection.

Please select one of the given options and continue </pre>

##  Dependencies
* please ensure your system satisfies the configuration below: 
<pre>
  •bash 4.0 or greater
  •python v2.7.5 or greater 
  •perl v5.10.x, v5.14.x or v5.16.x
  •gcc 4.4.7 or greater 
  •glibc 2.15 or greater 
  •Ubuntu LTS or CentOS 6.4 or above </pre>
* Please download the latest BioNano tools (Linux version) and the latest BioNano scripts. To determine which accelerator type should be used, please use the command "grep avx /proc/cpuinfo" or "grep sse2 /proc/cpuinfo" and search for the word ‘avx’ or ‘sse2’. If both types exist, use AVX as it is faster than SSE2.
 <pre>
   You may download BioNano scripts and tools from:
   
   BioNano tools: http://www.bnxinstall.com/RefAlignerAssembler
   
   BioNano scripts: http://www.bnxinstall.com/Scripts </pre>
* Please ensure BioNano RefAligner and BioNano Assembler are executable. Please ensure BioNano scripts are readable.

After all required dependencies are set, you can use 'runBNG' to start your analyses.  

A manual detailing how to set and use 'runBNG' has been provided in the [Manual](https://github.com/AppliedBioinformatics/runBNG/blob/master/Manual).

We have also supplied a testing dataset ([Examples](https://github.com/AppliedBioinformatics/runBNG/tree/master/Examples)). You may use this dataset to test this software.

Any problem in using 'runBNG' can be raised in the [Issuse](https://github.com/AppliedBioinformatics/runBNG/issues).

Thanks for using 'runBNG'! 
