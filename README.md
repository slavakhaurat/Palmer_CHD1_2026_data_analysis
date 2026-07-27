# Palmer_CHD1_2026_data_analysis

## Data and code availability
RNA-seq data generated in this study have been deposited in the Gene Expression Omnibus (GEO) under accession number GSE336993. ATAC-seq data generated in this study have been deposited in GEO under accession number GSE337107. Proteomics datasets generated in this study have been deposited to the ProteomeXchange Consortium via the PRIDE repository under accession numbers PXD080429 and PXD080595. Processed data underlying the figures and custom analysis scripts are available from the Lead Contact upon reasonable request.

## Mass spectrometry data analysis of histones
<details>
<summary>from Methods</summary>
For peptide identification from DDA data, the RAW-files were loaded into Proteome Discoverer (version 3.2.0.450, Thermo Scientific). All MS/MS spectra were searched using MSAmanda version 3.0 (Dorfer V. et al., J. Proteome Res. 2014 Aug 1;13(8):3679-84). The peptide and fragment mass tolerance was set to ±10 ppm, the maximum number of missed cleavages was set to 2, using tryptic enzymatic specificity without proline restriction. Peptide and protein identification was performed in two steps. For an initial search the RAW-files were searched against the Uniprot reference database for mouse (21,816 sequences; 11,706,438 residues), supplemented with common contaminants and sequences of tagged proteins of interest. The result was filtered to 1 % FDR on protein level using the Percolator algorithm (Käll L. et al., Nat. Methods. 2007 Nov; 4(11):923-5) integrated in Proteome Discoverer. A sub-database of proteins identified in this search was generated for further processing. For the second search, the RAW-files were searched against the created sub-database using the same settings as above and considering the following additional variable modifications: oxidation on methionine, phosphorylation on serine, threonine and tyrosine, acetylation on Lysine and protein N-terminus, methylation on Arginine, Lysine and protein N-terminus, di-methylation on Arginine and Lysine, tri-methylation on Lysine and glutamine to pyro-glutamate conversion at peptide N-terminal glutamine. The localization of the post-translational modification sites within the peptides was performed with the tool ptmRS, based on the tool phosphoRS (Taus T. et al., J. Proteome Res. 2011, 10, 5354-62). The result was filtered to 1 % FDR on PSM and protein level using the Percolator algorithm. Additionally, an Amanda score cut-off of at least 150 was applied. Proteins were filtered to be identified by a minimum of 2 PSMs in at least 1 sample. Protein areas have been computed in IMP-apQuant (Doblmann J. et. al, J Proteome Res 2019, 18(1):535-41) by summing up unique and razor peptides. Resulting protein areas were normalized using iBAQ (Schwanhäusser B. et al., Nature 2011, 473(7347):337−42) and sum normalization was applied for normalization between samples. Match-between-runs (MBR) was applied for peptides with high confident peak area that were identified by MS/MS spectra in at least one run. Proteins were filtered to be identified by a minimum of 3 quantified peptides. 
</details>

Mean abundance is calculated as an average of protein spectral areas among all samples. Spectral areas of proteins are comprised of spectral areas of detected peptides assigned to a protein and normalized for all proteins in a sample. Fold change is calculated as a ratio between the mean spectral areas of CHD1IMN samples and Control samples. Two samples per condition are analysed.

```
Mass spectrometry of extracted histones
        |
        V
Proteomics data processing 
        |
        V
Resulting abundance table
        |
        V
Visualisation with Python (Figure 2M)

```
[Resulting abundance table .xlsm](histones_mass_spec/Khauratovich_Goloborodko_IMBA_ID2045_20250423_E4_insol_Urea_ArgC_2x2runs_mouse_histones_Top100_quanOnAll_v2.xlsm)   
[Visualisation with Python .ipynb](histones_mass_spec/Mass_spec_Histones_main_3nd_cleaned.ipynb)      
__Figure 2M__ Mass spectrometry analysis of acid-enriched histone protein preparations    
- contains proteins (histones) abundance change CHD1iMN/Control
- change in detected histone modifications (PTMs) 

## RNA-seq data analysis
<details>
<summary>from Methods</summary>
Following STA-PUT isolation of enriched spermatocyte (F2) fractions as detailed above. Cell pellets of 1 million cells were resuspended in 1ml of PBS. 100µl was separated, pelleted (600RCF for 5 minutes) and the resultant cell pellet was snap-frozen for Western blot analysis of CHD1 protein levels. The remaining 800µl was washed in PBS and pelleted (600RCF for 5 minutes). 500µl of TRI-reagent (Sigma-Aldrich, CAT# T9424) was used to resuspend each pellet and this cell solution was immediately snap-frozen for later processing.  Nucleic acids were separated via addition of 200µl chloroform (Merck # 1024451000) and vortexing the mixture. After centrifugation (15 minutes, 21,000RCF at 4oC) the aqueous phase was transferred to a new tube and another 200µl of chloroform was added. The mixture was vortexed and spun again (15 minutes, 21,000RCF at 4oC). The aqueous phase was transferred to a new tube and 500 µl of isopropanol was added. This solution was vortexed and left for 10 minutes at room temperature for nucleic acids to precipitate. The precipitate was then pelleted via centrifugation (30 minutes, 21,000RCF at 4oC). The resultant pellet was washed with 75% Ethanol and left to air dry. When dry the pellet was resuspended in 43µl of RNase- and DNase-free DEPC-Treated Water (Thermofisher, # AM9906). Next, DNA was removed from the sample via the addition of DNase I buffer (ThermoScientific # B43) to a final concentration of 1X together with 1U DNase I (ThermoScientific # EN0525) and 40U RiboLock RNase inhibitor (ThermoScientific #EO0382). This was left to incubate for 20 minutes at 37oC. Next, the volume was topped up to 100µl and 200µl Phenol:Chloroform:Isoamyl alcohol 25:24:1 (Merck, CAT #P3803) was added. This solution was moved to a phase lock gel heavy tube (QuantaBio (# 2302830 – Now discontinued), this was then vortexed and spun down (30 minutes, 21,000RCF at 4oC). The aqueous phase was transferred to a new tube and 10 µl of 3M NaAc, 1 µL glycogen RNA-grade, 10mg/ml (ThermoScientific # R0551) and 300 µL ice-cold 100% EtOH was added. This solution was vortexed and RNA was left to precipitate at -80oC for 1 hour. The precipitated RNA was pelleted (45 minutes, 21,000RCF at 4oC). The resultant pellet was then washed 1X with 80% ethanol and 2X with 75% ethanol with associated centrifugation steps (15 minutes, 21,000RCF at 4oC). After the final wash the solution was sun down one final time (10 minutes, 21,000RCF at 4oC), the supernatant was discarded and the pellet was air-dried for 5 minutes. The pellet was then resuspended in 30µl of 1X TE buffer (Invitrogen #T11493). Libraries were prepared from total RNA using a stranded mRNA-seq library preparation protocol with poly(A) enrichment, fragmentation, cDNA synthesis, adapter ligation, indexing, and PCR amplification.
</details>
RNA-seq data were processed using the nf-core/rnaseq pipeline implemented in Nextflow 120. Adapter trimming was performed using Trim Galore! 121, reads mapping to abundant RNA species including rRNA were removed using Bowtie2 122, and filtered reads were aligned to the mouse reference genome (Ensembl GRCm38/mm10) using STAR 123. Gene-level read counts were generated using featureCounts 124, and differential gene expression analysis was performed using DESeq2 125 using at least three biological replicates per genotype. Genes with adjusted p-values (Benjamini-Hochberg corrected) of padj < 0.01 (FDR < 1%) were considered differentially expressed.

```
RNA-seq FASTQ
        │
        ▼
nf-core/rnaseq
        │
        ▼
Counts + DESeq2
        │
        ▼
Python notebooks
        ├── Differential expression
        ├── MA plot
        ├── Promoter expression
        └── Figure 2, Fig. S3

```


## ATAC-seq data analysis from spermatocytes and MEFs

<details>
<summary>from Methods</summary>   
For ATAC-seq experiments performed on STA-PUT-purified spermatocyte F2 fractions. Cell pellets were washed in PBS, and 40,000 cells per sample were processed using the Active Motif ATAC-Seq Kit according to the manufacturer’s instructions. For ATAC-seq experiments performed on 4-OHT or ETOH-treated Chd1iKO MEFs, Cells were trypsinised at ~70% confluency, washed with PBS and 100,000 cells per sample were processed using the Active Motif ATAC-Seq Kit according to the manufacturer’s instructions. For ATAC-seq performed on STA-PUT-purified spermatocyte F2 fractions. Cell pellets were washed in PBS, and 40,000 cells per sample were processed using the Active Motif ATAC-Seq Kit according to the manufacturer’s instructions. For ATAC-seq performed on 4-OHT or ETOH-treated Chd1iKO MEFs, Cells were trypsinised at ~70% confluency, washed with PBS and 100,000 cells per sample were processed using the Active Motif ATAC-Seq Kit according to the manufacturer’s instructions.
</details>

- Two sets of ATAC-seq libraries were generated: meiotic and somatic. Meiotic libraries were prepared from STA-PUT purified spermatocyte (F2) fractions, with three biological replicates per condition. Somatic libraries were generated from mouse embryonic fibroblasts (MEFs) derived from a single Control and a single Chd1iMN mouse, with three replicate libraries per condition. All ATAC-seq data were processed using the same pipeline.      
- Libraries were sequenced on an Illumina NextSeq 550 platform using paired-end 75 bp reads, using the digitonin conditions provided with the kit. ATAC-seq data were processed using the nf-core/atacseq pipeline implemented in Nextflow 120. Adapter trimming and quality filtering were performed using Trim Galore! 121, reads were aligned to the mouse reference genome (GRCm38/mm10) using BWA-MEM 126, and mitochondrial reads, PCR duplicates, and low-quality alignments were removed using SAMtools 127 and Picard. To perform differential chromatin accessibility analysis, peaks were called for each replicate using MACS2 v2.2.7.1 128, the resulting files were assessed using DESeq2 125 to compare control and Chd1iMN conditions. The differentially accessible regions (FDR < 5%) were assigned to genome features using HOMER v4.10 129 and the same Ensembl release of Mus musculus GRCm38/mm10 genome annotation.__ANALYSIS 1__ __Figure S3C__ To visualize the fragment length distribution, unnormalized alignment files were merged per condition and the histograms were generated with number of fragments normalized to one million mapped fragments within each condition.__ANALYSIS 2__ __Figure 3A; Figure S3A,B,I__      
- Genome-wide ATAC-seq coverage tracks were generated from the merged alignment files for each condition using bamCoverage from deepTools v3.4.3 130, CPM method was used to normalize the coverage. To visualise the genome-wide chromatin accessibility in genomic bins, ATAC-seq coverage was calculated for each 2kb genomic bin using the merged and normalized BigWig files and plotted as a scatterplot for both conditions. Bins from sex chromosomes and bins overlapping annotated transcription start sites were highlighted with color. Gene annotations were obtained from Ensembl release 95 for the Mus musculus GRCm38/mm10 genome assembly. __Figure 3B,C,D,E,F; Figure S3H__ To couple the promoter accessibility derived from ATAC-seq and RNA abundance derived from RNA-seq data, promoter regions from the Mus musculus GRCm38/mm10 genome annotation (Ensembl release 95) were coupled with featureCounts RNA-seq DESeq2 analysis output based on gene ID. __Figure 3H, Figure S3D,E,F__ The coordinates of double-strand break (DSB) hotspots were used from Lange et al., 2016, the DSB hotspots are sorted based on the annotated SPO11-oligo coverage per hotspot and the top 10% are visualised. __Figure 5A,B,C__


```
ATAC-seq FASTQ
        │
        V
nf-core/atacseq
        │
        V
       BAMs -> MACS2 peaks -> DeSeq2 -> HOMER assign peaks to genomic features -> ANALYSIS 1 (Visualisation of changed accessibility peaks among genome features) (Figure S3C)
        |
        V
Merged BAMs per condition -> ANALYSIS 2 (Fragment length distribution histograms) (Figure 2A, Figure S3A,B,I)
        |
        V
Coverage and CPM normalisation
     BigWigs -> ANALYSIS 3 (ATACseq coverage in genomic bins) (Figure 3B,C,D,E,F; Figure S3H) + DSB hotspots (Figure 5A,B,C)
        |
        |-> ANALYSIS 4 To couple the accessibility of promoters with RNA abundance of correspondent genes (Figure 3H, Figure S3D,E,F)

```

ANALYSIS 1      
- [DeSeq2_output file]()    
- [DeSeq2 preparations for HOMER .ipynb](HOMER_input_preparation.md)     
- [HOMER_Output_FDR005](HOMER_deseq2_changed_005_out) / [HOMER_Output_FDR001](HOMER_deseq2_changed_001_out)      
- [Changed accessibility peaks accross genome features visualisation .ipynb](HOMER_hist_DeSeq2_cleaned.ipynb)      
__Figure S3C__


ANALYSIS 2    
merged bam files
bams for chrX and for chd3
[Fragment length distribution histogram spermatocytes .ipynb]()      
__Figure 3A; Figure S3A,B__








