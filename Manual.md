# Manual                                                
* Thanks for using'runBNG'
* This manual helps to set and run 'runBNG'.
* Users may read this manual carefully before using 'runBNG', which could bring a better experience in using 'runBNG'.

## Download 'runBNG'
Users may use 'git clone https://github.com/AppliedBioinformatics/runBNG.git' in their 'Terminal' to download 'runBNG' package.

## Dependencies installation 

* The requried dependencies are:
 <pre>
  •Ubuntu LTS or CentOS 6.4 or newer or other equivalent Linux system
  •python v2.7.5 or newer 
  •perl v5.10.x, v5.14.x or v5.16.x
  •gcc 4.4.7 or newer
  •glibc 2.15 or newer 
  •BioNano tools
  •BioNano scripts </pre>

1) Before installing all needed dependencise, users may check their system and see if it is satisfied to run 'runBNG'. 
   Open the 'Terminal' and type, for example 'lsb_release -a' to check. If users use Ubuntu, please use LTS version. If users use 
   CentOS, please use version 6.4 or greater. Other Linux sytem, such as Redhat, Fedora, SUSE, Arch Linux and Debian, they may use equivalent version.

   a) If the system is satisfied, users may 'cd' to 'runBNG directory' and type 'chmod +x runBNG'
    in the 'Terminal'. Once the executable permission is given to 'runBNG', users may type './runBNG', and then
    'runBNG' will check the system and tell which dependency needs to be set or installed. 
    If there is no error raise, it means all dependencies are installed and set properly to 
    run 'runBNG'.

   b) If the system is not sastified, we are afraid users cannot use this software in their system. 

2) How to install needed dependencies.
  <pre>
   1) Using 'linuxbrew'
   
    Users may follow the introduction from http://linuxbrew.sh to install 'linuxbrew' in their system.
    After setting 'linuxbrew' to $PATH, users are able to use 'brew' to install all needed dependencies. 
    For example: brew install bash; brew install python; brew install perl@5.14; brew install gcc; and
    brew install glibc. 

   2) Using source code
   
      python: https://www.python.org/downloads/release
      perl: http://www.cpan.org/src/README.html
      gcc: https://gcc.gnu.org/releases.html
      glibc: https://www.gnu.org/software/libc
      
    Each provided website has a detailded instruction showing how to install corresponding software. 
    Users may follow those instructions and install needed dependencies.

    BioNano scripts can be downloaded at: http://www.bnxinstall.com/Scripts
    Linux version BioNano tools can be downloaded at: http://www.bnxinstall.com/RefAlignerAssembler
    To determine which accelerator type should be used, please use the command "grep avx /proc/cpuinfo" 
    or "grep sse2 /proc/cpuinfo" and search for the word ‘avx’ or ‘sse2’. If both types exist, use AVX 
    as it is faster than SSE2.</pre>
    
3) Once all needed dependencies installed, users may go to the runBNG directory again and type '/runBNG' 
    to check wheter the dependencies are set properly. If there are still errors, users may use:
    "export PATH=/path/to/installed/needed_dependency:$PATH" to set each dependencies. 
    For instance: 
    <pre>
      export PATH=$HOME/.linuxbrew/Cellar/gcc/5.3.0/bin:$PATH
      export PATH=$HOME/.linuxbrew/Cellar/glibc/2.19/bin:$PATH
      export PATH=$HOME/.linuxbrew/Cellar/perl514/5.14.4/bin:$PATH
      export PATH=$HOME/.linuxbrew/Cellar/python/2.7.11/bin:$PATH </pre>

4) After all settings being done, 'runBNG' should work in the satisfied linux system.

## Run 'runBNG'

1) Functions provided by 'runBNG' are: 
    <pre>
    •converting a fasta file into a cmap file,
    •checking the quality of the raw molecule maps,
    •filtering out unqualified single molecule maps depending on the aims of research
    •merging multiple bnx files from the same sample with a same bnx version
    •checking the quality of consensus maps,
    •checking repeats in the raw molecules,
    •checking the mapping quality when single molecule maps and reference are available
    •denovo assembly,
    •hybrid scaffolding,
    •structural variation detection and
    •alignment between different cmap files.</pre>

2) Detailed usages:
    
    $runBNG -h
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
    Please select one of the given options and continue</pre>

    $runBNG fa2cmap -h
    ```
    Description: Digest a given fasta format file into a cmap file using particular enzyme.

    Usage: runBNG fa2cmap [-h] [-f <fasta_file>] [-o <outDir>] [-e <enzyme_name>] [-q <enzyme_sequence>]
            [-z <minSeqLen>] [-l <minEnzy>] [-s <scriptsDir>]
            -h      display this help and exit.
            -f      a fasta format file to be digested.
            -o      output directory.
            -e      name of selected enzyme. Currently available enzymes are: BspQI, BbvCI, BsmI, BsrDI and BseCI.
            -q      sequence of the enzyme when -e is not given (optional).
            -z      filter criteria: min molecule length. Default 20 (Kb) (optional).
            -l      filter criteria: min number of selected enzymes in the molecule. Default is 5 (optional).
            -s      full path to BioNano scripts folder.
    ```
    $runBNG cmapstats -h 
    ```
    Description: Get stats of a cmap file.

    Usage: runBNG cmapstats [-h] [-c <cmap>] [-s <scripts>]
            -h  display this help and exit.
            -c  cmap file.
            -s  full path to BioNano scripts folder.
    ```
    $runBNG bnxmerge -h 
    ```
    Description: Merge different bnx files into one file. All bnx files should be generated from the same
                sample using a same enzyme. The version of those bnx files should be the same. For example: v1.2

    Usage: runBNG bnxmerge [-h] [-l <bnx_list>] [-t <maxthreads>] [-p <name>] [-r <RefAligner>] [-o <outDir>]
            -h      display this help and exit.
            -l      a file describing all bnx files to be merged. Each line lists the full path along with
                    a descriptive name for that file.
            -t      number of threads or CPUs.
            -m      memory (Gb).
            -p      a name for the merged file.
            -r      full path to BioNano RefAligner.
            -o      output directory.
    ```
    $runBNG bnxstats -h 
    ```
    Description: Check stats of a given bnx file (N_molecules, length, label density, SNR, intensity).

    Usage: runBNG bnxstats [-h] [-b <bnx>]
            -h      display this help and exit.
            -b      the bnx file.
            -p      a name for the table extracted from the bnx file.
            -o      output directory.
    ```
    $runBNG bnxfilter -h 
    ```
    Description: Molecule map quality control--filter unqualified molecule maps and get a new bnx file.

    Usage: runBNG bnxfilter [-h] [-b <bnx>] [-t <maxthreads>] [-p <name>] [-r <RefAligner>] [-l <minlen>]
            [-s <minsite>] [-m <maxsite>] [-i <maxintensity>] [-x <mres>] [-o <outDir>]
            -h      display this help and exit.
            -b      the bnx file to be filtered .
            -t      number of threads or CPUs.
            -m      memory (Gb).
            -p      a name for the output files .
            -r      full path to BioNano RefAligner.
            -l      min molecule length to be filtered (Kb). Default is 100 (optional).
            -s      min number of selected enzymes in the molecule. Default is 6 (optional).
            -M      max number of selected enzymes in the molecule. Default is 200 (optional).
            -i      maxIntensity to be filtered. Default is 0.6 (optional).
            -x      reduce resolution of input molecule maps by xxx*500bp. Default is 0.001 (optional).
            -o      output directory.
    ```
    $runBNG MQR -h
    ```
    Description: Report the quality of given BioNano single molecules.

    Usage: runBNG MQR [-h] [-b <bnx>] [-r <ref_cmap>] [-R <RefAligner>] [-t <maxthreads>] [-m <maxRAM>] [-s<minLen>]
            [-n <times>] [-i <iter>] [ -l <maxoutlier>] [-d <density>] [-z <genome_size>] [-o <outDir>] [-p <name>]
            -h      display this help and exit.
            -b      the raw molecule map file (Molecules.bnx).
            -r      reference maps (.cmap). You may use 'runBNG' to get one, if you only have a fasta formate reference.
            -z      the genome size of input species (Mb). Using this option can help estimate a suitable pvalue (optional).
            -R      full path to BioNano RefAligner.
            -t      maximum threads or CPUs.
            -m      maximum memory (Gb).
            -s      minimum length of single molecules to be filtered. Default is 150 (Kb) (optional).
            -n      times to regenerate the hashtable. Default is 3 (optional).
            -i      iterations for each hashtable. Default is 3 (optional).
            -l      cutoff of the label interval differences between matched ref and qry maps (Kb). Default is 40. Disable this option when
                    an input value >1000 (optional).
            -d      label density of the reference genome if -r is given (xxx/100Kb). For example: 10 (optional).
            -o      output directory.
            -p      a name for the output files.
     ```
     $runBNG denovo -h 
     ```
     Description: De novo assembly for BioNano single molecules.

     Usage: runBNG denovo [-h] [-t <toolsDir>] [-s <scriptsDir>] [-b <bnx>] [-l <len>] [-m <site>] [-T <nthreads>] [-j <njobs>]
             [-i <iter>] [-z <genome_size>] [-r <ref_cmap>] [-p <FP>] [-n <FN>] [-d <sd>] [-f <sf>] [-R <sr>] [ -L<lm>] [ -S <sm>] [-o <outDir>]
             -h      display this help and exit
             -t      full path to BiNano tools folder.
             -s      full path to BioNano scripts folder.
             -b      the raw molecule map file (Molecules.bnx).
             -T      number of threads or CPUs.
             -l      minimum length to filter out (Kb). Default is 150 (optional).
             -m      minimum labels on the molecule. Default is 8 (optional).
             -j      number of jobs to run.
             -i      times of iteration. Default is 5 (optional).
             -z      the genome size of input species (Mb).
             -r      the digested reference (.cmap). Default is None (optional).
             -p      flase positive density (/100Kb). Default is 1.5 (optional).
             -n      false negative rate (%/100). Default is 0.15 (optional).
             -d      scalingSD (Kb^1/2). Default is 0.0 (optional).
             -f      siteSD (Kb). Default is 0.2 (optional).
             -R      relativeSD. Default is 0.03 (optional).
             -L      large jobs maximum memory (GB). Default is 128 (optional).
             -S      small jobs maximum memory (GB). Default is 7.5 (optional).
             -o      output directory.
     ```
     $runBNG compare -h 
     ```
     Description: Compare a query BioNano cmap file to a ref cmap file

     Usage: runBNG compare [-h] [-R <RefAligner>] [-r <ref_cmap>] [-q <qry_cmap>] [-z <genome_size>]
             [ -o <outDir>] [-p <output_name>] [-t <maxthreads>] [-m <maxmemory>]
             -h      display this help and exit.
             -R      path to BioNano RefAligner.
             -r      the reference cmap file.
             -q      the query cmap file.
             -z      the genome size of input species (Mb).
             -o      output directory.
             -p      A name for the output files.
             -t      maximum threads or CPUs.
             -m      Memory (Gb).
     ```
     $runBNG SV -h 
     ```
     Description: Compare cmaps from different individuals to detect structural variation. If you want to use
             this function please perform BioNano denovo assembly first. You may use 'runBNG denovo'.

     Usage: runBNG SV [-h] [-r <ref_cmap>] [-b <bed> ] [-f <final_assembledDir>] [-s <scriptsDir>]
             [-t <toolsDir>] [-z <genome_size>] [-o <outDir>]
             -h      display this help and exit.
             -r      the reference cmap file.
             -b      a .bed file containing gap information to assist the further accuracy of SV calling. Default Null (optional).
             -f      full path to final assembled folder, such as *exp_refineFinal1.
             -s      full path to BioNano scripts folder.
             -t      full path to BioNano tools folder.
             -z      the genome size of input species (Mb).
             -T      maximum threads or CPUs.
             -o      output directory.
     ```
     $runBNG hybrid -h 
     ```
     Description: Run the BNG hybrid assembly pipeline.

     Usage: runBNG hybrid [-h] [-s <scriptsDir>] [-t <toolsDir>] [-r <reference>] [-b <bnx>] [-m <minLen>] [-l <minEnzy>]
             [-e <enzyme> ] [-B <conflict_filter_level>] [-N <conflict_filter_level>] [-z <genome_size>] [-f <final_assembled_cmap>]
             [-c <intial_p>] [-u <chimeric_p>] [-g <merge_p>] [-d <distance>] [-p <percentage>] [-o <outDir>] [-T <maxthreads>] [-M <maxmemory>]
             -h      display this help and exit.
             -s      full path to BioNano scripts folder.
             -t      full path to BioNano tools folder.
             -r      NGS sequence file.
             -b      the raw molecule map file (Molecules.bnx).
             -m      filter: min molecule length (Kb). Default is 20 (optional).
             -l      filter: min number of selected enzyme in molecule. Default is 5 (optional).
             -e      name of selected enzyme. Currently available enzymes are: BspQI, BbvCI, BsmI, BsrDI and BseCI. Default is BspQI (optional).
             -B      BioNano conflict filter level: 1 no filter, 2 cut contig at conflict, 3 exclude conflicting contig.
             -N      NGS conflict filter level: 1 no filter, 2 cut contig at conflict, 3 exclude conflicting contig.
             -z      the genome size of input species (Mb).
             -f      final assembled cmap file. For instance exp_refineFinal1_contigs.cmap.
             -c      Minimum confidence value to output intial alignments. Recommended starting value of 1e-5/genome size in Mb. Default is 1e-10 (optional).
             -u      Minimum confidence value used to flag chimeric/conflicting alignments. Default is 1e-13 (optional).
             -g      Minimum confidence value used to merge alignments. Recommand to set it to be the same as the -u. Default is 1e-13 (optional).
             -d      The distance (kb) from a conflicting site within which the chimeric quality score of BioNano genome map labels will be examined.
                    Default is 10 (optional).
             -p      The minimal percentage (%) of molecules spanning to the left and right of a label of interest, thus supporting the BioNano assembly
                    at that region. default is 35 (optional).
             -o      output directory.
             -T      maximum threads or CPUs.
             -M      maximum RAMs (Gb).
      ```
Note:
    <pre>
    a) Users can select any of the given options to start their analyses. 
    b) Flags without 'optional' indicated are all mandatory. Errors will be raised when they are not specified.
    c) It is suggested to run 'MQR' first before running 'denovo', because the result from 'MQR' can be used to adjust the parameters in 'denovo', such as 'flase positive density', 'false negative rate' and 'siteSD'.
    d) Users may use 'bnxstats' and 'bnxfilter' together to perform quality control of their single molecule maps.
    e) 'SV' requires the result from denovo assembly. It is recommended to run 'denovo' first before running 'SV'.</pre>
    
