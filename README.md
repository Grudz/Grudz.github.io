---
layout: default
---

# About Me

test

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

![gif](/assets/images/giphy.gif)

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```

**The Guts**: links to a file that is key to the functionality of the project.

**The Repo**: links to the GitHub repository.

---

### Intelligent Ground Vehicle Competition

![image](/assets/images/gem.jpg)


#### LiDAR

In my first year as a member of the Smart Vehicle Club, I took on the role of the team leader for Perception. I wrote a C++ ROS node which reads the LiDAR data points from a Cepton LiDAR and creates an occupancy grid surrounding the vehicle. We fuse this information with object detections from a custom trained YOLOv3 object detection model to both detect and localize objects around the vehicle.

![image](/assets/images/lidar_on_roof.jpg)

<p align="center">
  <img src="/assets/images/lidar_road.gif">
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/blob/master/perception/src/PointMap.cpp">The Guts</a>
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/">The Repo</a>
<br>
</p>

Below is a visualization I created utilizing the Waymo Open Dataset and Open3D

<p align="center">
  <img src="/assets/images/waymo_lidar.gif">
<br>
  <a href="https://github.com/John-Brooks/WaymoOpenDatasetLiDARViz/">The Repo</a>
<br>
</p>

---

#### Vision

When I joined the team I started by updating our vision system to use a modern CNN + Object Detector. At the time YOLOv3 had the best real time performance. We had no dataset so we used transfer learning from the YOLO model pretrained on the VOC dataset and retrained it on images that we hand labeled from Google Images. The end result was a detection network that functioned "Good enough". There were however some class imbalance issues that caused the network to misclassify the directionality of one way signs.

![image](/assets/images/labeling.png)

<p align="center">
  <img src="/assets/images/LiDAR.gif">
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/blob/master/yolo/src/YOLO.cpp">The Guts</a>
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/tree/master/yolo">The Repo</a>
<br>
</p>

---

#### RADAR

The platform had 360 degree RADAR coverage provided by six Continental ARS430 RADARs. The IGVC competition does not require tracking of any moving objects and we found the RADARs to be too noisy for ranging static objects. This was only possible though by developing a RADAR visualization tool. I wrote a visualizer in Python using PyGame. It allowed us to assign various RADAR parameters like RCS and relative velocities to RGB color channels which was useful in attempting to filter out false positive datapoints.

<p align="center">
  <img src="/assets/images/RADAR.gif">
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/blob/add-RADAR/radar/visualize/main.py">The Guts</a>
<br>
  <a href="https://github.com/oaklandsmartvehicles/ou_self_drive_ros/tree/add-RADAR/radar/visualize">The Repo</a>
<br>
</p>

---

#### Electromechanical Design

After the 2019 competition year it was clear that our platform had a problem. Electrically it was a hacked together mess of Arduinos and circuits held together with hopes, dreams, and in some cases duct tape. At one point a USB hub literally caught fire. The most glaring issue though was that the steering was so slow the car could not navigate the timed course as fast as our competitors. So in my time as President of the club, in preparation for the 2020 competition year, we completely overhauled the electrical system, installed a new more powerful steering motor, and wrote microcontroller firmware to control these systems over an Ethernet connection from the host computer.

<p align="center">
  <img src="/assets/images/circuit.png">
<br>
  <img src="/assets/images/drive_by_wire_test.gif">
<br>  
  <a href="https://www.youtube.com/watch?v=7-SMA4yzBNs">YouTube: First System Test</a>
<br>
  <a href="https://github.com/oaklandsmartvehicles/DriveByWireECU/blob/master/DriveByWireECU/DriveByWireIO.c">The Guts</a>
<br>
  <a href="https://github.com/oaklandsmartvehicles/DriveByWireECU/tree/master/DriveByWireECU">The Repo</a>
<br>
</p>


---

### Personal Projects

#### Drowsy Driver Detection

At the Grizzhacks 2 competition our team won first place overall and best mobile hack. I wrote the algorithm for detecting the driver's blink rate using a Haar Cascades in OpenCV and tracking the deviation of brightness of the detected eyes. Peaks in brightness detected by a spike in the standard deviation of overall greyscale values triggered a detected blink.

<p align="center">
  <img src="/assets/images/daydream.jpg">
<br>
  <a href="https://devpost.com/software/daydream-detector-aka-anti-sleep-5000">DevPost</a>
</p>

---

#### Reinforcement Learning

I find reinforcement learning to be very interesting. Under a robotics professor at Oakland University I performed a self guided study of reinforcement learning which included solving a classic Gridworld problem, CartPole, and LunarLander (discrete). The solved Lunar Lander was done using a DQN model implemented with Keras (Tensorflow backend).

<p align="center">
  <img src="/assets/images/lunar_lander.gif">
<br>
  <a href="https://github.com/John-Brooks/ReinforcementLearning/blob/master/LunarLander/tfmodel.py">The Guts</a>
<br>
  <a href="https://github.com/John-Brooks/ReinforcementLearning/tree/master/LunarLander">The Repo</a>
<br>
</p>

---

I also created my own reinforcement learning environment for a parking lot simulation. This simulation is cross platform. It generates C++ Python bindings using SWIG so that you can interface with the simulation using the same API as the Open AI gym. The 2D courses can be designed using a vector graphics program as they are loaded using a standard .svg file. The agent that I trained on this simulator is the tf.agents DDPG agent, but it's uhhh... still "learning".

<p align="center">
  <img src="/assets/images/scared_car.gif">
<br>
  <a href="https://github.com/John-Brooks/IGVC-Gem-Simulator/blob/master/src/Vehicle.cpp">The Guts</a>
<br>
  <a href="https://github.com/John-Brooks/IGVC-Gem-Simulator">The Repo</a>
<br>
</p>

 