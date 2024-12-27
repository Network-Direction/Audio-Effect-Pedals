# ProCo RAT

## Status

- [x] Schematic Drawn
- [x] Tested on breadboard
- [x] PCB designed
- [x] Gerbers created


</br></br>
## Links

https://electrosmash.com/proco-rat

http://beavisaudio.com/schematics/ProCo-Rat-II-Distortion-Schematic.htm


</br></br>
# Analysis

The RAT is made of four main stages:
* Power Supply
* Input/Clipping
* Tone Control
* Output


</br></br>
## Power Supply

The power supply is simple, providing both +9v and +4.5v. 9 volts to power the opamp and the transistor, and 4.5v to bias the input signal.

The diode is there for reverse polarity protection.

R1, C1, and C2 are used for filtering. C1 and C2 remove ripple, but combined with R1 they also create a low pass filter, to attenuate high frequency _impulse_ noise (sudden spikes).

R2 and R3 form a voltage divider, to create the 4.5v for biasing. C3 is there to remove any additional ripple that may be introduced.

![Power](https://github.com/user-attachments/assets/94d05e01-500b-42de-b422-06e3037da349)

</br></br>
## Input and Clipping


</br></br>
## Tone Control


</br></br>
## Output


