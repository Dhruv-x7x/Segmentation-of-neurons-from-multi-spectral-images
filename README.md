![Segmentation-Of-Neurons-From-Multi-Spectral-Images](https://biox.stanford.edu/files/styles/wide/public/ting_news_banner_large.webp?orig=png)
# Segmentation-Of-Neurons-From-Multi-Spectral-Images
The research paper titled "Automated scalable segmentation of neurons from multispectral images." is discussed here in layman terms and an attempt to implement segmentation algorithms on various datasets.

[1] Uygar Sümbül, et al. (2016). Automated scalable segmentation of neurons from multispectral images. [online] Neural Information Processing Systems (NIPS 2016). Available at: https://arxiv.org/abs/1611.00388 [Accessed 20 Jul. 2024].

This is purely for educational purposes, all credits go to Uygar Sümbül et al.

## Abstract
```
"Reconstruction of neuroanatomy is a fundamental problem in neuroscience. Stochastic expression of colors in individual cells is a promising tool,
although its use in the nervous system has been limited due to various sources of variability in expression. Moreover the intermingled anatomy of
neuronal trees is challenging for existing segmentation algorithms. Here, we propose a method to automate the segmentation of neurons in such
(potentially pseudo-colored) images. The method uses spatio-color relations between the voxels, generates supervoxels to reduce the problem size
by four orders of magnitude before the final segmentation, and is parallelizable over the supervoxels. To quantify performance and gain insight,
we generate simulated images, where the noise level and characteristics, the density of expression, and the number of fluorophore types are variable.
We also present segmentations of real Brainbow images of the mouse hippocampus, which reveal many of the dendritic segments"
```

**Spatio-color** relations means that the algorithm identifies neurons with same color/intensity and their position in space. Since we are using voxels, there is a third dimension, depth, which can be used for spatio-relations. 

**Voxel** is a 3D pixel. In 3D images, the smallest unit is called a voxel, volumetric pixel. A **supervoxel** is a group of similar voxels.

In layman terms, the problem the paper is trying to solve is the difficulty in automatic segmentation of neurons in 3D images due to their massive dataset size. Reconstructing the neural structures or the **neuroanatomy** helps neuroscientists understand the brain more but its not easy. One method to do this is to use **fluorescent** proteins that go to each neuron and label them with different colors, **stochastically** (randomly). Now that the neurons are colored, we can see each individual neuron and map it out but this method has its limitation as the color that expresses depends on too many factors. This is unreliable because you can have some neurons close together with the same colors, or one neuron with multiple colors or color changing over time, we can not control this. So, they take 3D images of the anatomy and have segmentation algorithms separate out individual neurons. This works but is harder to realize because 3D images are a really large dataset. The paper talks about an algorithm that groups together similar voxels based on their **spatio-color** relations to create supervoxels. This reduces the dataset size by an order of four, which means 10000 times smaller dataset. Now, the segmentation algorithms can be applied more easily and even be parallized over the supervoxels. 

The paper goes on to test the viability of their method on their own generated images and also on actual Brainbow images of the mouse hippocampus.
