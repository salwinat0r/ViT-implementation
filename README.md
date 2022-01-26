# Vision Transformers (ViT) Implementation

- Paper - [An Image is worth 16x16 words](https://arxiv.org/pdf/2010.11929.pdf)
- Annotated [paper](https://github.com/salwinat0r/ViT-implementation/blob/main/An%20Image%20Is%20Worth%2016x16%20Words%20-%20Annotated.pdf) by labml.ai.


## Notes

### Intuition
 
- ViTs or attention based models in general require substantially fewer computational resources to train. 
 
- This was the main reason to use them for vision based problems.

- Large scale image recognition models, like ResNet are better than attention based vision models
 
- An image is split into **patches** and a linear embedding (**unrolled image patches multiplied to the embedding matrix**) of these patches are provided as inputs to the Transformer. Images patches are analogous to **tokens**

- The authors rely on global attention rather than local attention which would require lot more computational resources since then each pixel would have to attend every other pixel

- When trained on mid-sized datasets, transformers yield not so good results compared to ResNets. This is because CNNs have the inductive bias of focusing on [local areas.](https://poloclub.github.io/cnn-explainer/assets/figures/convlayer_detailedview_demo.gif)

- This, however changes when the model is trained on larger dataset (14M-300M images) and outperforms conventional ConvNet architectures significantly.

### Benchmarks

| Dataset | Accuracy|
| ---- | ---- |
| ImageNet | 88.55% |
| ImageNet-ReaL |90.72% |
| CIFAR-100 |77.63% |
|VTAB |77.63 |

### The Model
![](https://i.imgur.com/PqpfoIK.png)

#### Model Variants
![](https://i.imgur.com/O2cS7iz.png)


### Results
1. Vision Transformers dominate ResNets on the performance/compute trade-off
2. ViT use $2-4$X to attain the same performance.
3. **Hybrid models** slightly outperform vanilla ViTs are small computational budgets.
4. On increasing the depth of the network, the _mean attention distance_ also increases.
<img src="https://i.imgur.com/8ycad9B.png" alt="scikit_learn" width="300" height="300"/>.
This means that ViTs can attend to pixels that are far away in the lower layers itself

![visualizing-conv-filters-vs-vit](https://theaisummer.com/static/1a825502d30ae8a5fde3386057ed1ef5/39a20/visualizing-conv-filters-vs-vit.png "visualizing-conv-filters-vs-vit")
### The ViT architecture
- The first layer consists of flattened image patches into a lower-dimensional space.
- After this, a learned position embedding is added to patch representations. Closer (adjacent) patches tend to have more similar position embeddings.
- It was found that self attention allows ViT to integrate information across the entire image even in the lowest layers.
- The **attention distance** is the average distance between the query pixel and the rest of the patch.
- This architecture doesn't consist of a decoder network.
- The model attends to image regions that are semantically relevant.
![visualizing-attention-vit](https://theaisummer.com/static/f7115f622470f12aac4bbb7a20dea366/c1b63/visualizing-attention-vit.png "visualizing-attention-vit")


### Conclusion
The papers revolves around using images as sequence based inputs(patches) and doesn't rely on image-specific inductive biases. This Transformer when pre-trained on large datasets, performs exceedingly well

---
tags: #🌲 #papers 
