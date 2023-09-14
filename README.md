# The supplmentary for the paper

## 1.Real-world experiment
### Real-world demonstraion:
We provide more video demonstraion on the manipulation process in the link.
### Comparisons with point cloud:
To substantiate our findings, we offer additional qualitative evidence within a real-world setting. 
All experiment specifics align with the details in main paper, serving to illustrate the limitations of point clouds. 
As illustrated in [xxx], it becomes evident that point clouds exhibit notable limitations when confronted with specular or transparent objects (such as the pan and kettle). For example, owing to its intrinsic nature, the object (faucet) comprises sparse points, introducing complexities in both perception and manipulation.
Take the pan as an illustration – although the lid is transparent, the handle is not, and the transparent component still affects the overall image, intensifying the difficulties in perception and manipulation. 
In constract, cost-effective RGB imsgaes exhibit dense pixel-wise information to capture specular and transparent object.Therefore, our motivation is to provide a potential solution of RGB-only manipulation framework, which has its own strength in industrial applications.


## 2. More ablation study on the view selection module

### Number of candidates: 
Our investigation into the impact of candidates quantity on the module involved dividing the potential space into 4/9/16 candidate regions based on predefined 3D space with distance (2.5 units to 4.5 units) and azimuth angle ranges. 
On 10 seen categories under pushing primitives, 4/9/16 candidates yield average accuracies of 0.72/0.73/0.73. 
It becomes apparent that a greater number of candidate regions did not result in significant performance improvement, as neighboring views demonstrate minimal variation across the entire potential space. 
The growth in candidates didn't lead to a corresponding increasement in information brought by different views.

### Candidate scope: 
We analysis the impact of the range of whole potential scope by expanding the predefined distance range to (1.0 units to 5.0 units) and azimuth angle range to (40 degrees) while subdividing the potential space into nine candidate regions to place camera.
Comparing to smaller scope, this experiment reveals a slight performance decrease, from 0.73 to 0.71. 
Since enlarging the predefined space will widen the range for each candidate space, it potentially introduces more ambiguity when positioning the camera in the broader candidate area. 
Meanwhile, we adopt random next view selection here, which achieves more performance drop to 0.5. Since in more broad 3D space, randomly placing can not ensure capturing valuable view for manipulation prediction.
This shows the important of our best next view selection strategy.
Meanwhile, when we reduce the potential space (2.5 units and 10 degrees) and generate the nine candidate regions, the performance dropped to 0.66. 
This suggests that a smaller potential scope might not encompass sufficiently informative views to complement the global perspective. 
Thus, striking a balance in the candidate space's scope is crucial.

### Upper bound: 
Given the case of 9 camera pose candidates, we establish an upper bound for the view selection module. 
We place the camera in each candidate region, generating refined affordance and manipulating the object. 
We define a successful manipulation if it achieves success once among the nine trials. 
In this scenario, we reach an accuracy of 0.74, which can be considered as the upper limit. 
Also, in section IV.C 'with random next view', we provide the lower limit of this module by randomly place the camera among the nine candiates to capture the next view, which achieves 0.70 accuracy. 
By comparing with the upper and lower bound, our view selection module shows its effectiveness in selecting informative views by yielding an accuracy of 0.73.

### Visulization of view selection module:

## 3.Domain randomization:
The randomization in object material and lighting is shown in the following. By doing so, we aim to easy the process of sim to real transfer since real-world usually contains diverse scenatios.




