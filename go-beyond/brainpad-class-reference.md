# BrainPad Class Reference

## BrainPad.Accelerometer  
The BrainPad’s built-in accelerometer returns X, Y and Z values as a variable of type double.   

BrainPad.Accelerometer.ReadX() – returns a double in the range of -2 to 2 based on the BrainPad’s X-axis acceleration.  
BrainPad.Accelerometer.ReadY()– returns a double in the range of -2 to 2 based on the BrainPad’s Y-axis acceleration.
BrainPad.Accelerometer.ReadZ()– returns a double in the range of -2 to 2 based on the BrainPad’s Z-axis acceleration.

## BrainPad.Buttons  
These commands are used to access BrainPad’s four buttons labelled L, U, R, D.   
 
ButtonEventHandler WhenDownButtonReleased 
ButtonEventHandler WhenUpButtonPressed 
ButtonEventHandler WhenUpButtonReleased 
ButtonEventHandler WhenRightButtonPressed 
ButtonEventHandler WhenRightButtonReleased 
ButtonEventHandler WhenDownButtonPressed 
ButtonEventHandler WhenLeftButtonReleased 
ButtonEventHandler WhenLeftButtonPressed 
 
         
BrainPad.Buttons.IsUpPressed() – returns a boolean true if the up button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsLeftPressed() – returns a boolean true if the left button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsRightPressed() – returns a boolean true if the right button is pressed and a boolean false otherwise.
BrainPad.Buttons.IsDownPressed() – returns a boolean true if the down button is pressed and a boolean false otherwise.
 
## BrainPad.Buzzer  
 
BrainPad.Buzzer.Beep() – Plays a short duration beep on the BrainPad's buzzer.  
 
BrainPad.Buzzer.StartBuzzing(double frequency) – Plays a sound of the given frequency. Will keep playing untils told to stop. [Example: BrainPad.Buzzer.StartBuzzing(251.00)] 
BrainPad.Buzzer.StopBuzzing() – Stops the buzzer if it is currently playing.
 
## BrainPad.Display 
Display commands in this section only change the memory buffer of the display and are not seen until you also call the BrainPad.Display.ShowOnScreen() method.  
 
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
BrainPad.Display.ShowOnScreen() 
 
The above display commands only affect the BrainPad’s display's memory/buffer, and must be ‘committed’ to the display by running the method BrainPad.Display.ShowOnScreen(). The display methods below have the ShowOnScreen() method built in and don’t require the use of BrainPad.Display.ShowOnScreen(). Keep in mind though that these methods also clear the entire screen before displaying new text. 
 
Display commands in this section change the memory/buffer and display to the BrainPad display instantly.  They do this by running 3 methods consecutively BrainPad.Display.ClearScreen(), BrainPad.Display.Draw...etc() and finally BrainPad.Display.ShowOnScreen().  
 
BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, long number); 
BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, double number); 
BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, long number); 
BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, double number); 
BrainPad.Display.DrawTextAndShowOnScreen(int x, int y, string text); 
BrainPad.Display.DrawSmallTextAndShowOnScreen(int x, int y, string text); 
BrainPad.Display.DrawScaledTextAndShowOnScreen(int x, int y, string text, int HScale, int VScale); 
 
## BrainPad.LightBulb. 
 
BrainPad.LightBulb.TurnColor(double r, double g, double b) – Used to create a variety of colors based on varying degrees of red, green and blue (min. 0 – max 100) 
BrainPad.LightBulb.TurnRed() 
BrainPad.LightBulb.TurnBlue() 
BrainPad.LightBulb.TurnGreen() 
BrainPad.LightBulb.TurnWhite() 
BrainPad.LightBulb.TurnOff() 
 
## BrainPad.LightSensor 
 
BrainPad.LightSensor.ReadLightLevel() 
 
## BrainPad.ServoMotors  
 
BrainPad.ServoMotors.ServoOne { get; } 
BrainPad.ServoMotors.ServoTwo { get; } 
BrainPad.ServoMotors.ConfigureAsContinuous(bool inverted); 
BrainPad.ServoMotors.ConfigureAsPositional(bool inverted); 
BrainPad.ServoMotors.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth); 
BrainPad.ServoMotors.Set(double value); 
BrainPad.ServoMotors.Stop(); 
 
## BrainPad.TemperatureSensor  
 
BrainPad.TemperatureSensor.ReadTemperatureInCelsius() – Returns the Celsius temp from the BrainPad’s sensor as a double.  
BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit()– Returns the Fahrenheit temp from the BrainPad’s sensor as a double. 
 
## BrainPad.Wait  
 
BrainPad.Wait.Milliseconds(double milliseconds) - Pause the code for the duration of the parameter in milliseconds.  
BrainPad.Wait.Seconds(double seconds) - Pause the code for the duration of the parameter in seconds. 
BrainPad.Wait.Minimum() – Pause the code for a default minimum duration.   
 
 
## BrainPad.WriteToComputer 
 
BrainPad.WriteToComputer(string message) – Writes the string in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(int message) – Writes the integer in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(double message) – Writes the double in its parameter to the Visual Studio Debug Output Window.  
 