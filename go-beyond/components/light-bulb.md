# Light Bulb
---
The BrainPad Light Bulb actually contains three light emitting diodes (LEDs) in one package. One LED is red, one is green, and one is blue. These can independently set to varying intensities to create up to one million different colors.

* BrainPad.LightBulb.TurnColor(double r, double g, double b) - Used to create a variety of colors by controlling the brightness of the red, green and blue LEDs. The minimum color intensity is 0 (off) and the maximum is 100. 

* BrainPad.LightBulb.TurnRed() - Turns the light bulb red at full intensity.

* BrainPad.LightBulb.TurnBlue() - Turns the light bulb blue at full intensity.

* BrainPad.LightBulb.TurnGreen() - Turns the light bulb green at full intensity.

* BrainPad.LightBulb.TurnWhite() - Turns the light bulb white at full intensity.

* BrainPad.LightBulb.TurnOff() - Turns off the light bulb. Same as BrainPad.LightBulb.TurnColor(0.0, 0.0, 0.0)