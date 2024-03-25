Authors: Christine Winter 1 , Robin Kosch 1 , Martin Ludlow 2 , Albert D. M. E. Osterhaus 2 and Klaus Jung 



## aim of the paper

----------------------------------------------------

1. The aim is to compare network meta-analysis and traditional meta-analysis on gene expression data as a tool for indirect inference.
2. analyse, how strong the list of differently expressed genes differs between network meta-analysis and traditional meta-analysis.
3. How strong do indirect log fold changes correlate between network meta-analysis and meta-analysis, but also to the true fold changes.
4. show limitations and benefits for both meta-analysis and network meta-analysis, by applying both to real data.


---------------------------------------------------




## significance for field, knowledge-gap and motivation

----------------------------------------------------

### gap: 

traditional meta analysis is not suited for gene expression data because of batch effects.

network meta analysis are already used for comparisons of clinical trials.
But not for expression data. for gene expression data only traditional meta-analysis has been used so far. this is the first paper that applies network meta-analysis to gene expression data.


### motivation: 

network meta analysis allows comparisons without batch effects.



### significance

"Published examples of network meta-analysis are for example the comparison of the efficacy of different treatments against each other , the comparison of different therapies, or the study of safety of different drugs."
-> network meta-analysis allows us to make indirect comparisons between groups and **allows us to compare the effect of treatments, infections and disease on the gene expression without batch effects**.


-----------------------------------------------------




## Background and important aspects about network meta-analysis

--------------------------------------------------


### difference between network meta-analysis and traditional meta-analysis

*"In contrast to ‘traditional’ meta-analysis which aggregates studies on the same study question, network meta-analysis also involves studies on different study questions which are linked by pairwise same treatment"*

*"Treatment comparisons that have not been studied in the original studies can indirectly be made within the network meta-analysis."*


Traditional Meta-Analysis: This involves pooling data from multiple studies that address the same research question or hypothesis. For example, if researchers are investigating the effectiveness of a particular drug for treating a certain condition, they would gather all relevant studies that have investigated this drug for that specific condition.

Network Meta-Analysis (NMA): NMA takes a broader approach by not only including studies that directly compare the same interventions for the same condition but also incorporating studies that compare interventions for different conditions as long as they have at least one common treatment being compared. This common treatment acts as a bridge, allowing for indirect comparisons between interventions across different studies.

In traditional meta-analysis, the focus is typically on pooling data from multiple studies that assess the effectiveness of a single drug (or intervention) for a specific condition or research question. The goal is to provide a summary estimate of the overall effect of that particular drug across all included studies.
On the other hand, network meta-analysis (NMA) expands on this by allowing for comparisons across multiple interventions, including different drugs or treatments, even if they were not directly compared within individual studies. 
This means that NMA can simultaneously assess the effectiveness of multiple interventions for a given condition, providing insights into their relative efficacy compared to one another.

In summary:
Meta-analysis typically focuses on aggregating studies that evaluate a single intervention for a specific condition.Network meta-analysis allows for comparisons across multiple interventions, facilitating indirect comparisons between treatments even if they were not directly compared in individual studies.You can compare different drugs and interventions against each other in NMA.
Common meta analysis can only handle one drug/treatment.

### batch effects

*"Merging of high-dimensional expression data can, however, implicate batch effects that are sometimes difficult to be removed. Removing batch effects becomes even more difficult when expression data was taken using different technologies in the individual studies (e.g. merging of microarray and RNA-seq data)."*

meta-analysis of expression data requires merging of data. merging causes batch effects. batch effects get worse when different technologies are used.

1. Meta-analyses have issues with batch effects.
2. Network analyses do not have a problem with batch effects since data are not merged.

Therefore, the results of network analyses are much closer to true results than meta-analyses.
Network analyses are preferred when batch effects have a strong impact (which should actually always be the case, right?).
For example, I cannot compare RNA-Seq studies with microarray studies because the technologies are different.

*"However, even after applying a batch effect removing step onto the merged data false discoveries may occur"*
- even after batch effect removal false discoveries occur in meta analysis.



### indirect inference

Comparisons, which have not been made in the original studies can now be studied.

see dotted lines in: ![[Screenshot from 2024-03-23 13-11-00.png]]



### paper-specific knowledge

#### whats the effect size for transcriptomics (strength of relationships)?


The effect size in meta-analysis typically represents the magnitude of the relationship between variables or the difference between groups. Examples of effect sizes include the mean difference, odds ratio, risk ratio, correlation coefficient, and many others, depending on the type of data being analyzed.
the standard error (SE) is a crucial measure used to quantify the uncertainty surrounding the estimated effect size.

**Here log fold changes are used as effect measure and the standard error of the log fold changes measures the uncertainty**.

Goal: **find/determine indirect log fold changes and their SE**.
indirect -> the log fold changes for the dotted line/ indirect comparisons.

## Results, findings and conclusions

- *"results from analyzing merged data sets and the results from network meta-analysis are highly correlated in simple study networks."*
- *"(if an) edge in the network is supported by multiple independent studies, network meta-analysis produces fold changes that are closer to the simulated ones than those obtained from analyzing merged data sets."*
- *"This method (network meta-analysis) is especially advantageous when batch effects between studies are hard to get removed."*
- choice between traditional meta-analysis and network analysis has consequences on the biological interpretation: you get different DE-Genes for both leading to different interpretations.
- the results of network meta-analysis are highly correlated with the results of merged data analysis in simply study networks
- network meta-analysis showed a higher correlation with the true fold changes than merged data analysis when one edge of the network was supported by multiple independent studies. This shows that batch effect removal doesn´t work when edges are supporte dby multiple studies.
- Used simulated studies: The results could be too optimistic. Maybe missed some batch effects not simulated by ComBat package.
- 

### append: genes found - not necessary to understand network meta-analysis but interesting.

![[Pasted image 20240325123839.png]]


"CXCR3 is expressed on activated T-lymphocytes, natural killer cells and on B-lymphocyte subsets and mediates T-cell migration into inflammatory areas of the nervous system during viral infection"

"CXCR3-deficient mice showed an increased mortality rate (associated with higher viral load) after West Nile Virus (WNV) or dengue virus infection hat can also lead to neuropathic diseases"

"In contrast, an elevated level of viral clearance was observed during HSV-1 encephalitis in CXCR3-deficient mice resulting in reduced clinical signs and mortality"

"CXCR3activation lead to transactivation of pro-inflammatory genes, and initiation of apoptosis in neurons. To prevent neuronal cell death during WNV Encephalitis, WNV-infected cells induce TNFα-regulated signaling pathways which result in down regulation of CXCR3"

"COX7B is one of the small, nucleus-encoded subunits of cytochrome c-oxidase, the terminal complex in the mitochondrial respiratory chain. The small subunits have regulatory functions and play an essential role in complex assembly . Furthermore, mutations lead to microcephaly, indicating a role for COX7B in brain and eye development . Expression changes of COX7B have also been described during the development of neurodegenerative diseases"

"nti-PNMa1 autoantibodies can be found in patients with paraneoplastic neurological disorders  in connection with brainstem or limbic encephalitis, hypothalamic disorder and dementia. Furthermore, PNMA1 expression is also increased in apoptotic neurons, although the underlying mechanism is poorly understood"

"Lymphotoxin B (LTB) is a type II membrane protein encoded by the LTB gene and plays a key role during lymph node development, LTB gene deletion in mice leads to a lack of peripheral lymph nodes and Peyer’s patches.LTB only binds its receptor LTBR, leading to NFκB activation and cell death"

"Mitofusin 2 (MFN2) GTPase is a mitochondrial membrane protein that is also crucial in mitochondria metabolism.Mitofusin 2 (MFN2) GTPase is a mitochondrial membrane protein that is also crucial in mitochondria metabolism. The loss of MFN2 lead to an enhanced virus-induced synthesis of IFNβ and decreased viral reproduction"

"Thyroid Peroxidase (TPO) is expressed in the thyroid gland and is essential for thyroid hormonogenesis. Nevertheless, TPO promotor also contains aspecificNFκB binding site, leading to transactivation after (LPS) stimulation"

"SLC4A1 is a chloride-bicarbonate exchanger expressed in erythrocytes and intercalated cells of renal collecting ducts. Mutations of SLC4A1 have been described associated with distal renal tubular necrosis and haemolytic anemia"
