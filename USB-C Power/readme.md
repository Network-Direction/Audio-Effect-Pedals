# USB-C Power Supply

Supplies 9v power to multiple pedals using USB-C as input.


</br></br>
## Version #1

* 4x 9v output
* USB-C input, power only (no data)
* Fixed 9v output
* Fixed current negotiation of 2A (meaning a USB power supply capable of 2A is required)
* Red LED to report negotiation errors


</br></br>
### Notes

* On the PCB, caps C7, C6, C9, and C5 need better spacing.
* Use a USB socket that allows surface mount ground pins, or update footprint to use through hole for these
* There is currently no way to detect drawing more than the negotiated current


</br></br>
### Improvement Ideas

* Add a selector switch to allow negotiating different currents
* Green LED to report that all is well
* Per-output protection (schottky diode) for reverse voltage protection and voltage sag prevention
