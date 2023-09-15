# The supplmentary for the paper

## 1.Real-world experiment
### Real-world demonstraion:
We provide more video demonstraion on the manipulation process. The video demonstrates that our approach is capable of handling specular or transparent objects successfully. Moreover, even when the depth estimation is not precise enough to enable a direct contact, our method utilizes sensor-based contact detection to facilitate the manipulation process. This capability allows us to achieve successful object manipulation despite the limitations of depth estimation accuracy.
### Comparisons with point cloud:
<p>To substantiate our findings, we offer additional qualitative evidence within real-world setting. 
All experiment specifics align with the details in main paper, aiming to illustrate the limitations of point clouds. 
As illustrated in [xxx], it becomes evident that point clouds exhibit notable limitations when confronted with specular or transparent objects (such as the pan and kettle). For example, due to its intrinsic nature, the faucet comprises sparse points, introducing complexities in both perception and manipulation.
Take the pan as a further illustration – although the lid is transparent, the handle is not, and the transparent component still affects the overall imaging, intensifying the difficulties in perception and manipulation. 
In constract, cost-effective RGB images exhibit dense pixel-wise information to capture specular and transparent object. Therefore, our motivation for this paper is to provide a potential solution of RGB-only manipulation framework, which has its own strength in industrial applications. Though such modality lacks geometry details, we complement by predicting depth to formulate object geometric structure. </p>
<img src="https://github.com/clorislili/imagemanip/blob/main/images/real_pc.png" alt="GitHub Logo" width="500" height="400">


## 2. Token-wise correspondence
<p>We show the visualization of the comparisons of pixel-wise and token-wise correspondenece. Pixel-wise correspondence is obtain with initial depth prediction, which may contain inaccuracy to lead error accumulation. In the top part of the following figure, we can see the misalignment circumstance in pixel-wise correspondence. To address such, we introduce token-wise correspondence which find the correspondence of tokens in high-dimensional feature, in which one token aggregate the feature of 64x64 pixels. It thus is more robust to depth inaccuracy since it does not require accurate pixel-level alignment. We visualize the token-wise corresponce at the bottom part of the figure and only fuse correspondent tokens. By doing so, we ensure that the fused tokens have the same semantic representation, and thus alleviate the impact of inaccurate depth prediction.</p>
<img src="https://github.com/clorislili/imagemanip/blob/main/images/correspondence.png" alt="GitHub Logo" width="700" height="250">


## 3. More ablation study on the view selection module

### Number of candidates: 
Our investigation into the impact of candidates quantity on the module involved dividing the potential space into 4/9/16 candidate regions based on predefined 3D space with distance (2.5 units to 4.5 units) and azimuth angle ranges. 
On 10 seen categories under pushing primitives, 4/9/16 candidates yield average accuracies of 0.72/0.73/0.73. 
It becomes apparent that a greater number of candidate regions did not result in significant performance improvement, as neighboring views demonstrate minimal variation across the entire potential space. 
The growth in candidates didn't lead to a corresponding increasement in information brought by different views.

### Candidate scope: 
<p>We analysis the impact of the range of whole potential scope by expanding the predefined distance range to (1.0 units to 5.0 units) and azimuth angle range to (40 degrees) while subdividing the potential space into nine candidate regions to place camera.
Comparing to the scope we decribed in the main paper, this experiment reveals a slight performance decrease, from 0.73 to 0.71. 
Since enlarging the predefined space will widen the range for each candidate space, it potentially introduces more ambiguity when positioning the camera in the broader candidate area. 
Meanwhile, we adopt random next view selection here, which achieves more performance drop to 0.5. As shown in the following figure, since in more broad 3D space, the views show great difference. Therefore, randomly placing can not ensure capturing valuable view for manipulation prediction .
This shows the important of our best next view selection strategy, especially in large scope.
Meanwhile, when we reduce the potential space (2.5 units and 10 degrees) and generate the nine candidate regions, the performance dropped to 0.66. 
This suggests that a smaller potential scope might not encompass sufficiently informative views to complement the global perspective since views are too similar, and the optimal view can easily lied out of the scope. 
In the following figure, we provide a visualization of next views captured beyond the specified range: (a) and (b) exceed the allowed distance, while (c)-(f) have
azimuth or altitude angles outside of the valid range. These images demonstrate the limited valuable information they provide for the previous global view. By setting the space range for capturing the
next view based on experimental experience and observation, we ensure that the subsequent views
contribute essential information, enhancing the learning process and enabling a more comprehensive understanding of the object and its articulated parts.</p>
<img src="https://github.com/clorislili/imagemanip/blob/main/images/large_scope.png" alt="GitHub Logo" width="700" height="150">

### Upper bound: 
Given the case of 9 camera pose candidates, we establish an upper bound for the view selection module. 
We place the camera in each candidate region, generating refined affordance and manipulating the object. 
We define a successful manipulation if it achieves success once among the nine trials. 
In this scenario, we reach an accuracy of 0.74, which can be considered as the upper limit. 
Also, in section IV.C 'with random next view', we provide the lower limit of this module by randomly place the camera among the nine candiates to capture the next view, which achieves 0.70 accuracy. 
By comparing with the upper and lower bound, our view selection module shows its effectiveness in selecting informative views by yielding an accuracy of 0.73.

### Visulization of view selection module:
<p>We show the improvement of refined affordance prediction compared to the initial affordance prediction. By incorporating the valuable visual information from the selected next view, the refined affordance maps exhibit improved precision and clarity, particularly in the boundary
regions. Compared to the initial affordance map, the refined affordance map provides a more accurate
representation of the object’s affordance.</p>
<img src="https://github.com/clorislili/imagemanip/blob/main/images/next_view.png" alt="GitHub Logo" width="700" height="350">
<p>We further demonstrate the refined affordance prediction given nine candidates. Different candidates generate different refined affordance prediction, showing the necessarity of applying view selection module. We observe that different next views capture distinct object details, leading to variations in the refined manipulation
maps after fusion. This observation further verifies the significance of the view selection module in
our approach.</p>
<img src="https://github.com/clorislili/imagemanip/blob/main/images/view_selection.png" alt="GitHub Logo" width="700" height="250">


## 4.Domain randomization:
The randomization in object material and lighting is shown in the following. By doing so, we aim to easy the process of sim to real transfer since real-world usually contains diverse scenatios.
<img src="https://github.com/clorislili/imagemanip/blob/main/images/material.png" alt="GitHub Logo" width="700" height="180">





