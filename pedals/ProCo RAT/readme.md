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

The opamp provides three functions in this stage. One is as an input buffer, where a high impedance input signal is converted to a low impedance output signal. This part is very similar to many other pedal's input stages.

The opamp also provides gain to the signal. boosting the signal affects how much clipping and distortion is applied to the signal later on.

Finally, the opamp is part of an active high pass filter, for attenuating higher frequencies.


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

There are several areas in this stage that add extra filtering. For starters, there is a 100pF capacitor across the 100K potentiometer. The pot controls the gain of the opamp, but placing a capacitor here creates a low pass filter. This attenuates some of the high end before clipping takes place.

When the potentiometer is at max, the filter will have the most effect, attenuating frequencies over 16KHz. This mellows out the distortion.

Setting the potentiometer at minimal levels sets the frequency cutoff at levels above human hearing, so effectively this filter only comes into play with lots of distortion.

![filters](https://github.com/user-attachments/assets/01fdcdd8-8262-4100-9921-a0ba7898b4bf)


</br></br>
There are also two RC networks in parallel, made of R8/C8 and R7/C9, connecting the inverting input to ground. This creates an _active high pass filter_.

The **R7/C9** filter attenuates frequencies below ~1.5KHz, at a rate of 20dB per decade.

The **R8/C8** filter attenuated frequencies below ~60Hz, at a rate of 40dB per decade, practically muting them.

The effect of this is to mute bass notes before they are clipped, creating a frequency dependant distortion (the low end is less clipped).


</br></br>
### Clipping and Distortion

There are two parts to distortion in this pedal. One is the gain created by the opamp, and the other is the clipping diodes.

The gain of the opamp determines the amplitude of the output signal. The more gain from the opamp, the more of the signal gets sent to ground through the clipping diodes.

Therefore, the higher the gain (controlled by the 100K potentiometer), the stronger the distortion.

![clipping](https://github.com/user-attachments/assets/2bee0f52-bc85-4809-af1f-65718e56845b)


</br></br>
> [!NOTE]
> The original pedal used 1N914 silicon diodes. For availability, they are replaced with the 1N4148 silicon diodes.


</br></br>
C10 and R9 are just there for safety. C10 is a coupling capacitor to remove DC biasing signal. R9 limits the current into the diodes and the next stages.


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

The output stage is effectively a _voltage follower_, AKA a _unitary gain amplifier_ or buffer. This is based around a JFET in _common drain_ configuration. This does not amplify or modify the signal. Instead it takes a low impedance signal and converts it to a high impedance signal.

There are two main achievements with this:
1. The integrity of the signal is preserved (no tone lost)
2. The tone stage is isolated from the volume, so they don't affect each other


</br></br>
> [!NOTE]
> The original pedal used a 2N5458 JFET. This is obsolete, and replaced with a J201 in this version.

</br></br>
![output](https://github.com/user-attachments/assets/7017f78b-6554-4e67-a7b9-b77d68effffe)

</br></br>
As the JFET is a J201 in this version, there are some slight changes to the circuit to make it work. R11/R12 create a voltage divider to bias the JFET correctly. This also means that R12 is slightly larger than in the original circuit (where it was 1M).

C12 filters out any DC that could feed back into the tone stage, and C13 removes any DC from the signal that has passed through the JFET.

Finally there's a passive volume control, that dumps some of the signal to ground.


