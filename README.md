# DetectionGeneInterruption


Analysis of gene interruptions. Example in Acinetobacter baumannii.

Analysis consist on identify if a gene have a similar homolog, complete, incomplete, frameshifted or interrupted. The best way to detect this, is to blast the gene to the genome. 

The number of blast hits per genome will tell if: 

      1- Gene is complete or incomplete.
            - if query size sequence is equal to reference size: gene is complete.
            - if query size sequence is longer than reference size: gene is incomplete.
      2- Gene either have a similar homolog, or is frameshifted or interrupted.
            - if more than one blast hit with same size between query and reference: gene has hmologs within the genome.
            - if more than one blast hit with a difference smaller than 10 nucleotides: gene is frameshifted.
            - if more than one blast hit with a difference larger than 100 nucleotides: gene is interrupted.


0. Use genome assemblies that are complete, assembled in a single contig. To avoid the confunding effect of the miss assemblies and gene interruptions.

1. Blasting the gene on the genome assemblies. by using tblastn. 

2. Curate Manuallymiss
