##  To prepare HOMER input file from DeSeq2 output and run HOMER 


in Python

```
ATAC_deseq2 = pd.read_csv('/users/uladzis.khauratovich/groups_SLAVA/ATAC_Seq/ATAC_RNA_Seq/ATAC_analysis_Claudia_files/controlvsexperimental.mRp.clN.deseq2.results.txt', sep="\t")

ATAC_deseq2_homer = ATAC_deseq2[['Geneid', 'Chr', 'Start', 'End', 'Strand']].copy()
ATAC_deseq2_homer.columns =['PeakID', 'chrom', 'start', 'end', 'strand']
ATAC_deseq2_homer['chrom'] = 'chr' + ATAC_deseq2_homer['chrom'].astype(str)

ATAC_deseq2_homer.to_csv('/users/uladzis.khauratovich/groups_SLAVA/ATAC_Seq/HOMER/ATAC_deseq2_homer_peak.txt', sep='\t', index=False)

```

in Bash

```
module load homer/4.10-foss-2018b
module load perl/5.28.0-gcccore-7.3.0

# HOMER was preinstalled on cluster
/software/2020/software/homer/4.10-foss-2018b/bin/annotatePeaks.pl

#the command from documentation i'm going to use
annotatePeaks.pl <peak/BED file> <genome> -hist   > <output file>
perl /software/2020/software/homer/4.10-foss-2018b/bin/annotatePeaks.pl deseq2_peaks_FDR005_homer_input.txt mm10 -gtf /users/uladzis.khauratovich/groups_SLAVA/ATAC_Seq/HOMER/Mus_musculus.GRCm38.95.chr.gtf -hist > Somatic_atac_deseq2_results_HOMER_output

```
