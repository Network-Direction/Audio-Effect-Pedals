# JFET Matcher

JFETs, unlike BJT's, have a wide variance in their characteristics. For example, when we look at the datasheet for the J113 transistor, the Vgs (voltage between gate and source pins) is listed as being somewhere between 0.5 volts and 3.0 volts.

In many cases, this doesn't really matter. However, there are cases such as the MXR Phase 90 pedal that use multiple JFETs as variable resistors (four in the Phase 90). In a case like this, the **Vgs** of each transistor should be as close to identical as possible.

This means we need to manually check the **Vgs** of each transistor, and match up two, four, or however many we need.

