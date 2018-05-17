# Servo Motors
---
The BrainPad has built in support for two servo motors. These can be either continuous or positional servo motors. Continuous servo motors can have their speed and direction controlled but there is no control over their position. They are capabable of rotating continously in either direction.

Positional servo motors only accept position commands. Positional servo motors only rotate part way through a revolution, usually turning up to half of a revolution (180 degrees). While you can tell a servo motor to go to a specific position, you have no control over how fast it will get there. The positional servo motor will move to a given position as quickly as possible, but it's speed depends on how much load is put on the motor.

* `BrainPad.ServoMotors.ServoOne.ConfigureAsContinuous(bool inverted)`

* `BrainPad.ServoMotors.ServoTwo.ConfigureAsContinuous(bool inverted)` 

* `BrainPad.ServoMotors.ServoOne.ConfigureAsPositional(bool inverted)`

* `BrainPad.ServoMotors.ServoTwo.ConfigureAsPositional(bool inverted)`

* `BrainPad.ServoMotors.ServoOne.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth)`

* `BrainPad.ServoMotors.ServoTwo.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth)`

* `BrainPad.ServoMotors.ServoOne.Set(double value)`

* `BrainPad.ServoMotors.ServoTwo.Set(double value)`

* `BrainPad.ServoMotors.ServoOne.Stop()`

* `BrainPad.ServoMotors.ServoTwo.Stop()`
