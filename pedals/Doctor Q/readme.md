# Doctor Q

Original **Doctor Q** was by Electro Harmonix from the 1970's. The schematics here incorporate the **Doctor Quack** mods from **Jack Orman**.

Another popular modification is called the **Nurse Quacky**


</br></br>
# How it Works
There are several main modules to the pedal:
1. Power
2. Input Buffer
3. Envelope Follower
4. Tone Selection
5. Voltage Controlled Filter (Wah Effect)


</br></br>
## Power

The power module provides an output of 9v and 4.5v.

![image](https://github.com/user-attachments/assets/c46336f1-20e1-42ce-9300-556c898eba60)

Interestingly, the 4.5v output is filtered with a 10uF capacitor, while the 9v output is not filtered.

The dual op amp package has a 9v power supply, with a 47-ohm resistor. This is a current-limiting resistor which provides minimal protection for the IC.


</br></br>
## Input Buffer

This is an addition to the original schematic. This is required to match impedance with the guitar, and preserve the original tone.

This is very common type of input buffer that biases the input to 4.5v, and provides capacitors to remove the DC offset.

![image](https://github.com/user-attachments/assets/d12a7a99-4f2f-41d2-a726-7456c95b488f)

The signal has two paths after the input buffer:
* The envelope follower
* The filter/wah effect



</br></br>
## Envelope Follower
### Overview

The purpose of the envelope follower, at least in this circuit, is to create a _Control Voltage_.

The [_envelope_ ](https://github.com/Network-Direction/Audio-Effect-Pedals/blob/main/Audio%20Theory/4.%20Envelope.md) is, simply put, the level of a sound over time. Imagine it as a graph that describes the amplitude of a wave.

The _envelope follower_ is the module that looks at the amplitude of the wave, and creates a voltage to describe it's level. If the amplitude goes up (the sound gets louder), then the envelope follower generates a larger voltage. If the amplitude goes down, then the output voltage goes down too.

This output voltage is called the _control voltage_, or _CV_. This is used to control some other aspect of the circuit as a whole.


</br></br>
# Tone Selection

The pedal is designed to work with electric guitars or bass guitars. A DPDT switch toggles between NORM or BASS mode.

**NORM** mode sends the signal down a path that emphasises mid to mid-high frequencies. **BASS** modesends the signal down a path that emphases higher frequencies.

This works by causing the signal to flow through difference RC networks. This is similar in concept to a tone control on any other pedal, except there are two fixed settings, rather than one or more potentiometers to create continuously variable frequencies.


</br></br>
## Wah Effect


</br></br>
# Links

Doctor Quack Resources - https://generalguitargadgets.com/effects-projects/filters-envelope/dr-quack-ehx-doctor-q/

Doctor Q Schematic - https://www.muzique.com/schem/doctor-q.gif

Doctor Quack Schematic - https://www.muzique.com/schem/doctor-q.gif

Nurse Quacky - https://home-wrecker.com/nurse-quacky.html

