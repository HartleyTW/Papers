## Title
Learning Spatio-Temporal Representation with Pseudo-3D Residual Networks


## Authors
Zhaofan Qiu, Ting Yao, and Tao Mei


## Link
<http://openaccess.thecvf.com/content_iccv_2017/html/Qiu_Learning_Spatio-Temporal_Representation_ICCV_2017_paper.html>


## Published
ICCV 2017


## Date Read
28th September 2018


## Summary
This paper introduces the concept of decomposing a 3D convolution into two
components, a 2D spatial convolution, and a 1D temporal convolution (N.B this
paper is the genesis for A Closer Look at Spatiotemporal Convolutions for Action
Recognition). They build a resnet style network around these new blocks. They
investigate three designs of block: 

- direct influence where spatial feeds into temporal and then joined with
residual input.

- Indirect influence where the input goes to both temporal and spatial
convolutions and both output to the residual input.

- Joint influence, a combination of the two where input goes to spatial
convolution, and it's output feeds into both the residual input as well as the
temporal convolution.

These three blocks are then built into bottle neck style units that begin and
end with a 1 x 1 x 1 convolution. They experiment with nets containing the three
different blocks in an interleaved manner.

They then perform a number of experiments which shows that P3D beats the
benchmarks at the time.



## Takeaways

Long paper with lots of experiments. Still some questions about why it's
better to split the temporal and spatial elements. Was it done for model
efficiency or is there a concrete reason that it works better.

The work was built upon by the Du Tran paper from CVPR 18.



