## Dimensionality Reduction

### Watershed Transform

Watershed is a image processing technique used for segmentation. It works well on image where the regions to be segemented are touching each other. The main idea of the watershed is valleys between hills getting filled with water until two distinct sources of water meet each other at the boundaries. This is done by converting the image into a **topological map** which means to convert it into a landscape where, for example, bright/colorful regions are shown as hills and darker/dull regions are shown as valleys. Water sources are placed at the bottom of the valleys. 

[Watershed_Implementation.ipynb](Watershed_Implementation.ipynb) has python implementation of the watershed transform which explains this technique better.

### Topology Preserving Warping
