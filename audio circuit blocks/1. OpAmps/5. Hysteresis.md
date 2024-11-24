# Comparitors and Hysteresis

Hysteresis is where we define upper and lower thresholds that a signal needs to reach for an action to be performed.

Think of this example, we want to convert a sine wave to a digital square wave. For this we can use an ADC or Analogue to digital converter. 

This converter may look at the sine wave like the one shown here, which has a voltage range of 1v at the top, to -1v at the bottom. 

![ADC-1](https://github.com/user-attachments/assets/45d06a5d-f113-43da-a3b7-e8704186f439)
</br></br>



Let’s say that we want the square wave to operate at 5v at the top, and 0v at the bottom. Whenever the input voltage is greater than zero, the converter will set an output voltage of +5v. Whenever it is lower than 0, it will output 0v.

This can be done using a comparator circuit. The input signal is on the non-inverting input, and the inverting is connected to ground. The output will be driven all the way up, or all the way down, depending on whether the voltage is above or below zero volts.

![comparitor](https://github.com/user-attachments/assets/492bffff-c083-42f3-8bc5-373b2b24d267)
</br></br>


This will create a square wave like this:

![ADC-2](https://github.com/user-attachments/assets/261b7280-a487-467a-861c-a7807ff72c77)
</br></br>


That seems to work very nicely. Only there’s a problem. In the real world, there is often noise in signals, they’re not usually perfect sine waves. So what if the input signal were to fluctuate around the midpoint (0v) a little? This would cause the ADC to drive the output signal high or low when it’s not meant to do so.
That is, noise could cause rapid switching between the digital high and low signals.

To fix this, we can add hysteresis. This is an upper and lower threshold, or limit, that we define, like this:

![hysteresis](https://github.com/user-attachments/assets/20f6f65c-cf00-43dd-aca1-3288121ec616)
</br></br>


In this example, we set the limits at +0.6v and -0.6v. Now the signal voltage will have to be above 0.6v before the ADC drives the output signal to high (+5v in this case), and lower than -0.6v to drive the signal low (0v in this case).

The purpose of this is to ignore any small variability of the signal between these limits.

Note, some circuits will use only an upper threshold when implementing hysteresis. These are usually simpler, but more limited.

