## Title 
A Closer Look at Spatiotemporal Convolutions for Action Recognition


## Authors 
Du Tran, Heng Wang, Lorenzo Torresani, Jamie Ray, Yann LeCun, Manohar
Paluri


## Link <http://openaccess.thecvf.com/content_cvpr_2018/papers/Tran_A_Closer_Look_CVPR_2018_paper.pdf>


## Published 
CVPR 18


## Date 
Read 26th September 18


## Summary 
The paper investigates a number of architectures based on
spatiotemporal convolutions, primarily based around C3D. The m5 model types they
investigate are:

R2D: (2D resnets)

MCx and rMCx: nets that combine blocks of 3D and 2D convolutions ie. MCx is 3D
then 2D whilst rMcx is 2D then 3D.

R3D: 3D resnets

R(2+1)D: A combination 2D and 1D convolutions. The 2D performs a spatial
convolution followed by a 1D convolution over the temporal extent. The benefit
of this is to double the number of non-linearities, allowing more complex
functions to be represented.

The paper tests these architectures against the kinetics dataset using 8 frame
and 16 frame inputs. The R2D networks perform poorly suggesting that there is
benefit to using 3D convolutions that don't collapse the temporal element of the
input clip. The R3D architecture performs the second worst followed by MCx and
rMCx. Of these two 3D Convolutions followed by 2D Convolutions performs best.
Finally the best perform architecture is R(2+1)D which they carry forward for
further experiments.

They show results for R(2+1)D trained on RGB inputs as well as optical flow (computed using Farnebacks method) as well as a two stream version. The two stream version ultimately performs better compared to the single stream version. They also experiment with varying the pre-training dataset and find, as I3D did, that Kinetics is better for pre-training than sports-1M.


They perform comparisons with the current state of the art network - I3D and
find that theirs is marginally worse (~0.1-0.3%) when reporting against the
kinetics dataset. I3D did not give results for Sports-1M.


## Takeaways

I think it's interesting that two stream networks seem to win again.

Does the splitting of 3D conv blocks into seperate 2D and 1D blocks suggest that temporal and spatial signals should always be looked at separately.



