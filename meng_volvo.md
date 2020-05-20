## Pedestrian Intention Recognition

<p align='left'>
<img src="images/volvo.png?raw=true" width="120" height="80"/>
</p>
<a href='https://github.com/mjpramirez/Volvo-DataX' target = "_blank">
GitHub Repo | 
</a>
<a href='https://matthew29tang.github.io/pid-model/#/' target = "_blank">
Project Website | 
</a>
<a href='https://arxiv.org/abs/2005.07796' target = "_blank">
Research Paper
</a>
<br>
<br>
**Results:**
<p align='left'>
<img src="images/modelA.gif?raw=true" width="220" height="150"/>
<img src="images/modelC.gif?raw=true" width="220" height="150"/>
</p>
**Project description:** 
<br>
<br>
Collaborative research project between Volvo Cars, and student teams from UC Berkeley and Chalmers University.
<br>
<br>
The research project was aimed at predicting the intention of a pedestrian to cross or not cross the road. This project was a successful attempt to emulate the behaviour of a human driver to guess the intention of fellow road users such as pedestrians. Our team based the approach on a research paper that had some progress in this line of work. After replicating the paper, our teams decided on experimenting additional approaches and eventually arrived at Fusion based Intention Prediction Networks.

First Model that we built was based on the research paper. This model consisted of 3 components: Object detector, object tracker and a classifier. The model predicted the intention of pedestrians to cross or not cross by indicating red/green bounding box around the pedestrians. As far as the ego vehicle is concerned, the intention of pedestrians in the immediate vicinity or in the path of the vehicles are of importance, whereas other pedestrians in the scene are not important (hence their bounding box colors should be green for most of the scene duration). The model's input is the live video feed from the front camera after which the object detector (YOLOv3) dissects the video into frames and tries to localize the objects of interest (pedestrian in our case) in each frame by plotting a bounding boxes around them. After this stage, the detected pedestrians in the video are tracked with the help of object tracker (SORT) resulting in unique IDs for each pedestrian in the video. Finally the detected and tracked pedestrians from each frame are gathered as features for the 3D scence classifier (DenseNet). This classifier uses these information of each pedestrian in the video to predict their intention to cross ultimately resulting in a green bounding box for non-crossing or red bounding box for crossing pedestrian. 
