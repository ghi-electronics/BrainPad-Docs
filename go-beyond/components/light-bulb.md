# Light Bulb
---
The BrainPad Light Bulb actually contains light emitting diodes (LEDs) in one package. One LED is red, one is green, and one is blue. These can turned on independantly at varying intensities to create up to one million different colors.

BrainPad.LightBulb.TurnColor(double r, double g, double b) - Used to create a variety of colors based on varying degrees of red, green and blue. The minimum color intensity is 0 (off) and the maximum is 100. 

* BrainPad.LightBulb.TurnRed() - Lights the light bulb red at full intensity.

* BrainPad.LightBulb.TurnBlue() - Lights the light bulb blue at full intensity.

* BrainPad.LightBulb.TurnGreen() - Lights the light bulb green at full intensity.

* BrainPad.LightBulb.TurnWhite() - Lights the light bulb white at full intensity.

* BrainPad.LightBulb.TurnOff() - Turns off the light bulb. Same as BrainPad.LightBulb.TurnColor(0.0, 0.0, 0.0)