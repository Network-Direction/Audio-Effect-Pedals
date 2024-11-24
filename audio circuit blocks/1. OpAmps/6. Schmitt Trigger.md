# Schmitt Triggers

A **schmitt trigger** is a type of circuit that converts a sine wave to a square wave. It is used in applications such as analogue to digital conversion, oscillators, and other signal processing.

The key point in a schmitt trigger is _hysteresis_. The schmitt trigger defines an upper and lower threshold, which eliminates spurious signal changes when noise is present.

</br></br>

## The Circuit
The schmitt trigger is effectively a comparator that includes a feedback network. The non-inverting input is connected to ground, which sets our reference point (the vertical midpoint of our waveform) at zero volts.
In other versions of this circuit, we might connect the inverting input to a virtual ground (a reference voltage) to bias the opamp to use some other value as the midpoint of the waveform.

![schmitt trigger](https://github.com/user-attachments/assets/f4784338-d9ad-4545-823b-fb46867b6674)


The ratio between R1 and R2 (a voltage divider) create the upper and lower thresholds. The output voltage (Vout) feeds back through R2 to the non-inverting input.

</br></br>


## Thresholds

To calculate the thresholds, we first need to know the output voltage range of the opamp. Let’s assume we can get from -6v to +6v.

Let’s also assume for now that R1 is 10K, and R2 is 20K.

To calculate either threshold:

```math
threshold = {R1 \over (R1+R2)} \times Vout
```
</br></br>

Let’s work on the upper threshold first. In this case we have:

```math
threshold = {10K \over 10K + 20K} \times 6v
```
</br></br>

That is 1/3 times 6 volts, which is +2v. The input voltage will have to exceed 2v before the output will switch from -6v to +6v.

The lower threshold is calculated the same way. 1/3 multiplied by -6v is -2v. The input signal will have to drop below -2v before the output will switch from +6v to -6v.

</br></br>
What if we don’t have a negative power supply? In this case, our output voltage (Vout) may be something like +5v and 0v.

The same calculations apply here. The upper threshold is 1/3 multiplied by 5v, which is 1.67v. The lower threshold is 1/3 multiplied by 0v, which of course is 0 volts.

