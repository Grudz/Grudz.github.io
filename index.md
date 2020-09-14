---
layout: default
---

# About Me

My fondest experiences at Oakland University are the people I met and got to work with. I got to enjoy playing my favorite sport, hockey, with a great group of guys. My freshman year especially, I was out of my comfort zone playing with teammates two to four years older than me. That was a fantastic learning experience on communication and teamwork, and not to mention really fun. I also found comradery joining the Autonomous Vehicle Club. That club has a fantastic amount of diversity of thought, and it is a pleasure picking everyones brains. Another amazing thing about the club is the immense knowledge of my teammates. They are incredibly smart and an absolute pleasure to work with and learn from. In my free time, I find myself tinkering around with ROS, studying artificial intelligence, working on personal engineering projects, and playing hockey.

---

This webpage has 4 sections:

**Autonomous Vehicle Systems, Autonomous Vehicle Club, Machine Learning, Embedded Software**

##### Contact Infomation:
**LinkedIn:** <a href="https://www.linkedin.com/in/bengrudzien/">linkedin.com/in/bengrudzien</a>

**Email:**
 bgrudzien@oakland.edu
 
---

### Autonomous Vehicle Systems

IGVC Course Challenge

![](igvc_course.gif)

GPS waypoint project

![](audi_bot_gps_sim.gif)



---

### Autonomous Vehicle Club

Point Cloud data

![](point_cloud.gif)

Voltage divider for accel signal

![](scope_vdivider.jpg)

Relay board soldering

![](relay_board.jpg)

---

### Machine Learning

I think sign language one

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

course 4 maybe 

~~~python
lr_schedule = tf.keras.callbacks.LearningRateScheduler(
    lambda epoch: 1e-8 * 10**(epoch / 20))
~~~

~~~python
history = model.fit(train_set, epochs=100, callbacks=[lr_schedule])
~~~

course 1

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

### Embedded Software

breadboard test

![](6502_breadboard.jpg)

gif

![](6502_vid.gif)

---

