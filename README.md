# runBNG
Bash wrapper to run common BioNano tasks on clusters.

Before using runBNG, 
* please ensure your system has installed python v2.7.x and Perl v5.10.x, v5.14.x or v5.16.x
* Please download the latest BioNano IrysSolve from http://www.bnxinstall.com/RefAlignerAssembler and the latest BioNano scripts from http://www.bnxinstall.com/Scripts. To determine which accelerator type you should use, please use the command "grep avx /proc/cpuinfo" or "grep sse2 /proc/cpuinfo" and search for the word ‘avx’ or ‘sse2’. If both types exist, use AVX as it is faster than SSE2.
* Please enusre BioNano RefAligner, BioNano Assembler and BioNano scripts are executable.

After all required dependencies are been set, you can use runBNG to start your analysis. 

At present, runBNG offers 7 mainly used functions in BioNano analysis, which are 
* converting a fasta file into a cmap file, 
* reporting the quality of the raw molecules, 
* checking repeats in the raw molecules, 
* denovo assembly, 
* hybrid scaffolding, 
* structural variation detection and 
* alignment between different cmap files.

Detailed usages are listed as below: 
<pre>
Description: This pipeline aims to complete all BioNano IrysView key functions using command line.

Version: 1.0

Usage: runBNG [fa2cmap] [mol_qty] [repeatCheck] [denovo] [compare] [hybrid] [SV]
        fa2cmap         convert a given fasta format file into a cmap file.
        mol_qty         get a molecule quality report for the BioNano data.
        repeatCheck     check repeats using BioNano raw data.
        denovo          de novo assemble BioNao single molecule.
        compare         compare two different cmap files.
        hybrid          perform BioNano hybrid scaffolding.
        SV              structural variation detection.

Please select one of the given options and continue
</pre>

We have also supplied a testing dataset (Examples). You may use this dataset to test this software.

Thanks for using runBNG!

