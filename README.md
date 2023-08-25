# Normative-Sex-Differences
Here, we investigate sex differences in structural MRI derived measures of brain volume in both humans and mice.

This repository contains all of the data, code, and text necessary to rerun analyses found in the preprint:
Elisa Guma, Antoine Beauchamp, Siyuan Liu, Elizabeth Levitis, Jacob Ellegood, Linh Pham, Rogier B Mars, Armin Raznahan *, Jason P Lerch *, (2023). Comparative neuroimaging of sex differences in human and mouse brain anatomy, Preprint: https://doi.org/10.1101/2023.08.23.554334
*Equal contribution

Article accessible here: https://www.biorxiv.org/content/10.1101/2023.08.23.554334v1

# Project overview

We use  cross-species structural magnetic resonance imaging to carry out the first comparative neuroimaging study of sex-biased neuroanatomical organization of the human and mouse brain.

# File description

In the input data folder, you will find the raw and pre-processed human and mouse data used for this study. 

## Input_data:
### Human_anatomy: 
The human data comes from Human Connectome Project (HCP) 1200 release (3T T1-weighted 0.7mm3 sMRIs from healthy young adults, 597 females/496 males aged 22-35 years).

_HCP_demographics_QC.csv_: demographics file

_df_HCP_volumes_clean.csv_ (also available as RDS): aggregated volumes used for analysis include cortex (Glasser), subcortex (aseg), amygdala and hippocampal subfields, brainstem subdivisions, and hypothalamus volumes. These were generated from data files found in the raw_data_human folder, which includes the R script used to clean the data

_HCP_homologs_aggregated.csv_ (also available as RDS): aggregated volume for homologous brain regions, derived from the script found in the analysis_scripts/cross_species/ folder.

_mz_twins_1.csv_: contains info for twin and sibling pairs for HCP

### Mouse_anatomy:

_Volumes_150.RData_: mouse volumes in tree form as RData

_Allen_hierarchy_definitions.json_: required to create a tree and ascribe hierarchy to regions (i.e., parents, children, siblings, etc)

_DSURQE_40micron_average.mnc:_ average brain file for DSURQE atlas useful for plotting

_DSURQE_40micron_labels.mnc:_ label file for DSURQE atlas

_DSURQE_40micron_R_mapping.mnc:_ mapping of labels from DSURQE atlas 

_full_mouse_sampletree.RDS:_ mouse data in tree form as an RDS

_Mouse_demographics:_ demographics for mice

_Mouse_homologs_aggregated_postcombat.csv_ (also available as RDS): volumes from aggregate homologous regions, derived from the script found in the analysis_scripts/cross_species/ folder. 

_mouse_volumes_tree.RData_: mouse volumes in tree form

_Variance_analysis_mouse_2.csv_ and _Variance_analysis_mouse_noTTV_2.csv_: necessary for running the Variance analysis

### Gene_expression:

**Raw data files:**

_Mouse_expression_matrix.csv:_ raw gene expression data from Allen Mouse Brain Atlas for all genes

_Human_expression_matrix.csv:_ raw gene expression data from Allen Human Brain Atlas for all genes

_MouseHumanGeneHomologs_edited.csv:_ list of homologous genes for humans and mice

_Aggregated_human_gene_expression.csv _(also available as .RDS): averaged human gene expression data for homologous brain regions

**Chromosome info:**
_Human_chromosome_genes.csv_: links human gene names to location on chromosomes

_Mouse_chromosome_fullinfo.csv:_ links mouse gene names to location on chromosomes

_Chromosome_key_allen.csv_: required for the mouse data

_Weights_for_aggregation_human.csv:_ information required to compute the weighted gene average based on the volume of subregions in the human atlas

**Aggregated data:**

_Aggregated_mouse_gene_expression.csv_ (also available as .RDS): averaged mouse gene expression data for homologous brain regions

_Transposed_homologous_human_genes_weighted.csv _(also available as .RDS): averaged homologous human gene expression data for homologous brain regions

_Transposed_homologous_mouse_genes.csv_ (also available as .RDS): averaged homologous mouse gene expression data for homologous brain regions

**Other analysis files:**

_Df_corr_expression.csv:_ correlation of all homologous genes across homologous brain regions

_X_chromosome_genes.csv:_ list of x-chromosome genes that are also homologous

_tree_tools.R_: tools required to prune the tree, useful for script in analysis_scripts/cross_species/ folder.

**Sex hormone files: **

Homologous sex hormone genes: _sex_hormone_genes_short.csv,_ 

Homologous androgen genes: _sex_hormone_genes_male_short.csv,_ 

Homologous estrogen and progesterone genes: _sex_hormone_genes_female_short.csv_

### Analysis_scripts: 
these scripts perform all analyses included in the manuscript, and are also used to generate tables and figures

**Cross_species:**

_Sex-diffs-homologous-ROIs.Rmd:_ Aggregates volumes for homologous brain regions in humans and mice; 
Runs Combat harmonization on mouse data to account for different studies;
Runs a linear model in each species testing for sex differences and covarying for total brain volume, age, and euler number for humans, and total brain volume, age, and background strain in mice; 
Correlates effect size for sex computed from those linear models across all regions, and for cortex and non cortex separately

**Gene_expression_scripts**

_Gene-resampling.Rmd:_ script to use to generate null distribution as a control for gene subset analyses

_Homologous_gene_analysis.Rmd:_ analysis script used to compute analyses evaluating whether the cross-species similarity of neuroanatomical sex differences in related to the cross-species similarity of homologous gene expression patterns across homologous brain regions

_Human_expression_data_cleanup.Rmd: _script used to filter gene expression data to homologous brain regions, and to filter those genes to only include homologous genes. 

_Mouse_expression_data_cleanup.Rmd:_ script used to filter gene expression data to homologous brain regions, and to filter those genes to only include homologous genes. 

_Sex-hormone-gene-lists.Rmd:_ script used to query Gene Ontology database to get a list of sex hormone genes (androgen, estrogen, and progesterone). In the script, I also filter by homologous genes.

**Human_anatomy**

_Human_total_regional_volume_analysis.Rmd:_ script used to run linear model to look at sex differences in total and regional brain volume and variance in volume.

_Human_analysis_notwinpairs.Rmd:_ script used to assess whether including of twin pairs affected sex-difference maps

**Mouse_anatomy**

_Mouse_total_regional_volume_analysis.Rmd_: script used to run linear model to look at sex differences in total and regional brain volume and variance in volume.

