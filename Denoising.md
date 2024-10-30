## Denoising

We would not want noise to affect the automatic segmentation further down the line, therefore, denoising must be performed. Denoising can lead to blurring of boundaries, loss of some information about the neuroanatomy, etc., we are okay with it as long as we do not lose the neuroanatomical **structure** during the process. The paper assumes gaussian noise in the 3d images and uses the BM4D denoiser on individual channels of the data. 

### Causes of the noise

- "Voxel colors within a neurite can drift along the neurite"*, In other words, the colors of the voxels which represent the neurite can get altered as you go along the neurite, drifting in color. This can be a gradual drift or high frequency variations. The reasons for this variability can be summarized as:
  - Stochastic expression of the colors of fluorescent proteins, which just means that the colors show up randomly, in no particular pattern.
  - Protein density along the neurite.
  - Some proteins are membrane binding while others stay in the cytoplasm resulting in a difference in color intensity.

### Collaborative Filtering

The term is used most in *recommender systems*, where this technique makes predictions about a user's likes and dislikes based on the preferences of other users who share similar tastes. In the context of image denoising, collaborative filtering finds similar patches, regions with similar intensities, texture, patterns, etc., and denoises them collectively in an additional dimension. 

The additional dimension is important because this filtering technique is not applied in the traditional physical dimensions such as x, y and z but rather on a higher dimension consisting of a group of similar patches. Traditional filters such as the gaussian are applied in the physical dimensions where the neighbourhood of pixels contributing to the filtering is based on **spatial proximity**. In collaborative filtering the neighbourhood consists of regions with **content similarity** even if they are far apart in space. It is because of this property of collaborative filtering that it preserves structural information in the image by consistently removing noise across similar patches.

### BM4D Denoiser

BM4D and BM3D work on similar principles which involve block matching, collaborative filtering, hard thresholding and wiener filtering (optional). Patches are grouped if their disimilarity falls below a certain threshold, after which all the groups are stacked to form a higher dimensional shape and the filtering is applied across each group. The inverse transform of the filtering is computed to reproduce the filtered blocks back as a 3d image. The higher dimension allows BM4D to leverage spatial redundancy. 

This method was introduced in, "EXACT TRANSFORM-DOMAIN NOISE VARIANCE FOR COLLABORATIVE FILTERING OF STATIONARY CORRELATED NOISE" by Ymir Mäkinen, Lucio Azzari, and Alessandro Foi. 

In our context, we use BM4D denoiser for 3D images. The paper [1] shows that boundaries are preserved in the denoised images. In bm3d_tut.ipynb, I have used the bm3d filter on a sample of images to see the effects. We can compare the output of this denoising with gaussian, mean filter, sobel filters, median filters, mean shift and other such methods. Mean shift is implemented in MEAN_SHIFT.m in matlab. The results have been compiled in Results.pdf.
