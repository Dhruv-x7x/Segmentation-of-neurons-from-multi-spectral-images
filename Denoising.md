## Denoising

We would not want noise to affect the automatic segmentation further down the line, therefore, denoising must be performed. Denoising can lead to blurring of boundaries, loss of some information about the neuroanatomy, etc., we are okay with it as long as we do not lose the neuroanatomical **structure** during the process. The paper assumes gaussian noise in the 3d images and uses the BM4D denoiser on individual channels of the data. 

### Causes of the noise

- "Voxel colors within a neurite can drift along the neurite"*, In other words, the colors of the voxels which represent the neurite can get altered as you go along the neurite, drifting in color. This can be a gradual drift or high frequency variations. The reasons this variability can be summarized as:
  - Stochastic expression of the colors of fluorescent proteins, which just means that the colors show up randomly, in no particular pattern.
  - Protein density along the neurite.
  - Some proteins are membrane binding while others stay in the cytoplasm resulting in a difference in color intensity.
