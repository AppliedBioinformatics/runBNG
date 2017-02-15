# runBNG
Bash wrapper to run common BioNano tasks on clusters.

Before using runBNG, 
* please ensure your system has installed python v2.7.x and Perl v5.10.x, v5.14.x or v5.16.x
* Please download the latest BioNano IrysSolve from http://www.bnxinstall.com/RefAlignerAssembler and the latest BioNano scripts from http://www.bnxinstall.com/Scripts. To determine which accelerator type you should use, please use the command "grep avx /proc/cpuinfo" or "grep sse2 /proc/cpuinfo" and search for the word ‘avx’ or ‘sse2’. If both types exist, use AVX as it is faster than SSE2.
* Please enusre BioNano RefAligner, BioNano Assembler and BioNano scripts are executable.

For detailed usage please refer to the wiki.

Thanks for using runBNG!

