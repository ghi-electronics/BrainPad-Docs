# Buttons
---
The four directional buttons (up, down, left and right) are used as inputs and can be read by your program to determine if the button is being pressed or not. They can be checked in two different ways. One way is to just check once to see if the button is being pressed. This works well, but it is possible to miss a button press if your program doesn't check often enough. Sometimes this is not a problem, but for some programs it may be an issue. The other way of checking buttons is to use an event handler.

An event handler will continuously check to see if a button has been pressed or released. A button is released when the person pushing the button stops pushing (or releases) the button. Once an event handler is set up, the BrainPad will start an event listener that will check the button for you. This allows your program to do other tasks without you worrying about missing a button event. Once the button is pushed (or released) the event listener will call your event handler. The event handler is code you write to tell the BrainPad how to react when a button is pushed (or released).

While an event handler is a little harder to set up, it allows the program to take care of other tasks while never missing a button event.

## Button Methods
 
* `BrainPad.Buttons.IsUpPressed()` - returns a boolean true if the up button is pressed and a boolean false otherwise.

* `BrainPad.Buttons.IsLeftPressed()` - returns a boolean true if the left button is pressed and a boolean false otherwise.

* `BrainPad.Buttons.IsRightPressed()` - returns a boolean true if the right button is pressed and a boolean false otherwise.

* `BrainPad.Buttons.IsDownPressed()` - returns a boolean true if the down button is pressed and a boolean false otherwise.

* `ButtonEventHandler` `WhenUpButtonPressed`

* `ButtonEventHandler` `WhenUpButtonReleased`

* `ButtonEventHandler` `WhenLeftButtonPressed`

* `ButtonEventHandler` `WhenLeftButtonReleased`

* `ButtonEventHandler` `WhenRightButtonPressed`

* `ButtonEventHandler` `WhenRightButtonReleased`
 
* `ButtonEventHandler` `WhenDownButtonPressed`

* `ButtonEventHandler` `WhenDownButtonReleased`

> [!Tip]
> When entering event listener code, hitting the `Tab` key after the `+=` (see sample below) will automatically complete the line of code and generate a basic event handler routine.

## Button Sample Code
The following program uses both polling and an event handler to check the up and down buttons. When the up button is pressed the light bulb will turn blue, and when the down button is pressed the light bulb will turn off.

To try it, [start a new C# project](../csharp/intro.md#start-a-new-project), [manage the NuGet packages](../csharp/intro.md#manage-the-nuget-packages), and [add the BrainPad helper code](../csharp/intro.md#add-the-brainpad-helper-code). Then copy this code and paste it into the `Program.cs` window replacing just the `main` method in the original program.

```
static void Main()
{
    BrainPad.Buttons.WhenDownButtonPressed += Buttons_WhenDownButtonPressed;

    while (true)
    {
        if (BrainPad.Buttons.IsUpPressed()) BrainPad.LightBulb.TurnBlue();
        BrainPad.Wait.Minimum();
    }
}

private static void Buttons_WhenDownButtonPressed()
{
    BrainPad.LightBulb.TurnOff();
}
```