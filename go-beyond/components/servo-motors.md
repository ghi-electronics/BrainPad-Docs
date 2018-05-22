# Servo Motors
---
The BrainPad has built in support for two servo motors. These can be either continuous or positional servo motors. Continuous servo motors can have their speed and direction controlled but there is no control over their position. They are capabable of rotating continously in either direction.

Positional servo motors only accept position commands. Positional servo motors only rotate part way through a revolution, usually turning up to half of a revolution (180 degrees). While you can tell a servo motor to go to a specific position, you have no control over how fast it will get there. The positional servo motor will move to a given position as quickly as possible, but it's speed depends on how much load is put on the motor.

## Servo Motor Methods

* `BrainPad.ServoMotors.ServoOne.ConfigureAsContinuous(bool inverted)` (A `true` argument will make the motor move in the opposite direction.)

* `BrainPad.ServoMotors.ServoTwo.ConfigureAsContinuous(bool inverted)` (A `true` argument will make the motor move in the opposite direction.)

* `BrainPad.ServoMotors.ServoOne.ConfigureAsPositional(bool inverted)` (A `true` argument will invert the position so the 0 degree position becomes the 180 degree position and vice versa.)

* `BrainPad.ServoMotors.ServoTwo.ConfigureAsPositional(bool inverted)` (A `true` argument will invert the position so the 0 degree position becomes the 180 degree position and vice versa.)

* `BrainPad.ServoMotors.ServoOne.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth)` (Pulse width in milliseconds)

* `BrainPad.ServoMotors.ServoTwo.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth)` (Pulse width in milliseconds)

* `BrainPad.ServoMotors.ServoOne.Set(double value)` (allowable position from 0 to 180 degrees for positional motors, allowable speed from -100% to 100% for continuous motors.)

* `BrainPad.ServoMotors.ServoTwo.Set(double value)` (allowable position from 0 to 180 degrees for positional motors, allowable speed from -100% to 100% for continuous motors.)

* `BrainPad.ServoMotors.ServoOne.Stop()`

* `BrainPad.ServoMotors.ServoTwo.Stop()`

## Servo Motor Sample Code

### Positional Servo Example

The following program configures servo one for a servo motor that expects positional pulses in the one to two millisecond range. It then moves the motor to the zero degree position, waits five seconds, and then moves the motor to the 180 degree position.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing the just the `main` method in the original program.

```
static void Main()
{
    BrainPad.ServoMotors.ServoOne.ConfigureAsPositional(false);
    BrainPad.ServoMotors.ServoOne.ConfigurePulseParameters(1.0, 2.0);

    BrainPad.ServoMotors.ServoOne.Set(0.0);
    BrainPad.Wait.Seconds(5.0);
    BrainPad.ServoMotors.ServoOne.Set(180.0);
}
```

### Continuous Servo Example

The following program configures servo two for connection to a continous servo motor. The program moves the motor for five seconds at 100 percent speed in one direction, and then reverses direction for 5 seconds at 60 percent speed. It then stops the motor.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    BrainPad.ServoMotors.ServoTwo.ConfigureAsContinuous(false);

    BrainPad.ServoMotors.ServoTwo.Set(100);
    BrainPad.Wait.Seconds(5);
    BrainPad.ServoMotors.ServoTwo.Set(-60);
    BrainPad.Wait.Seconds(5);
    BrainPad.ServoMotors.ServoTwo.Set(0);
}
```