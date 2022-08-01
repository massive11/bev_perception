# 3D Object Detection with Depth

## Abstract

* [BEVDepth](#BEVDEPTH)

## Details

* [MEGVII Technology] BEVDepth<spain id = "BEVDEPTH"></span>

  * BEVDepth认为许多最新的工作虽然加入了深度估计，但这种深度估计得到的信息是在没有相机信息的情况下隐式学习的，这使得它实际上是伪点云的伪深度。BEVDepth通过编码相机的内外参得到了显式的深度估计。

    结合代码来看，本文在基于LSS的投影部分之上加入LiDAR提供的点云数据作为ground truth，监督通过编码内外参得到的深度，以此矫正像素的深度分布估计。这种方法让模型能学习到更接近实际情况的深度预测，因此实现了大幅度的精度提升。

    在时序部分，本文先将前后帧的BEV特征图进行空间对齐，然后参考FlowNet的方法，将两帧BEV特征直接concat起来。