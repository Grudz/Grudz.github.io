---
layout: default
---

# About Me

My fondest experiences at Oakland University are the people I met and got to work with. I got to enjoy playing my favorite sport, hockey, with a great group of guys. My freshman year especially, I was out of my comfort zone playing with teammates two to four years older than me. That was a fantastic learning experience on communication and teamwork, and not to mention really fun. I also found comradery joining the Autonomous Vehicle Club. That club has a fantastic amount of diversity of thought, and it is a pleasure picking everyones brains. Another amazing thing about the club is the immense knowledge of my teammates. They are incredibly smart and an absolute pleasure to work with and learn from. Plus, after a year in the club, I got promoted to Vice President! In my free time, I find myself tinkering around with ROS, studying artificial intelligence, working on personal engineering projects, and playing hockey.

---

This webpage has 4 sections:

**Autonomous Vehicle Systems, Autonomous Vehicle Club, Embedded Software, Machine Learning**

##### Social Media and Contact:
**LinkedIn:** <a href="https://www.linkedin.com/in/bengrudzien/">linkedin.com/in/bengrudzien</a>

**GitHub:** <a href="https://github.com/Grudz">github.com/Grudz</a>

**Email:**
 bgrudzien@oakland.edu
 
---

### Autonomous Vehicle Systems

This is called the "IGVC Course Challenge". My teamate and I Implemented the ROS Nav-Stack in C++ with SLAM and Dijkstra’s algorithm to navigate a robot autonomously through a course. In this case, the global costmap for the lanes is pre-generated and the local costmap generates in real-time to avoid course obstacles. Navigation goals were set in C++ which gave the robot a goal location.

![](igvc_course.gif)


Take a look at the "GPS waypoint Project". I programmed an algorithm in C++ to drive a car through 8 GPS waypoints in under 45 seconds. The algorithm utilizes the GPS coordinates of the waypoint, a reference GPS coordinate, and the heading of angle of the Audi R8 relative to the next waypoint for localization and navigation.

![](audi_bot_gps_sim_2.gif)



---

### Autonomous Vehicle Club

We had an event where high school students and their parents came to hear about our club. For this, we had point cloud information from the cars LiDAR on display in real-time.

![](point_cloud.gif)


This is a picutre of a teammate and I testing a voltage divider on an acceleration signal coming from the motor using an oscilloscope.

![](scope_vdivider.jpg)


I hand soldered DV9 cables and our cars relay board based on a schematic we generated. This was crucial to get our drive by wire system completed.

![](relay_board.jpg)

---

### Embedded Software

Based on YouTube tutorials done by Ben Eater, I built a 6502 based computer. There were two tutorials, one for a custom clock module using 555 timers, and another for the 6502 computer. I combined those both on to one breadboard.

![](6502_breadboard.jpg)

Another part of Ben Eater's tutorial was assembly programing. He taught me how to program the 6502 microcontroller and display text to a LCD display. I expaneded on his tutorial, in which he only worked on a breadboard, and converted it to a PCB. (Plus it was way easier to program the ROM this way, because I didn't have to worry about accidently pulling any wires out on the breadboard)

![](6502_vid.gif)

---

### Machine Learning

This summer I completed four TensorFlow courses on Coursea and earned the Deeplearning.AI TensorFlow Developer Specialization. The courses I completed were "Introduction to TensorFlow for Artificial Intelligence, Machine Learning, and Deep Learning", "Convolutional Neural Networks in TensorFlow", "Natural Language Processing in TensorFlow", and "Sequences, Time Series and Prediction". 

![](tf_cert.png)
<a href="https://coursera.org/share/6afb226e61e1776eb9c04fb6f5fe602b">Certificate Validation Link</a>


This is a multilass deep neural network I made to recoginze sign lanugae images for each letter of the alphabet. This is a sequential neural network (NN) meaning the layers appear in the order that they are declared. This NN has two convolutional layers. The first convolution has 64 image filters and an input shape of 28x28 pixels in grayscale. The pooling layer basically simplifies the convolution layer's output and keeps the most impactful pixels. The activation function 'relu' stands for rectified linear unit, all this really does is ignore negative values that appear. Convolutions are in a matrix like data structure, so the flatten layer converts that into a vector to feed into the dense layers neurons. The dropout layer lets the NN ignore neurons if it thinks that they are too bias. Finally, the 'softmax' activation function is used at the output layer because this is multiclass NN. If the output desired was a yes or no answer, I would have used a 'sigmoid' activation function.

~~~python
model = tf.keras.models.Sequential([
    tf.keras.layers.Conv2D(64, (3,3), activation='relu', input_shape=(28, 28, 1)), # first convolution
    tf.keras.layers.MaxPooling2D(2, 2),
    tf.keras.layers.Conv2D(128, (3,3), activation='relu'), # second convolution
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dropout(0.2), # Add dropout
    tf.keras.layers.Dense(512, activation='relu'), # 512 neurons
    tf.keras.layers.Dense(25, activation='softmax') # Multiclass set up   
])
~~~


This is an interesting use of callbacks. This function changes the learning rate per every epoch. Then after the model is trained at a bunch of different learning rates, I graphed the epochs vs the learning rate and discovered the optimal learning rate for my model's optimizer.

~~~python
lr_schedule = tf.keras.callbacks.LearningRateScheduler(
    lambda epoch: 1e-8 * 10**(epoch / 20))
~~~

~~~python
history = model.fit(train_set, epochs=100, callbacks=[lr_schedule])
~~~


This is an example of another helpful callback. This code stoped training my model once the desired accuracy was reached. For example, even if the model is at epoch 10 out of 30, if the desired accuracy has been reached, the model will stop getting trained.

~~~python
    class myCallback(tf.keras.callbacks.Callback):
        def on_epoch_end(self, epoch, logs={}):
            if (logs.get('acc') >= 0.99):
                print("\nReached 99% accuracy so cancelling training!")
                self.model.stop_training=True

    callbacks = myCallback()
~~~

~~~python
    history = model.fit(x_train, y_train, epochs=10, 
                        callbacks=[callbacks])
~~~

---

