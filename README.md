<h1>Interactive Coffee Mug For Music Control</h1>
<h2>Motivation</h2>
<p>Coffee mugs are very common and prevalent in our daily life. We use them on a very regular basis, for example, home, office, leisure time, and chilling. One thought which crossed my mind was if we can have an interactive mug, that can be used for music control. For example, such a mug could measure the temperature of the liquid inside it and allow for micro gestures on it.</p>

<p>Interacting with computers while holding objects is a hot research topic in human-computer interaction. Micro gestures are defined as gestures that happen within 4 seconds. Recently “Sharma et al.” defined grasping micro gestures, which are a set of gestures that are performed on handheld objects. In this specific application, I aim to create an interactive mug that can support micro gestures.</p>

<p>The application is a music control app, that can detect swipes and taps for various actions. For example, swiping left can rewind a track, swiping right can fast forward a track, swiping up and down can increase and decrease the volume and double-tap can switch between the tracks. Simultaneously with high-resolution textile touch sensor, we can also detect how the person is holding the cup as in prior work.</p>

<h2>Project Concept</h2>
<p>The aim of the project is to develop an Interactive Coffee Mug. The Coffee mug can detect multiple pressure input based gestures which can then be used for various applications such as controlling a music player, gestural interaction for gaming, etc.  In addition, I wish to explore the capacitive sensing for creating interactions with the fluids in the mug. This can be achieved by using the method described in Touch.</p>

<h3>Pressure Input on the Surface of the Mug:</h3>

<p>Similar to how the authors have created various interactions in Touch, the liquid inside the mug could also be used as an interactive medium. By coupling the gestural interaction with textile-based gestural interaction on the surface of the cup, new interactions can be created. For example, by using the textile sensor on the surface of the mug, we can detect how the user is holding the cup. For example, if the user is holding the cup with its handle, then the sensor readings on the surface of the cup will be different. On the other hand, if the user is grasping the cup without using the handle, then the sensor reading on the surface of the cup will be different since there is more pressure applied on the surface of the cup, the interactive textile will show a different signature. This is similar to detecting the grasp signatures using a glove.</p>

<h3>Background:</h3>

<p>There are a number of research works that explored input through textiles. The most related projects are patch in which the authors created pressure-sensitive textile patches that can be worn on the body. Then there Is work on pressure-sensitive textiles for various interactions such as automotive interfaces, interactive furniture, and prosthetics. For capacitive sensing, the most relevant work which is related to this project it Touch in which swept-frequency capacitive sensing is used for detecting the number of gestures.</p>

<h2>Materials Used</h2>

1. SMD LEDs 
2. Lithium ION Battery
3. Needle (for sewing)
4. Conductive thread
5. Adafruit flora(Micro Controller) + BLE module 
6. Copper tape
7. Temperature sensor (TMP36)
8. Interactive textile cloth

<h2>Project Implementation</h2>
<p>For demonstration purposes, the fabric will be attached to the cup, and users can play with the music player and try out the various gestures. The gestures will be displayed on an external screen.</p>

<h3>Design Exploration</h3>

<b>Testing and Identifying sensor placement:</b>

<p>The initial step which has been considered for this task is to identify the ideal placement of the sensor. The sensor should be placed in such a way that it should not hinder the usual activity that we perform with the cup. For example, considering the pause and play button, Usually, this pause and play button should be quickly accessible, and at the same time, should not invoke false activation.</p>

<p>  If the sensor is placed on the handle, then it results in lots of false positives, because the hand is always in contact with the handle. On the other hand, if the sensor is placed on the rim, it solves the problem of false positives, but it is not easily accessible. One solution could be to place it on the rim near the handle. However, since we usable sip the beverages from the coffee mug, care should be taken to ensure that the sensor should not be touching our lips, when we are drinking. Hense after a few trails and testing, one location which is suitable is on the rim exactly above the handle. </p>

<b>Design of a textile augmented cup:</b>
<p>To check the feasibility of how I can create a textile augmented cup, I initially wrapped a cloth around my cup to give a look and feel of its looks and the ergonomics.</p>

<p>To implement touch sensing, "capsense" library has been used. It's an open-source library that allows for implementing touch sensing, on any conductive object. Since conductive textile was not available, a small piece of copper tape has been used as a touch sensor. After connecting to the circuit, the "capsense" library was downloaded to the Arduino library. After setting up the capacitive sensing in the Arduino library. The WPF application reads the values through the serial port. We can also analyze the values for differentiating between "Touch" and "No Touch" from the  Arduino values.</p>

<b>Technical Implementation:</b>

<p> To implement the touch sensing, Arduino capsense library has been used. The circuit works by charging and discharging a capacitor. A capacitor is formed by two conductive elements. One is the conductive textile, which is the sensor and the second plate of the capacitor is formed by the human finger. So as the finger comes closer to the sensor, the capacitance increases, due to which the charging time of the capacitor increases, and hence this phenomenon can be used for detecting a touchdown event. The sensor is connected to pin number 2, a 1 MΩ resistor is connected to pin 3. So, this forms a RC circuit.</p>

<h2>Frabrication of Touch Matrix </h2>

<p>After previously implementing capacitive touch sensing using the capsense library, I realized that we need a higher resolution sensing for realizing continuous touch gestures such as swipes. After reading a few papers and tutorials, one of the most common ways to implement continuous touch gestures is through touch matrices. In a touch matrix, there are rows and columns of electrodes. The rows and columns are insulated by a non-conductive material. By using a commercially available touch controller, this matrix consisting of rows and columns can be easily connected to an Arduino.</p>

<h3> Preparing the touch sensor matrix:</h3>

<p>   For initial prototyping, the plan is to prepare a 3x3 matrix (3 rows and 3 columns). For this 6 strips of conductive fabric was cut. All the 6 strips are approximately equal in length and width. The columns were first attached to a ruled paper with a paper adhesive(Glue stick). The ruled paper was used to ensure that the spacing between the rows and columns can be kept consistent to a maximum possible extent. After affixing the columns, a layer of transparent scotch tape was affixed to insulate the rows from columns. Then, the 3 rows of textile strips were affixed on to the scotch tape. the resulting sensor can be sensing.</p>

<h3> Interfacing with the sensor</h3>

<p> To interface the touch matrix a more powerful touch sensing hardware is required, rather than the capsense library. For this, a commercial touch controller(MPR 121), has been used. This touch controller is a very popular touch controller and can detect touch events, for up to 12 electrodes. I2c protocol is used for communicating the touch events between the touch controller and the Arduino. For connecting the touch controller, the SCL pin of the controller is connected to the A5 pin of the Arduino. The SDA pin is connected to A4. The electrode lines from the touch matrix, are connected to the controller via copper tape and jumper wires.</p>

<h2> Lessons Learned </h2>

1. Always ensure that the sizes of the row and column strip should be approximately equal size. Otherwise, the sensor shape will be irregular.
2. Secondly, always insulate the rows and columns completely. Some times when the width of the scotch tape is smaller then there can be a few gapes between the row and the column layers and this can result in a short circuit.
3. Always leave some space at the edges of the strips so that they can be used to create connections with the Arduino. In the earlier attempt, I had covered the entire column layer with the scotch tape and hence was not able to connect the strips to the Arduino.
4. Usage od visual guides for aligning the rows and columns will be very helpful For example, in my case a ruled paper was used. 

<h3>Gesture Design and Recognition Pipeline</h3>

<p> There are four different gestures I intend to develop:
    1. Long Press
    2. Double Tap
    3. Left Swipe
    4. Right Swipe
The reasons for designing these gestures are: firstly, they are very common, intuitive and are used in daily smartphone based interactions. Hence not special training is needed for users. Secondly, they are also easier to perform when holding a cup. While testing various gestures, I found out that these were also the simpler ones implementation wise give the time-frame of the project.
For implementing these gestures, I have a done a literature review on how these gestures can be implemented using existing algorithms. Unlike smartphones , tablets and touchscreens, which provide SDKs for implementing Swipe and Tap gestures, there are no such existing SDKs for Arduino. The key challenge here is to identify and understand how to implement these gestures. I spent a considerable amount of time in studying researching and understanding how the touch algorithms work and how gesture recognizers can be built with capacitive sensing data.
</p>

<h4>Raw Signal Interpolation</h4>
<p>The key requirement for detecting continuous touch events is to have touch interpolation i.e. when the finger moves from one electrode to the other, the touch location should be interpolated for smooth and continuous localization of the finger.
For a 3x3 matrix, there are three rows and three columns which comprise of 6 different channels acting as inputs to the MPR121 touch controller. The MPR 121 touch controller returns the baseline value and filtered value for each channel.

Getting accurate coordinates using an interpolation algorithm: By using an interpolation algorithm, we can get the finger's x and y coordinates accurately. For the horizontal coordinates (y co-ordinate), since we use three electrodes (ELE0 – ELE2), the . The formula is: 
SumN = 1 × Dele(0) + 2 × Dele(1) + 3 × Dele(2) 
SumD = Dele(0) + Dele(1) + Dele(2)
Dele(n) (n = 0 to 2) represents the delta value (difference) of electrode-filtered data and its corresponding baseline value. After getting SumN and SumD, then: 
Coordinate = SumN ÷ SumD 
After getting the finger's horizontal coordinate,  the same interpolation method can be used to  to compute the vertical coordinate, using the other three electrodes (ELE3 – ELE5).</p>
