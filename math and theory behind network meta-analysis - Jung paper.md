
## Abbreviations


- ***n*** = number of groups / nodes
- ***m*** = edges
- ***m<sub>direct</sub>***
- ***m´<sub>direct</sub>***
- ***m<sub>indirect</sub>***
- ***{k=/=k´,k,k´=1,....,n}*** = A pair k cannot pair with itself.
- **g** = gene g in collection of genes (g=1,....,G), where **G** is the collection of Genes as a whole.
- **Beta<sub>g</sub>** = log fold change between 2 groups (treatment and control) for gene g.
- SE(**Beta<sub>g</sub>** ) = standard error of **Beta<sub>g</sub>**  
### example

![[Screenshot from 2024-03-23 13-11-00.png]]

In the image you can see a network. There 3 nodes (n=3). There are 3 m´direct green arrows which is the number of independent direct comparisons. mdirect is 2 because there is only 2 direct comparisons between control and treatment 1 and control and treatment 2.
It follows that 

**mdirect'> mdirect** is possible. The number can also be equal.

m<sub>indirect</sub> is the indirect comparison between treatment 1 and treatment 2, given by the dotted gray line. m<sub>indirect</sub> is 1 in this example. m<sub>indirect</sub> is not studied in the original  studies. Instead it is inferred/estimated by the network.


## goal

the goal of network meta-analysis it to make indirect comparisons/ inference. 
-> Find values for m<sub>indirect</sub>

Indirect Comparisons are defined as the difference between all edges and direct edges:

m<sub>indirect</sub> = m - m<sub>direct</sub>


## whats the input? + DE-Analysis

1. I can perform DE-analysis directly on each m´<sub>direct</sub> and merge the results.
2. Alternatively you can merge the data and perform analysis on the merged data. 

## DE-analysis

DE-analysis on each pair k,k' of experimental groups is performed for each gene g separately (via limma package). As result I get the following.
-> coefficient  **Beta<sub>g</sub>** = log fold change between 2 groups (treatment and control) for gene g.
-> standard error of **Beta<sub>g</sub>** = SE(**Beta<sub>g</sub>** )
-> p-value for each gene.

-> Calculations are always **done separately for each gene** and only for genes which **are available in all studies**.


Calculate SE and Log Fold Change for each gene using Limma.

## calculate network

Then **estimate coefficients** for each gene separately.
-> **These are the coefficients for the network. Those are not the same as the limma produced coeffcients**.
 -> limma calculates log fold changes for each study separately. But we need to bring the results together for all comparisons.

![[Pasted image 20240330130750.png]]

Attention: We use the log-fold changes and standard errors for each gene, which we get from the limma package, as input for the network to calculate network coefficients.

We need linear Algebra and matrices to build a network.

Here are the matrices and vectors we need.

beware: **Each calculation is done for each gene separately**. Meaning, 100 genes have each their own of the following matrices, vectors and calculations.
The aim is to determine log fold changes and SE for gene g in the entire network.

## Matrix W

W is a ***m´<sub>direct</sub>*** X ***m´<sub>direct</sub>*** Matrix
- with diagonal values being 1/SE(Beta)^2 
- diagonal takes values between 0 and 1.
- off-diagonals being 0.

Comparisons with high SE get less weight in the network.
-> W works like the resistance in electric networks.
-> High resistance (= high variance/SE) = less weight.

## Vector X

A vector storing log fold changes for individual comparisons.
Those are the original log fold changes from limma
Used as Input for calculating network log fold changes stored in vector **V**.

## Matrix B

M is a ***m´<sub>direct</sub>*** X ***n*** matrix.
row = available direct comparisons.
columns = nodes.

represents connections of the nodes to each other.
1 and -1 represents the connection between 2 nodes.
The rowsum is 0.
Shows for which pairs DE-Analysis are available from the original studies.

Use B and W to calculate 2 Things
- Laplace Matrix
- Moore-penrose Inverse


r = variance of log fold change 
square of r = Standard error.
