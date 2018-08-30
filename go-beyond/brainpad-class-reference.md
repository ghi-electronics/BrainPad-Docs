# BrainPad Class Reference

## BrainPad.Accelerometer
The accelerometer is an input device that measures the force of acceleration in three axes (x, y, and z). This is commonly referred to as g-force and is expressed as a multiple of the force of gravity. For example an airplane pilot experiences of force of 2 g in a 60 degree banked turn. This means he is being pushed into his seat with a force that is double his weight. Fighter pilots may experience up to 9 g. The BrainPad returns an accelerometer value that is equal to g-force multiplied by 100.

If the BrainPad is laying flat on a table with the display away from you on the right side, the x-axis runs horizontally left and right, the y-axis goes horizontally toward you and away from you, and the z-axis extends vertically straight up and down. If the BrainPad is stationary in this position, the x and y axes would read 0, but the z-axis would read -100. This is because the force of gravity is pushing down on the accelerometer with force equal to 1 g (the force of the Earth's gravity). If you turn the BrainPad upside down, the z-axis would read 100. The only time all axes read zero is when the BrainPad is free falling. 

BrainPad.Accelerometer.EnableFullRange = {true|false} - If set to false, the accelerometer values range from -100 to 100 (-1 g to 1 g). If set to true, the accelerometer values range from -200 to 200 (-2 g to 2 g).

BrainPad.Accelerometer.ReadX() - returns an integer value in the range of -100 to 100 (or -200 to 200 if BrainPad.Accelerometer.EnableFullRange = true) based on the BrainPad's x-axis acceleration.
 
BrainPad.Accelerometer.ReadY() - returns an integer value in the range of -100 to 100 (or -200 to 200 if BrainPad.Accelerometer.EnableFullRange = true) based on the BrainPad's y-axis acceleration.

BrainPad.Accelerometer.ReadZ() - returns an integer value in the range of -100 to 100 (or -200 to 200 if BrainPad.Accelerometer.EnableFullRange = true) based on the BrainPad's z-axis acceleration.

## BrainPad.Buttons  
The four directional buttons (up, down, right and left) are used as inputs and can be read by your program to determine if the button is being pressed or not. They can be checked in two different ways. One way is to just check once to see if the button is being pressed. This works well, but it is possible to miss a button press if your program doesn't check often enough. Sometimes this is not a problem, but for some programs it may be an issue. The other way of checking buttons is to use an event handler.

An event handler will continuously check to see if a button has been pressed or released. A button is released when the person pushing the button stops pushing the button. Once an event handler is set up, the BrainPad will start an event listener that will check the button for you. This allows your program to do other tasks without you worrying about missing a button event. Once the button is pushed (or released) the event listener will call your event handler. The event handler is code you write to tell the BrainPad how to react when a button is pushed (or released).

While an event handler is a little harder to set up, it has the advantage allowing you to be concerned with other tasks and never missing a button event.
 
BrainPad.Buttons.IsUpPressed() – returns a boolean true if the up button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsLeftPressed() – returns a boolean true if the left button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsRightPressed() – returns a boolean true if the right button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsDownPressed() – returns a boolean true if the down button is pressed and a boolean false otherwise.

ButtonEventHandler WhenDownButtonReleased 
ButtonEventHandler WhenUpButtonPressed 
ButtonEventHandler WhenUpButtonReleased 
ButtonEventHandler WhenRightButtonPressed 
ButtonEventHandler WhenRightButtonReleased 
ButtonEventHandler WhenDownButtonPressed 
ButtonEventHandler WhenLeftButtonReleased 
ButtonEventHandler WhenLeftButtonPressed 
 
         
 
## BrainPad.Buzzer
The BrainPad buzzer is an output device. It is really not a buzzer but a crude speaker that is even capable of playing voice or music, but with very poor quality. The buzzer commands allow you to make a beep sound where you have no control over the frequency or duration of the sound. You can also tell the BrainPad to play a tone where you decide the frequency. The BrainPad will keep playing that sound until you tell it to stop. This allows you to play sound effects for games as well as simple melodies.
 
BrainPad.Buzzer.Beep() – Plays a short duration beep on the BrainPad's buzzer.  
 
BrainPad.Buzzer.StartBuzzing(double frequency) – Plays a sound of the given frequency. Will keep playing untils told to stop. [Example: BrainPad.Buzzer.StartBuzzing(251.00)] 
BrainPad.Buzzer.StopBuzzing() – Stops the buzzer if it is currently playing.
 
## BrainPad.Display 
The BrainPad display is an output device. The BrainPad has commands allowing you to display numbers and text and draw simple pictures and shapes including points, lines, circles and rectangles.

Display commands in this section only change the memory buffer of the display and are not seen until you also call the BrainPad.Display.RefreshScreen() method.  
 
BrainPad.Display.Height() – returns the BrainPad display's height in pixels (64). 
BrainPad.Display.Width() - returns the BrainPad display's width in pixels (128).
 
BrainPad.Display.DrawSmallNumber(int x, int y, long number) - Displays a number of type long in small text at the given x and y coordinates. [Example: BrainPad.Display.DrawSmallNumber(10, 20, 52)]
BrainPad.Display.DrawSmallNumber(int x, int y, double number) – Displays a number of type double in small text at the given x and y coordinates.
BrainPad.Display.DrawNumber(int x, int y, long number) - Displays a number of type long in large text at the given x and y coordinates.
BrainPad.Display.DrawNumber(int x, int y, double number) - Displays a number of type double in large text at the given x and y coordinates. 

BrainPad.Display.DrawSmallText(int x, int y, string text) - Displays a string in small text at the given x and y coordinates. [Example: BrainPad.Display.DrawSmallText(20, 20, “Hello”)]  
BrainPad.Display.DrawText(int x, int y, string text) – Displays a string in small text at the given x and y coordinates.
BrainPad.Display.DrawScaledText(int x, int y, string text, int HScale, int VScale); 
 
BrainPad.Display.CreatePicture(int width, int height, byte[] data); 
BrainPad.Display.CreateScaledPicture(int width, int height, byte[] data, int scale); 
 
BrainPad.Display.DrawCircle(int x, int y, int r) – Draws a circle of radius r with the center located at the given x and y coordinates.  
BrainPad.Display.DrawRectangle(int x, int y, int width, int height); 
BrainPad.Display.DrawFilledRectangle(int x, int y, int width, int height) - Draws a filled box at the display’s x and y coordinates. Width and height are in pixels.   
BrainPad.Display.DrawLine(int x0, int y0, int x1, int y1) – Draws a line from (x0, y0) to (x1, y1).  
BrainPad.Display.DrawPoint(int x, int y) - Turns on a single pixel at the given x and y coordinates.
 
BrainPad.Display.DrawPicture(int x, int y, Picture picture); 
BrainPad.Display.DrawPictureFlippedHorizontally(int x, int y, Picture picture); 
BrainPad.Display.DrawPictureFlippedVertically(int x, int y, Picture picture); 
BrainPad.Display.DrawPictureRotated180Degrees(int x, int y, Picture picture); 
BrainPad.Display.DrawPictureRotated270Degrees(int x, int y, Picture picture); 
BrainPad.Display.DrawPictureRotated90Degrees(int x, int y, Picture picture); 
                         
BrainPad.Display.ClearPartOfScreen(int x, int y, int width, int height); - Clears a rectangular section of the display where x and y are the top left corner of the rectangle of given width and height 
 
BrainPad.Display.ClearPoint(int x, int y); - Clears a pixel located at the display’s x and y coordinate.  
BrainPad.Display.ClearScreen() - Clears the entire screen buffer. 

BrainPad.Display.InvertColors(bool invert); 
BrainPad.Display.RefreshScreen() 
 
## BrainPad.LightBulb. 
The BrainPad Light Bulb is actually three light emitting diodes (LEDs) in one package. One LED is red, one is green, and one is blue. These can turned on independantly at varying intensities to create up to one million different colors.


BrainPad.LightBulb.TurnColor(double r, double g, double b) – Used to create a variety of colors based on varying degrees of red, green and blue (min. 0 – max 100) 
BrainPad.LightBulb.TurnRed() 
BrainPad.LightBulb.TurnBlue() 
BrainPad.LightBulb.TurnGreen() 
BrainPad.LightBulb.TurnWhite() 
BrainPad.LightBulb.TurnOff() 
 
## BrainPad.LightSensor
The BrainPad Light Sensor is used to measure the amount of light falling on the sensor. 
 
BrainPad.LightSensor.ReadLightLevel() 
 
## BrainPad.ServoMotors  
The BrainPad has built in support for two servo motors. These can be either continuous or positional servo motors. Continuous servo motors can have their speed and direction controlled but there is no control over their position. They are capabable of rotating continously in either direction.

Positional servo motors only accept position commands. Positional servo motors only rotate part way through a revolution, usually turning up to half of a revolution (180 degrees). While you can tell a servo motor to go to a specific position, you have no control over how fast it will get there. The positional servo motor will move to a given position as quickly as possible, but it's speed depends on how much load is put on the motor.

BrainPad.ServoMotors.ServoOne { get; } 
BrainPad.ServoMotors.ServoTwo { get; } 
BrainPad.ServoMotors.ConfigureAsContinuous(bool inverted); 
BrainPad.ServoMotors.ConfigureAsPositional(bool inverted); 
BrainPad.ServoMotors.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth); 
BrainPad.ServoMotors.Set(double value); 
BrainPad.ServoMotors.Stop(); 
 
## BrainPad.TemperatureSensor
The BrainPad temperature sensor is basically a digital thermometer. The commands for reading the temperature can report the temperature in either Celsius or Fahrenheit.
 
BrainPad.TemperatureSensor.ReadTemperatureInCelsius() – Returns the Celsius temp from the BrainPad’s sensor as a double.  
BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit()– Returns the Fahrenheit temp from the BrainPad’s sensor as a double. 
 
## BrainPad.Wait  
This command tells the BrainPad to wait and do nothing for the time specified. This command could be used to play a musical note for a given duration. It can also be used to tell the BrainPad to wait long enough for another task to finish. For example, you might tell a servo motor to move to a specified position and then tell the BrainPad to wait to give the servo time to move to that position.

BrainPad.Wait.Milliseconds(double milliseconds) - Pause the code for the duration of the parameter in milliseconds.  
BrainPad.Wait.Seconds(double seconds) - Pause the code for the duration of the parameter in seconds. 
BrainPad.Wait.Minimum() – Pause the code for a default minimum duration.   
 
 
## BrainPad.WriteToComputer 
This command writes numbers or text to the computers Visual Studio debug output window. This can be helpful for debugging or finding the errors in a program. For example, if you are doing a calculation involving a large number of steps that is giving an incorrect result, you can write the result of each step to the computer to figure out which step is not working properly. You could use the BrainPad's display to do the same thing, but the display might already be in use or might not be big enough to display all the information.

BrainPad.WriteToComputer(string message) – Writes the string in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(int message) – Writes the integer in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(double message) – Writes the double in its parameter to the Visual Studio Debug Output Window.  
 