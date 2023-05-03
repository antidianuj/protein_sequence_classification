## Protein Sequence Classification

## Protein-Protein interaction predicton
Dataset source: https://thebiogrid.org/77183/publication/a-human-protein-protein-interaction-network-a-resource-for-annotating-the-proteome.html


Either using identifier ID (Case-1) or gene names (Case-2) of protein A and protein B, to determine the interaction type. In this course, I considered a study of employing MLP for finding the performance over Case-1 and Case-2. Furthermore, I also employ a possible new approach to feed the temporal information surrounding individual points to study the peroformance over case-2 into a MLP classifier.

This apporach I term as "LSTM-Masked-MLP". Following are the schemes of two topologies associated to it.

### Topology-1

![image](https://user-images.githubusercontent.com/47445756/235841336-c332073a-c6d7-4385-b801-275342b2b1db.png)


### Topology-2

![image](https://user-images.githubusercontent.com/47445756/235841380-53c1cea0-eb54-4d2b-ac93-15e3ce81639b.png)


The difference between topology 1 and 2 is that in topology-1, same MLP is considered over each point at sequence, while in toplogy-2, different MLP is associated with each point of sequence, which are the output hidden states of LSTM. The MLP acts on masked hidden states where the considered hidden state is removed, and the remaining sequency is mapped to a low dimensional sequence. Later, the concatenated output is fed into a classifier like MLP to determine classification probabilities.


Following is the comparison of training accuracy and loss curves during cases of study.

![image](https://user-images.githubusercontent.com/47445756/235841982-d1a29521-be91-4f18-8abd-13b87c6e21a7.png)



## Determination of Gene Ontologies from Protein Interaction Network

The dataset utilized for this case is same as that of the paper "Predicting Multicellular Function through Multi-layer Tissue Networks", which is conveniently utilized via torchgeometric library. The problem can be identified as node classification, where each node is a protein with positional gene sets, motif gene sets and immunological signatures as features.

For the case study of utilizing of Graph Convolution Network (GCN) and Graph Attention Network (GAN), following is the training and validation profile comparison. The bottom accuracy curves are infact validation curves.

![image](https://user-images.githubusercontent.com/47445756/235842749-7f283665-dd5a-4b8e-b44b-19e65e860cb4.png)







