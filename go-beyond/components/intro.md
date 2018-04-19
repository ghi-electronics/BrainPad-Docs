# Components
---
This section provides descriptions of the various BrainPad components and a list of the methods used to interact with each component. Each of these components acts as either an input device or an output device. Input and output are defined by whether the information for the component goes into, or comes out of, the "brain." The "brain" is the processor chip or microcontroller in the center of the BrainPad.

If information flows into the processor it is considered an input device. For example, the temperature sensor is read by the processor when your program wants to know the temperature. The temperature sensor is an input device -- the temperature information moves from the sensor *into* the processor.

The buzzer is an output device. When you program the BrainPad to produce sound, the sound information is *output* from the processor to the buzzer.

In humans, ears are input devices, and the mouth is an output device. Together they allow us to communicate. Just like the BrainPad, your brain gets input from your ears, processes it and figures out what to say, and then sends output to your mouth and vocal cords to generate speech.

The BrainPad has all of its inputs arranged on the left side of the board:
* [Accelerometer](accelerometer.md)
* [Buttons](buttons.md)
* [Light Sensor](light-sensor.md)
* [Temperature Sensor](temperature-sensor.md)

All of the output devices are on the right side of the BrainPad:
* [Buzzer](buzzer.md)
* [Display](display.md)
* [Light Bulb](light-bulb.md)
* [Servo Motors](servo-motors.md)

So the flow of information on the BrainPad goes from left to right. Inputs come in from the sensors on the left side of the BrainPad, are processed by the "brain," and then sent to the output devices on the right side of the board. Note that most devices are not set up this way -- we did this to make it a little easier to learn and understand how the BrainPad works.