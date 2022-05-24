# FairVGNN
This repository is an official PyTorch(Geometric) implementation of FairVGNN in "Fair View Graph Neural Network for Fair Node Representation Learning".

## Motivation
Node representation learned by Graph Neural Networks (GNNs) may inherit historical prejudices and societal stereotypes from training data, leading to discriminatory bias in predictions. This paper demonstrates that feature propagation could vary feature correlations and cause the leakage of sensitive information to innocuous feature channels, which could further exacerbate discrimination in predictions.

As demonstrated by the following Figure on German dataset, the Pearson Correlation of each feature channel to the sensitive feature varies significantly after feature propagation, which further increases the model bias as shown in Figure.


## Framework
To prevent the sensitive leakage caused by feature propagation, we propose a novel framework FairVGNN to automatically learn fair views by identifying and masking sensitive-correlated channels and adaptively clamping weights to avoid leveraging sensitive-related features in learning fair node representations. The whole flowchart of FairVGNN is shown below:

![](./img/fairvgnn.png)


## Result
Here we list the performance of our model (**FairV**). To reproduce the table, please run the following command:
```linux
bash run_german.sh (bash run_{dataset}.sh for other datasets.)
```
![](./img/german_gcn.png)

We want to kindly note that the table is obtained based on the scatter-based propagation, which is a non-deterministic operation (https://github.com/rusty1s/pytorch_scatter/issues/226). Therefore, we would end up with different results after each running. Furthermore, we provide the sparse-matrix-based propagation, which is a deterministic operation. Both of these two versions of propagation are implemented in our repo for GCN baselines.


## Reproduce preliminary results
The prelim folder includes all details to reproduce all preliminary results in this paper.
