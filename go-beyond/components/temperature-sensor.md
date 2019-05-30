# Temperature Sensor
---
The BrainPad temperature sensor is basically a digital thermometer. There are seperate commands for reading the temperature in Celsius and Fahrenheit.

## Temperature Sensor Methods
 
* `BrainPad.TemperatureSensor.ReadTemperatureInCelsius()` - Returns the temperature in Celsius from the BrainPad's sensor. Returns the temperature as type double.  

* `BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit()` - Returns the temperature in Fahrenheit from the BrainPad's sensor. Returns the temperature as type double.

## Temperature Sensor Sample Code
The following program displays the temperature in Fahrenheit on the BrainPad screen.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    while (true)
    {
        BrainPad.Display.Clear();
        BrainPad.Display.DrawSmallText(30, 0, "Temperature");
        BrainPad.Display.DrawNumber(25, 12, BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit());
        BrainPad.Display.DrawText(90, 12, "F");
        BrainPad.Display.DrawCircle(105, 14, 2); // Degree mark
        BrainPad.Display.DrawNumber(25, 36, BrainPad.TemperatureSensor.ReadTemperatureInCelsius());
        BrainPad.Display.DrawText(90, 36, "C");
        BrainPad.Display.DrawCircle(105, 38, 2); // Degree mark
        BrainPad.Display.RefreshScreen();
        BrainPad.Wait.Minimum();
    }
}
```