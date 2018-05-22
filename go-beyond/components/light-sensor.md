# Light Sensor
---
The BrainPad Light Sensor is used to measure the amount of light hitting the sensor.

## Light Sensor Method

* `BrainPad.LightSensor.ReadLightLevel()` - Reads the amount of light hitting the light sensor and returns an integer corresponding to the brightness. The higher the returned value greater the intensity of the light. The output range is from 0 to 100.

## Light Sensor Sample Code
This program acts as a simple night light. The lower the intensity of light hitting the sensor the brighter the light bulb gets.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    double lightLevel;
    while (true)
    {
        lightLevel = BrainPad.LightSensor.ReadLightLevel();
        lightLevel = 100 - lightLevel;
        BrainPad.LightBulb.TurnColor(lightLevel, lightLevel, lightLevel);
        BrainPad.Wait.Minimum();
    }
}
```
