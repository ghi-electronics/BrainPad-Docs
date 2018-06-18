# High/Low Thermometer
---
A simple high/low thermometer.

**Difficulty: Easy.**

**Objective: Basic sensing and control.**

## How it Works
This program uses the temperature sensor to read the current temperature and keep track of the high and low temperatures from the time the program starts. It changes the light bulb color depending on the current temperature. It also shows a bar graph at the bottom of the screen which reflects where the current temperature is relative to the high and low temperatures.

This project is a demonstration of a simple programmable control system. For example, instead of controlling the light bulb the temperature sensor could be used to control a fan. Such a system could be used to keep sensitive electronic components from overheating by turning on a cooling fan before the temperature gets too high.

## The code in C#
> [!Tip]
> Make sure the namespace in your program matches your project's namespace.  Your project's namespace can be found in the BrainPad Helper file by clicking on the BrainPad1.cs tab.  [**More Info**](../csharp/intro.md#a-few-words-about-namespaces).

```
using System;

namespace BrainPadHighLowThermometer {
    class Program {
    static double CurrentTemperature, MaximumTemperature, MinimumTemperature, TemperaturePosition;

        static void Main() {
            CurrentTemperature = BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit();
            MinimumTemperature = CurrentTemperature;
            MaximumTemperature = CurrentTemperature;

            while (true) {
                CurrentTemperature = BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit();
                if (CurrentTemperature > MaximumTemperature)
                    MaximumTemperature = CurrentTemperature;
                if (CurrentTemperature < MinimumTemperature)
                    MinimumTemperature = CurrentTemperature;

                BrainPad.Display.Clear();

                BrainPad.Display.DrawSmallText(39, 0, "Current");
                BrainPad.Display.DrawText(37, 12, (CurrentTemperature.ToString("F1")));

                BrainPad.Display.DrawSmallText(2, 34, "Minimum");
                BrainPad.Display.DrawText(0, 46, (MinimumTemperature.ToString("F1")));

                BrainPad.Display.DrawSmallText(72, 34, "Maximum");
                BrainPad.Display.DrawText(70, 46, (MaximumTemperature.ToString("F1")));

                if ((MaximumTemperature - MinimumTemperature) > 0) {
                    TemperaturePosition = (CurrentTemperature - MinimumTemperature) / (MaximumTemperature - MinimumTemperature) * 127;
                    BrainPad.Display.DrawLine(0, 63, (int)TemperaturePosition, 63);
                    BrainPad.Display.DrawPoint(0, 62);
                    BrainPad.Display.DrawPoint(127, 62);

                    BrainPad.LightBulb.TurnColor(TemperaturePosition / 32, 0, (127 - TemperaturePosition) / 16);
                }

                BrainPad.Display.RefreshScreen();
                BrainPad.Wait.Milliseconds(250);
            }
        }
    }
}
```