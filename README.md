"# scBIO-gut" 
cellule 3 -> print out the number of cells and genes we have in the first place
cellule 3 : Our dataset contains x cells and x genes.
cellule 5 : We filtered out cells expressing less than 200 genes and genes expressed in less than 10 cells. No cells were removed but 5618 genes were removed by this filtering. Thus we end up with x cells and x genes to analyse.
cellule 6 -> print the mean counts
cellule 6 : We used scanpy function to calculate quality control metrics and deduced the mean counts of our dataset as well the total count. The mean counts is x.
cellule 8 : This histogram shows the distribution of the total number of transcripts among our dataset. We end up with a right-skewed distribution which is usually the case in single cell datasets. Majority of cells have between 0 and 5000 transcripts. 
cellule 8 -> retirer le boxplot et la distribution du total de transcripts par gene
cellule 9 -> je vois pas trop la diff avec la cellule 8
cellule 10 -> pas certaine non plus que les violin plots apportent quelque chose
cellule 11 : After filtering the dataset, we need to normalize it. The scanpy funtion normalize_total allows normalization of counts per cell meaning a normalization of each cell by total counts over all genes so that every cell has the same total count after normalization. Then we performed a log1p transformation for better interpretation of the values. These steps are the usual steps used for normalization of single cell datasets and are known as count depth scaling with log plus one transfomation. (cf https://scanpy.readthedocs.io/en/stable/tutorials/basics/clustering.html)
cellule 12 : Next step is the principal component analysis for dimensionnality reduction. In order to determine the number of principal components needed in order to capture the maximum of variance without including noise, we plotted the variance ratio with respect to the number of principal components used. From this curve, we decided to go for 30 pcs, corresponding to the flattening of the curve. Taking more pcs will not necessarly capture more variance but introduce more noise.
cellule 13 : Clustering is performed using Leiden graph-clustering method. it directly clusters the neighborhood graph of cells computed just after PCA. It allows to group cells with similar gene expression. The result from this clustering can be seen visually using UMAP representation.
cellule 14 : The UMAP shows us the different clusters of cells we end up with after PCA and Leiden clustering. We have 12 clusters of cells. All are quite distinct from one another meaning that the cells in the different clusters have sufficiently different genes expressions so that they cluster in separate groups. Those different clusters should correspond to different cells types, 12 different cell types in our case. We need to look more closely to the gene expression pattern of the different clusters in order to determine the cell type corresponding. 
cellule 15 : The function rank_genes_groups allows us to extract the top 3 genes (because of the variable n_genes=3) more expressed in each of our clusters. 
cellule 17 : ???
cellule 18 : The dotplot allows us to visualize how the different clusters (lines) differe from each other in their top expressed genes (columns). Bigger is the dot, more cells in the cluster expresse the gene, darker is the dot bigger is the mean expression of the gene in that cluster. From it we can extract the genes defining the clusters : 
cluster 1 : 
cluster 2 : 
cluster 3 : 
cluster 4 : 
cluster 5 : 
cluster 6 : 
cluster 7 : 
cluster 8 : 
cluster 9 : 
cluster 10 : 
cluster 11 :
cluster 12 : 
cellule 19 -> n'apporte pas plus d'infos que le dotplot avant
