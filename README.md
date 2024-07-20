# Segmentation-Of-Neurons-From-Multi-Spectral-Images
The research paper titled "Automated scalable segmentation of neurons from multispectral images." from Uygar Sümbül et al. is discussed here in layman terms and an attempt to implement segmentation algorithms on various datasets.

## Abstract
```
"Reconstruction of neuroanatomy is a fundamental problem in neuroscience.
Stochastic expression of colors in individual cells is a promising tool, although its
use in the nervous system has been limited due to various sources of variability in
expression. Moreover, the intermingled anatomy of neuronal trees is challenging
for existing segmentation algorithms. Here, we propose a method to automate the
segmentation of neurons in such (potentially pseudo-colored) images. The method
uses spatio-color relations between the voxels, generates supervoxels to reduce
the problem size by four orders of magnitude before the final segmentation, and is
parallelizable over the supervoxels. To quantify performance and gain insight, we
generate simulated images, where the noise level and characteristics, the density
of expression, and the number of fluorophore types are variable. We also present
segmentations of real Brainbow images of the mouse hippocampus, which reveal
many of the dendritic segments"
```
In layman terms, the problem the paper is trying to solve is the automatic segmentation of neurons in 3D images. Reconstructing the neural structures or the **neuroanatomy** helps neuroscientists understand the brain more. One method to do this is to use **fluorescent** proteins that go to each neuron and label them with different colors, **stochastically** (randomly). Then the algorithm groups together similar voxels based on their **spatio-color** relations to create supervoxels.

**Spatio-color** relations means that the algorithm identifies neurons with same color/intensity and their position in space. Since we are using voxels, there is a third dimension, depth, which can be used for spatio-relations. 

**Voxel** is a 3D pixel. In 3D images, the smallest unit is called a voxel, volumetric pixel. 


