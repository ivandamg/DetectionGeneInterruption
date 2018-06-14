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

Create db of genome assembly and blast gene to genome assembly

      # create db 
      makeblastdb -dbtype nucl -in STRAIN_ASSEMBLY -parse_seqids -out STRAINdbFILE1_db 
      # tblastn
      tblastn -db STRAIN_db -outfmt 6 -evalue 1e-8 -show_gis -num_alignments 1 -max_hsps 20 -num_threads 30 -out blastProteinSeq_in_Strain.xml -query ProteinSeq.faa

# 3. Extract sequence interrupting the gene

- Extract sequence
      
      # extractregion with coordinates
      blastdbcmd -entry 'SCAFFOLD' -db STRAINdbFILE1_db -range minPosition-maxPosition > Destination/FileStrain1.fa

- Annotate sequence.
Use Prokka    
                        
        ~/software/prokka-1.12/prokka/bin/prokka --outdir Annotation_FOLDER --genus GENUS --species SPECIES --strain STRAIN --locustag GS_STRAIN --prefix FILEPREFIX_Prokka --rfam --usegenus Destination/File.fa

Or genemark to detect Open reading frame (ORF). http://opal.biology.gatech.edu/GeneMark/
           
                     
             
- Identify IS elements inside sequence.
Blast to IS element database https://isfinder.biotoul.fr/



# 4. Plot the gene interruptions. 

R markdown tutorial of plotting gene interruptions in several strains. 
