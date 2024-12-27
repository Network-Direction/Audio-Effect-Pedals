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

Many pedals have an input stage, to work with the low impedance input signal, and a clipping stage to produce distortion. The RAT combines both of these into a single stage.


</br></br>
### Input

The first part of the stage takes the input signal. R4 is in place as a pull down resistor, to remove any popping sounds when the stomp switch is pressed.

R5 provides a bias to the input signal, raising the midpoint of the wave from 0v to 4.5 volts. C4 makes sure this DC bias voltage does not flow back to the pickups.

R4 and R5 control the input impedance. Originally these were 1M each, which made the input impedance about 500K. This version has increased them to 2M, to make the input impedance about 1M, which is generally better to avoid tone sucking.

R6 is in place to protect the opamp from any unexpected current.

R6 together with C5 creates a low pass filter, which shunts frequencies over 159KHz to ground. This is a key part to the RAT architecture. It emphasises mids, and attenuates highs and lows.

![input](https://github.com/user-attachments/assets/e64370e4-5c70-4c6e-9117-7ed01fe9fdf2)


</br></br>
### Opamp

The opamp provides two functions in this stage. One is as an input buffer, where a high impedance input signal is converted to a low impedance output signal. This part is very similar to many other pedal's input stages.

The opamp also provides gain to the signal. boosting the signal affects how much clipping and distortion is applied to the signal later on.


</br></br>
> [!NOTE]
> The original pedal used an LM308 opamp. They are obsolete, so this version uses an OP07CP. OP07DP would also be suitable.


</br></br>
This opamp is used in a slightly different way than opamps in other pedals. While it is still a low-noise opamp like the TL071, it is very different in terms of _slew rate_.

As the input signal in continually changing (oscillating), the output of the opamp must also be continually changing. The speed at which it can react to these changes is called the _slew rate_. Normally, a fast slew rate is ideal, as the output of the opamp is a good representation of the input signal.

The OP07CP has a low slew rate of about 0.3V/us (about 40x lower than the TL071). It is special though, as the _compensation capacitor_ (C6) can control the slew rate (the smaller the cap, the faster the slew rate).

![op07cp](https://github.com/user-attachments/assets/8f4b9a64-64f0-43f2-827b-15304f9c27d2)


</br></br>
What this means is, the opamp cannot effectively reproduce high frequencies (>5.3KHz), as it can't oscilate the output signal fast enough. Once again, this is part of the RAT's tone, as it emphasises mid frequencies, and attenuates high and low frequencies.


</br></br>
### Filtering


</br></br>
### Clipping and Distortion


</br></br>
## Tone Control

The tone control is a simple passive low pass filter, controlled by the 100K potentiometer. R10 is there to make sure there is always a minimum of 1.5K ohms in the LPF, even if the pot is turned all the way down.

</br></br>
> [!NOTE]
> The original pedal used an Audio pot, not a linear pot, for tone control.

![tone](https://github.com/user-attachments/assets/977a08a6-9c78-46b9-a917-bac0431aa36e)

</br></br>
The minimum cutoff frequency is 475Hz, and the maximum is 32KHz.

This, along with other filtering in the circuit, creates a mid-boost.

</br></br>
> [!NOTE]
> The clipping stage has a double RC network, which attenuates harmonics below 1.5KHz


</br></br>
## Output


