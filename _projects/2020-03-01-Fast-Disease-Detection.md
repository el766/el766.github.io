---
layout: single
title: Fast Disease Detection Network
header:
  teaser: /assets/images/Disease_Detection/Teaser.png
---
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/Disease_Detection/bitmap.png" alt="">

Pixel level segmentation has its unique advantage in image-based plant disease detection. The segmentation mask approximates the irregular shape of the infection in the image, making the data annotation and human verification straightforward. Moreover, the output mask correlates with the size of the observed infection, which can be linked to the disease severity rate. However, compared to image level classification or bounding box detection tasks, segmentation is usually more time and resource consuming, especially on high resolution images used in disease detection.

While we developed our [PhytoPatholoBot](/projects/2020-07-20-PPB/), we noticed that none of the existing real-time segmentation methods can achieve the speed we required while maintaining accuracy comparable to our off-line baseline method. Therefore, we started to design a customized network for our needs. 

The key principle is to keep the feature map resolution high in the network while reducing the time for processing these feature maps. The famous Deeplab structure used dilated convolution, which effectively maintained the resolution but also increased the computation cost. Alternatively, we used transposed convolutions aggressively to restore the feature map resolution in a side branch while allowing the feature map resolution to decrease as normal in the main ResNet based backbone. We also introduced the addition operation-based skip connection in both the backbone and segmentation head to merge the multi-scale information more effectively. Our customized network achieved the best efficiency-accuracy trade-off comparing to other state-of-the-art methods, and our work was presented on IROS2022 ([Paper link](https://ieeexplore.ieee.org/abstract/document/9981404)).


<img src="{{ site.url }}{{ site.baseurl }}/assets/images/Disease_Detection/result.png" width="75%" height="75%" alt="">
