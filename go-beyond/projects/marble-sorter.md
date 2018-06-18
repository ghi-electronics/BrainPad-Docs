# Marble Sorting Robot
---

**Difficulty: Fairly difficult. Construction required.**

**Objective: Servo control / simple robotics.**

This project requires a two positional servo motors. More details are found at the bottom of this page.

## How it Works
The BrainPad is programmed to seperate black and white marbles using the light sensor and two servo motors.

## The Code in C#

```
using System.Diagnostics;

namespace BrainPadMarbleSorter
{
    class Program
    {
        static void Main()
        {
            int LightLevel;

            BrainPad.ServoMotors.ServoOne.ConfigureAsPositional(false);
            BrainPad.ServoMotors.ServoOne.ConfigurePulseParameters(0.5, 2.5);
            BrainPad.ServoMotors.ServoOne.Set(125.0);

            BrainPad.ServoMotors.ServoTwo.ConfigureAsPositional(false);
            BrainPad.ServoMotors.ServoTwo.ConfigurePulseParameters(0.5, 2.5);
            BrainPad.ServoMotors.ServoTwo.Set(80.0);

            // Servo1 is marble release.  65 degrees lets marble in for scanning.  125 degrees releases marble and blocks next one.
            // Servo2 is deflector.  80 degrees lifts deflector allowing marble underneath.  127 degrees lowers and deflects marble.

            for (int marbleNumber = 0; marbleNumber < 20; marbleNumber++)
            {
                BrainPad.ServoMotors.ServoOne.Set(73);
                BrainPad.Wait.Milliseconds(180);
                LightLevel = BrainPad.LightSensor.ReadLightLevel();
                Debug.WriteLine(LightLevel.ToString());

                if (LightLevel < 35) BrainPad.ServoMotors.ServoTwo.Set(127);
                else BrainPad.ServoMotors.ServoTwo.Set(80);

                BrainPad.ServoMotors.ServoOne.Set(117);
                BrainPad.Wait.Milliseconds(180);
            }
        }
    }
}
```
