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
Research Paper at arXiv
</a>
<br>
<br>
### Results:
<p align='left'>
<img src="images/modelA.gif?raw=true" width="220" height="150"/>
<img src="images/modelC.gif?raw=true" width="220" height="150"/>
</p>
<br>
### My role in the project:
- sfsfs
- sdsffsf
- sdffs
- sfd
<br>
<br>
<br>
### Brief Project description:
<br>
<br>
Collaborative research project between Volvo Cars, and student teams from UC Berkeley and Chalmers University.
<br>
<br>
The research project was aimed at predicting the intention of a pedestrian to cross or not cross the road. This project was a successful attempt to emulate the behaviour of a human driver to guess the intention of fellow road users such as pedestrians. Our team based the approach on a research paper that had some progress in this line of work. After replicating the paper, our teams decided on experimenting additional approaches and eventually arrived at Fusion based Intention Prediction Networks.

First Model that we built was based on the research paper. This model consisted of 3 components: Object detector, object tracker and a classifier. The model predicted the intention of pedestrians to cross or not cross by indicating red/green bounding box around the pedestrians. As far as the ego vehicle is concerned, the intention of pedestrians in the immediate vicinity or in the path of the vehicles are of importance, whereas other pedestrians in the scene are not important (hence their bounding box colors should be green for most of the scene duration). The model's input is the live video feed from the front camera after which the object detector (YOLOv3) dissects the video into frames and tries to localize the objects of interest (pedestrian in our case) in each frame by plotting bounding boxes around them. After this stage, the detected pedestrians in the video are tracked with the help of object tracker (SORT) resulting in unique IDs for each pedestrian in the video. Finally the detected and tracked pedestrians from each frame are gathered as features for the 3D scence classifier (DenseNet). The classifier uses the information of each pedestrian in the video to predict their intention to cross, ultimately resulting in a green bounding box for non-crossing or red bounding box for crossing pedestrian. 

The challenge here is to predict the intention atleast 0.5 secs before the intended action occurs which from a safety perspective is required for the car to make any necessary decision. 

Our teams took this basic framework and experimented with alternate types for each component of the model such as SORT, DeepSORT, Pose-Estimation based detection and tracking. Similarly, alternate types for classifer such as Recurrent Neural Networks, Random Forest and DenseNets. Finally we tried feature engineering for the DenseNet classifier which initially used only the cropped pedestrian images as features. In this feature engineering we applied skeletons for the pedestrian using Pose-Estimator and retrained the classifier resulting in a improved AP score of 0.89 achieving more that the research paper that we started with. Thus using this new classifier and additional feature engineering we arrived at a better model for intent prediction that predicts 0.5 secs before the intended action occurs.

For clear schematics diagrams, codes, demos and the Research paper and explanations please checkout the different URLs at the top of the page.