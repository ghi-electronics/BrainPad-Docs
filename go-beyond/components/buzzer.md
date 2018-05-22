# Buzzer
---
The BrainPad buzzer is an output device. It is really not a buzzer but a crude speaker that is even capable of playing voice or music, but with poor sound quality. The buzzer's beep command allows you to make a beep sound with no control over the beep's frequency or duration.

You can also tell the BrainPad to play a tone where you decide the frequency. The BrainPad will keep playing that sound until you tell it to stop or tell it to play a different tone. This allows you to play sound effects for games as well as simple melodies.

## Buzzer Methods
 
* `BrainPad.Buzzer.Beep()` - Plays a short duration beep on the BrainPad's buzzer.  
 
* `BrainPad.Buzzer.StartBuzzing(double frequency)` - Plays a sound of given frequency. Will keep playing until told to stop.
* `BrainPad.Buzzer.StopBuzzing()` - Stops the buzzer if it is currently playing.

## Buzzer Sample Code

The following program makes a siren sound while the down button is pressed.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    while (true)
    {
        if (BrainPad.Buttons.IsDownPressed())
        {
            for (int frequency = 1200; frequency < 3200; frequency += 160)
            {
                BrainPad.Buzzer.StartBuzzing(frequency);
                BrainPad.Wait.Milliseconds(8);
            }

            for (int frequency = 3200; frequency > 1200; frequency -= 160)
            {
                BrainPad.Buzzer.StartBuzzing(frequency);
                BrainPad.Wait.Milliseconds(8);
            }
        }
        else BrainPad.Buzzer.StopBuzzing();
    }
}
```