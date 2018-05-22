# Light Bulb
---
The BrainPad Light Bulb actually contains three light emitting diodes (LEDs) in one package. One LED is red, one is green, and one is blue. These can independently set to varying intensities to create up to a million different colors.

## Light Bulb Methods

* `BrainPad.LightBulb.TurnColor(double r, double g, double b)` - Used to create a variety of colors by controlling the brightness of the red, green and blue LEDs. The minimum color intensity is 0 (off) and the maximum is 100. 

* `BrainPad.LightBulb.TurnRed()` - Turns the light bulb red at full intensity.

* `BrainPad.LightBulb.TurnBlue()` - Turns the light bulb blue at full intensity.

* `BrainPad.LightBulb.TurnGreen()` - Turns the light bulb green at full intensity.

* `BrainPad.LightBulb.TurnWhite()` - Turns the light bulb white at full intensity.

* `BrainPad.LightBulb.TurnOff()` - Turns off the light bulb. Same as BrainPad.LightBulb.TurnColor(0.0, 0.0, 0.0)

## Light Bulb Sample Code
The following program turns the light bulb red, blue, green and then a custom color. It changes color every second and repeats forever.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    while (true)
    {
        BrainPad.LightBulb.TurnRed();
        BrainPad.Wait.Seconds(1);
        BrainPad.LightBulb.TurnBlue();
        BrainPad.Wait.Seconds(1);
        BrainPad.LightBulb.TurnGreen();
        BrainPad.Wait.Seconds(1);
        BrainPad.LightBulb.TurnColor(5, 25, 100);
        BrainPad.Wait.Seconds(1);
    }
}
```