# DetectionGeneInterruption


Analysis of gene interruptions. Example in Acinetobacter baumannii.

Analysis consist on identify if a gene have a similar homolog, complete, incomplete, frameshifted or interrupted. The best way to detect this, is to blast the gene to the genome. 

# The number of blast hits per genome will tell if: 

      1 Blast hit: 
            - Gene is complete or incomplete.
            - if query size sequence is equal to reference size: gene is complete.
            - if query size sequence is longer than reference size: gene is incomplete.
      2 or more Blast hits:
            - Gene either have a similar homolog, or is frameshifted or interrupted.
            - if more than one blast hit with same size between query and reference: gene has hmologs within the genome.
            - if more than one blast hit with a difference smaller than 10 nucleotides: gene is frameshifted.
            - if more than one blast hit with a difference larger than 100 nucleotides: gene is interrupted.



Use genome assemblies that are complete, assembled in a single contig. To avoid the confunding effect of the miss assemblies and gene interruptions. (ex. If the assembly contain 300 contigs, and gene has two blast hit in different contigs, it could be that the contig is duplicated in the assembly, and the 2 hits are the result of the missassembly and not that the gene is duplicated or interrupted )

# 1. Selection of query. 
Identification of genes to detect in different genomes assemblies.
ex. comA gene in acinetobacter baumannii.  

# 2. Blasting the gene on the genome assemblies. by using tblastn. 


# 3. Extract sequence interrupting the gene

- Extract sequence

- Identify genes inside sequence.

- Identify IS elements inside sequence.



2. Curate Manuallymiss
