
# Projects

## [Binary Clock][Binary Clock Link]

The Binary Clock project started when I wanted a simple clock that displayed the
time in binary coded decimal. After looking online and finding none that looked
good, I made my own.

![alt text][Binary Clock picture]

More information, documentation, and a high level overview can be found
[here][Binary Clock Link].


## [Harma][Harma Link]

The Harma (meaning Mimic in Swedish) project is a solution to my shaky, over caffeinated hands.
It is a robot-assisted soldering tool, much like [robot-assisted surgery][Robot Assisted Surgery],
but much less expensive (hopefully).

The idea is to have two distinct sub systems working together: One or two [Pensels][Pensel Link] to
detect orientation and movement of the users hands and an accompanying one or two robotic
arms (cool Swedish name to be determined) mimicking the user's input as well as performing
special actions on a button press, such as feeding solder or wire.

More info about the project can be found [here][Harma Link].


## [Pensel][Pensel Link]

The Pensel (meaning brush or pencil in Swedish) project is the sub-component of the Harma
project that gets the user's input. The user holds the Pensel like it was the soldering
iron and the robotic arm mimics their movement on a finer scale, as well as filtering
out jitter.

![alt text][Pensel Top]

The above is my first cut at the PCB. So far all sensors are working and I am getting
accelerometer and magnetometer data out of the orientation IC. This is currently the main
part I am working on for the overall Harma project. More info can be found [here][Pensel Link].


## [Ladder 42][Ladder 42 Link]

![alt text][Ladder 42 complete]

Ladder 42 (AKA candleBot) was a project for my Microprocessors II lab by myself
and [Broderick Carlin][Broderick Link]. The project is based on the
[Trinity College Firefighting Robot Competition][trinity robot link].
The goal is to have the robot find the fire (a candle) and extinguish it as fast as possible.

We went about this by getting a [Pixy][pixy link] to do image processing,
two old Wiimotes to sense IR, two compass MEMS ICs, a color sensor to go on the bottom to detect the
white circle that is under the candle, and a cell module to text the "fire department" to put out the candle.
A bit overboard, but we wanted to go all out on this project. We designed
all of the PCBs ourselves and got them fabricated by [Dirty PCB][diry PCB link].

![alt text][Ladder 42 block diagram]

The compasses were dead on arrival because we selected too small of packages and did the reflow
ourselves. The wiimotes were very easy to interface with (there are many guides online to do this) so
detecting the candle's position was easy. However, the image processing we needed (edge detection) was
not supported out of the box by the pixy. One of my main parts of the project was to try to
get edge detection working on the pixy camera.

![alt text][Ladder 42 Edge Detection]

Stark corners were easy, but getting rid of spurious noise and repairing torn edges was very
difficult. The Pixy also had a fish eye lens on it, distorting straight lines. Edge detection
was working for the most part, but I failed to get a communication scheme with the main
MCU finalized before the competition. This project was for a semester long course, so we
just ran out of time. I also was responsible for the code interfacing with the color sensor, the I2C
driver, and part of the wiimote code.


## Senior Design

![alt text][Senior Design Assembled]

My Senior Design project was an [EHF][EHF link] 60 GHz radar sensor for detecting distance.
The basic idea is that the radio chip, a custom ASIC, would output a ramp in frequency from
60 to 67 GHz over a few milliseconds, hits the target object, and comes back. By the time
the radar wave returns, it is slightly slower in frequency than what is currently being outputted.
The ASIC then subtracts these two signals in the frequency domain and outputs the result, now in
the kHz range, to be used by the application processor.

![alt text][Senior Design Signal Final]

We used an Altera FPGA to do the DSP. I was responsible for the DSP (written in Verilog) to
detect the distance of objects, which was proportional to the output signal from the radar ASIC.
I also wrote a UART driver. We were mostly successful. The fundamental frequency seen in the above plot is
correlated to the distance of the object, but the large regular spikes were due to an error somewhere
in the signal path that we could not identify.

![alt text][Senior Design UART]


## Ice Dancer

The Ice Dancer was a project in collaboration with Dr. Thomas Shepard and
Dr. Thomas Rodengen to measure ice thickness formation during the winter on
Minnesota lakes.

![alt text][Ice Dancer PCB pic]

The Ice Dancer works by freezing a PVC pipe into the ice with a stopper on the bottom
and a metal ring around the outside. The Ice Dancer then lowers a magnet down to the bottom
on a string, attaches to the metal ring, and pulls it up. The Ice Dancer measures the distance
via an encoder on the motor and determines if it is pulling the metal ring by measuring the
amount of current the motor is drawing.

![alt text][Ice Dancer Test pic]

Everything for this project worked, except for the SD card reader. I unfortunately
had to end the project there without resolving this as Senior Design was taking up
too much of my time.


## [PiBot][PiBot Project Link]

The PiBot project is a collaboration between myself and [Broderick Carlin][Broderick Link].
The goal of the PiBot project is to enable the maker community with an easy to use, but
powerful robot platform. It does this by off-loading the motor driver logic as well as the
distance and velocity calculation to our co-processor, allowing the users processor to handle
more important tasks.

This project uses the NXP MKL03Z32VFK4, a M0+ processor. I wrote the firmware while
Broderick is responsible for the board design. The initial firmware is complete, but
the board design is still in progress. More information as well as the firmware, unit
tests, and board files for this project can be found [here][PiBot Project Link] on the GitHub page.

![alt text][PiBot Current Board Layout]


[Broderick Link]: https://www.linkedin.com/in/broderick-carlin-90707879/
[trinity robot link]: http://www.trinityrobotcontest.org/
[pixy link]: http://charmedlabs.com/default/pixy-cmucam5/
[dirty PCB link]: http://dirtypcbs.com/store/pcbs
[EHF link]: https://en.wikipedia.org/wiki/Extremely_high_frequency


[Binary Clock picture]: http://raw.githubusercontent.com/TDHolmes/BinaryClock/master/documents/pictures/BinaryClock_rev1.JPG "Binary Clock v1 displaying 20:31:08 (8:31 PM)"
[Binary Clock Link]: http://www.holmesengineering.com/BinaryClock "Binary Clock Project Page"


[Harma Link]: http://www.holmesengineering.com/Harma "Harma Project Page"
[Robot Assisted Surgery]: http://en.wikipedia.org/wiki/Robot-assisted_surgery


[Pensel Link]: http://www.holmesengineering.com/Harma/Pensel "Pensel Project Page"
[Pensel Bottom]: https://raw.githubusercontent.com/TDHolmes/Harma/master/Pensel/documentation/pictures/Pensel_1_0_bottom.jpg "The bottom of the 1.0 Pensel PCB"
[Pensel Top]: https://raw.githubusercontent.com/TDHolmes/Harma/master/Pensel/documentation/pictures/Pensel_1_0_top.jpg "The top of the 1.0 Pensel PCB"

[Ladder 42 Link]: https://github.com/beeedy/candleBot "Ladder 42 Project Page"
[Ladder 42 complete]: https://github.com/beeedy/candleBot/blob/master/Images/Pics%20of%20finished%20bot/IMG_0164.png?raw=true "Final design"
[Ladder 42 block diagram]: https://raw.githubusercontent.com/beeedy/candleBot/master/Images/Communication%20Lines.png "Ladder 42 Block Diagram"
[Ladder 42 Edge Detection]: https://raw.githubusercontent.com/beeedy/candleBot/master/Images/PixyEdgeDetectProofOfConcept.png "Edge Detection of a coffee cup, stapler, and box"


[Senior Design UART]: https://raw.githubusercontent.com/TDHolmes/tdholmes.github.io/master/_pictures/seniordesign_UART.jpg "UART driver bringup"
[Senior Design Assembled]: https://raw.githubusercontent.com/TDHolmes/tdholmes.github.io/master/_pictures/seniordesign_finaldesign.jpg "Final design with Altera dev-board for signal processing"
[Senior Design Signal Final]: https://raw.githubusercontent.com/TDHolmes/tdholmes.github.io/master/_pictures/seniordesign_final_output_crop.jpg "Signal Output with unknown noise source"


[Ice Dancer PCB pic]: https://raw.githubusercontent.com/TDHolmes/tdholmes.github.io/master/_pictures/icedancer_PCB.jpg "Ice Dancer Arduino shield"
[Ice Dancer Test pic]: https://raw.githubusercontent.com/TDHolmes/tdholmes.github.io/master/_pictures/icedancer_test_cropped.jpg "A test of the Ice Dancer prototype"


[PiBot Project Link]: https://github.com/TDHolmes/PiBot "PiBot Project Page"
[PiBot Current Board Layout]: https://raw.githubusercontent.com/TDHolmes/PiBot/master/documentation/pictures/PiBot_layout_proto.png "Current board layout"
