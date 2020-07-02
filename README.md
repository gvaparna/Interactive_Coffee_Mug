<h1>Motivation</h1>
<p>Coffee mugs are very common and prevalent in our daily life. We use them on a very regular basis, for example, home, office, leisure time, and chilling. One thought which crossed my mind was if we can have an interactive mug, that can be used for music control. For example, such a mug could measure the temperature of the liquid inside it and allow for micro gestures on it.</p>

<p>Interacting with computers while holding objects is a hot research topic in human-computer interaction. Micro gestures are defined as gestures that happen within 4 seconds. Recently “Sharma et al.” defined grasping micro gestures, which are a set of gestures that are performed on handheld objects. In this specific application, I aim to create an interactive mug that can support micro gestures.</p>

<p>The application is a music control app, that can detect swipes and taps for various actions. For example, swiping left can rewind a track, swiping right can fast forward a track, swiping up and down can increase and decrease the volume and double-tap can switch between the tracks. Simultaneously with high-resolution textile touch sensor, we can also detect how the person is holding the cup as in prior work.</p>

<h1>Project Concept</h1>
<p>The aim of the project is to develop an Interactive Coffee Mug. The Coffee mug can detect multiple pressure input based gestures which can then be used for various applications such as controlling a music player, gestural interaction for gaming, etc.  In addition, I wish to explore the capacitive sensing for creating interactions with the fluids in the mug. This can be achieved by using the method described in Touch.</p>

<h3>Pressure Input on the Surface of the Mug:</h3>

<p>Similar to how the authors have created various interactions in Touch, the liquid inside the mug could also be used as an interactive medium. By coupling the gestural interaction with textile-based gestural interaction on the surface of the cup, new interactions can be created. For example, by using the textile sensor on the surface of the mug, we can detect how the user is holding the cup. For example, if the user is holding the cup with its handle, then the sensor readings on the surface of the cup will be different. On the other hand, if the user is grasping the cup without using the handle, then the sensor reading on the surface of the cup will be different since there is more pressure applied on the surface of the cup, the interactive textile will show a different signature. This is similar to detecting the grasp signatures using a glove.</p>

<h3>Background:</h3>

<p>There are a number of research works that explored input through textiles. The most related projects are patch in which the authors created pressure-sensitive textile patches that can be worn on the body. Then there Is work on pressure-sensitive textiles for various interactions such as automotive interfaces, interactive furniture, and prosthetics. For capacitive sensing, the most relevant work which is related to this project it Touch in which swept-frequency capacitive sensing is used for detecting the number of gestures.</p>

<h1>Materials Used</h1>

1. SMD LEDs 
2. Lithium ION Battery
3. Needle (for sewing)
4. Conductive thread
5. Adafruit flora(Micro Controller) + BLE module 
6. Copper tape
7. Temperature sensor (TMP36)
8. Interactive textile cloth

<h1>Project Implementation</h1>
<p>For demonstration purposes, the fabric will be attached to the cup, and users can play with the music player and try out the various gestures. The gestures will be displayed on an external screen.</p>

<h3>Design Exploration</h3>

<h3>Testing and Identifying sensor placement:</h3>

<p>The initial step which has been considered for this task is to identify the ideal placement of the sensor. The sensor should be placed in such a way that it should not hinder the usual activity that we perform with the cup. For example, considering the pause and play button, Usually, this pause and play button should be quickly accessible, and at the same time, should not invoke false activation.</p>

<p>  If the sensor is placed on the handle, then it results in lots of false positives, because the hand is always in contact with the handle. On the other hand, if the sensor is placed on the rim, it solves the problem of false positives, but it is not easily accessible. One solution could be to place it on the rim near the handle. However, since we usable sip the beverages from the coffee mug, care should be taken to ensure that the sensor should not be touching our lips, when we are drinking. Hense after a few trails and testing, one location which is suitable is on the rim exactly above the handle. </p>

<h3>Design of a textile augmented cup:</h3>
<p>To check the feasibility of how I can create a textile augmented cup, I initially wrapped a cloth around my cup to give a look and feel of its looks and the ergonomics.</p>

<p>To implement touch sensing, "capsense" library has been used. It's an open-source library that allows for implementing touch sensing, on any conductive object. Since conductive textile was not available, a small piece of copper tape has been used as a touch sensor. After connecting to the circuit, as shown in the figure below, the "capsense" library was downloaded to the Arduino library. After setting up the capacitive sensing in the Arduino library. The WPF application reads the values through the serial port. We can also analyze the values for differentiating between "Touch" and "No Touch" from the  Arduino values.</p>

<h3>Technical Implementation:</h3>

<p> To implement the touch sensing, Arduino capsense library has been used. The circuit works by charging and discharging a capacitor. A capacitor is formed by two conductive elements. One is the conductive textile, which is the sensor and the second plate of the capacitor is formed by the human finger. So as the finger comes closer to the sensor, the capacitance increases, due to which the charging time of the capacitor increases, and hence this phenomenon can be used for detecting a touchdown event. As shown below, the sensor is connected to pin number 2, a 1 MΩ resistor is connected to pin 3. So, this forms a RC circuit.</p>
