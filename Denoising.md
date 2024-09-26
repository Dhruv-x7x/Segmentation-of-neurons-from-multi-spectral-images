## Denoising

We would not want noise to affect the automatic segmentation further down the line, therefore, denoising must be performed. Denoising can lead to blurring of boundaries, loss of some information about the neuroanatomy, etc., we are okay with it as long as we do not lose the neuroanatomical **structure** during the process. The paper assumes gaussian noise in the 3d images and uses the BM4D denoiser on individual channels of the data. 

### Causes of the noise

- "Voxel colors within a neurite can drift along the neurite"*, In other words, the colors of the voxels which represent the neurite can get altered as you go along the neurite, drifting in color. This can be a gradual drift or high frequency variations. The reasons this variability can be summarized as:
  - Stochastic expression of the colors of fluorescent proteins, which just means that the colors show up randomly, in no particular pattern.
  - Protein density along the neurite.
  - Some proteins are membrane binding while others stay in the cytoplasm resulting in a difference in color intensity.

### Collaborative Filtering

The term is used most in *recommender systems*, where this technique makes predictions about a user's likes and dislikes based on the preferences of other users who share similar tastes. In the context of image denoising, collaborative filtering finds similar patches, regions with similar intensities, texture, patterns, etc., and denoises them collectively in an additional dimension. 

The additional dimension is important because this filtering technique is not applied in the traditional physical dimensions such as x, y and z but rather on a higher dimension consisting of a group of similar patches. Traditional filters such as the gaussian are applied in the physical dimensions where the neighbourhood of pixels contributing to the filtering is based on **spatial proximity**. In collaborative filtering the neighbourhood consists of regions with **content similarity** even if they are far apart in space. It is because of this property of collaborative filtering that it preserves structural information in the image by consistently removing noise across similar patches.

### BM4D Denoiser

