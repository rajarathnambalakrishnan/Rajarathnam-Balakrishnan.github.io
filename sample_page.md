## Neural Networks for modelling and guidance of UAVs (Unmanned Aerial Vehicles) in urban environments

<p align='center'>
    <img src="images/bt.gif?raw=true" width="450" height="275"/>
</p>
<a href="/pdf/Tesi.pdf" download>Click here to download my Bachelor thesis</a>
<br><br>
**Project description:** 
<br>
The utilization of robots that can displace autonomously in a given environment have continuously increased in the past years. Potential applications are several and range from delivery vehicles, to robots assistants for elderly people, autonomous cars, surveillance drones, robots removing bombs in military areas, and planet exploration robots.
<br><br>
Privates as Tesla, Uber, Google, or Amazon are investing millions of dollars trying to de-
velop safe, reliable and effective technologies which can help them offer better services at
lower prices. One of the main complications and actual goals is represented by cities, where
fixed and moving obstacles are abundant and risk of crashing against one of them is high,
and would lead to legal problems.
<br><br>
Both for university research and industries, one of the most interesting type of au-
tonomous robot is represented by the Unmanned Aerial Vehicles (UAVs). UAVs are reusable
aircrafts designed to operate without an onboard pilot. They do not carry passengers and
can be either remotely piloted or preprogrammed to fly autonomously. 
Autonomous flight is a major target goal for all technologists. The ability to take-off, execute a given mission
with high maneuverability and return to its base without human intervention, promises to
enhance UAV deployment in many application domains.
<br><br>
In order to accomplish these tasks, the UAV must have perception of the surrounding
environment, know with precision its position, have a path to follow from a start to an end
point, and a control system. Each of these blocks is a vast research field, so we decided to
concentrate this work on path planning.
<br><br>
When defining a mission, path planning is the crucial element of the entire system. More
precisely, path planning involves the determination of a collision-free global route between
a start point A to an end point B, optimizing a performance parameter, such as distance,
time, or power. Depending on the kind of information possessed, we can have on-line and
offline path planning. Offline path planning requires complete information about static
and dynamic objects in the studied environment: this is known as global path planning.
When we do not possess complete information about the surrounding environment, so we
do not know the position or velocity of obstacles, the vehicle gets data through sensors and
cameras. This approach is called on-line path planning, or local path planning. Usually,
robots start their path offline and switch to on-line when a change in scenario is detected.

**Implementation and results:**
<br>
For this work, an offline bio-inspired path planning approach has been used. In particular,
a cell decomposition approach is used together with deep reinforcement learning techniques. The models have been implemented using the TensorFlow framework. More details about the implementation can be found on my <a href="/pdf/Tesi.pdf" download>bachelor thesis document.</a> 
<br>
The figure below shows the user interface we created for this project. Here are shown the computed path between two chosen points A and B, altitudes graph, and the drone's battery percentage. Finally, in the bottom right corner are shown some path's features: time, total space (every cell correspond to 5 meters), number of cells and maximum altitude. The text below alerts the user with
some important messages, for example, when the chosen points are not valid or a power recharge is necessary.
<br><br>
<img src="images/python8.JPG?raw=true"/>
<br><br>



