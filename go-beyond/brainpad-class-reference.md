# BrainPad Class Reference

## BrainPad.Accelerometer  
The BrainPad’s built-in accelerometer returns X,Y and Z values as the variable type double.   
 
        BrainPad.Accelerometer.ReadX() – (? Max - ? Min) – returns a double based on the BrainPad’s X position.  
        BrainPad.Accelerometer.ReadY()– (? Max - ? Min) – returns a double based on the BrainPad’s Y position.    
BrainPad.Accelerometer.ReadZ()– (? Max - ? Min) – returns a double based on the BrainPad’s Z position.    
 
BrainPad.Buttons  
These commands are used to access BrainPad’s 4 buttons labelled L, U, R, D.   
 
        ButtonEventHandler WhenDownButtonReleased 
 
        ButtonEventHandler WhenUpButtonPressed 
 
        ButtonEventHandler WhenUpButtonReleased 
 
        ButtonEventHandler WhenRightButtonPressed 
        ButtonEventHandler WhenRightButtonReleased 
        ButtonEventHandler WhenDownButtonPressed 
        ButtonEventHandler WhenLeftButtonReleased 
        ButtonEventHandler WhenLeftButtonPressed 
 
         
BrainPad.Buttons.IsDownPressed() – return True or False depending on if the “Down” button is pressed 
BrainPad.Buttons.IsLeftPressed() – return True or False depending on if the “Left” button is pressed 
BrainPad.Buttons.IsRightPressed() – return True or False depending on if the “Right” button is pressed 
BrainPad.Buttons.IsUpPressed()– return True or False depending on if the “Up” button is pressed 
 
BrainPad.Buzzer  
 
BrainPad.Buzzer.Beep() – Plays a default tone, for a default duration.  
 
[Example: BrainPad.Buzzer.StartBuzzing(251.00)] 
       BrainPad.Buzzer.StartBuzzing(double frequency) – Plays a tone based on the frequency passed in the methods parameters.  
       BrainPad.Buzzer.StopBuzzing() – Stops the Buzzer sound. 
 
BrainPad.Display 
Display commands in this section only change the memory buffer of the display and aren’t seen until you also run BrainPad.Display.ShowOnScreen() method. To see the results on the BrainPad’s display  
 
BrainPad.Display.Height() – returns the BrainPad’s display height = 64 
BrainPad.Display.Width() - returns the BrainPad’s display width = 128 
 
[Example: BrainPad.Display.DrawSmallNumber(10, 20, 10000000)] 
BrainPad.Display.DrawSmallNumber(int x, int y, long number) - Displays a small 8x8 pixel number at the display’s x and y coordinate. 
BrainPad.Display.DrawSmallNumber(int x, int y, double number) – Overloaded function, that accept doubles as the number. 
BrainPad.Display.DrawNumber(int x, int y, long number); 
        BrainPad.Display.DrawNumber(int x, int y, double number); 
  
 
[Example: BrainPad.Display.DrawSmallText(20, 20, “Hello”)] 
        BrainPad.Display.DrawSmallText(int x, int y, string text) - Draws the string in the parameter at the display’s x and y coordinate.  
        BrainPad.Display.DrawText(int x, int y, string text) – Draws a larger font string at the display’s x and y coordinate. 
BrainPad.Display.DrawScaledText(int x, int y, string text, int HScale, int VScale); 
 
         
 
        BrainPad.Display.CreatePicture(int width, int height, byte[] data); 
        BrainPad.Display.CreateScaledPicture(int width, int height, byte[] data, int scale); 
 
        BrainPad.Display.DrawCircle(int x, int y, int r) – Draws a circle located at the display’s x and y coordinates. Using r as the radius.  
BrainPad.Display.DrawRectangle(int x, int y, int width, int height); 
BrainPad.Display.DrawFilledRectangle(int x, int y, int width, int height) - Draws a filled box at the display’s x and y coordinates. Width and height are in pixels.   
BrainPad.Display.DrawLine(int x0, int y0, int x1, int y1) – Draws a line starting at the first parameters x and y coordinates, ending at the second parameters x and y coordinates.  
        BrainPad.Display.DrawPoint(int x, int y); 
 
 
         
 
        BrainPad.Display.DrawPicture(int x, int y, Picture picture); 
        BrainPad.Display.DrawPictureFlippedHorizontally(int x, int y, Picture picture); 
        BrainPad.Display.DrawPictureFlippedVertically(int x, int y, Picture picture); 
        BrainPad.Display.DrawPictureRotated180Degrees(int x, int y, Picture picture); 
        BrainPad.Display.DrawPictureRotated270Degrees(int x, int y, Picture picture); 
        BrainPad.Display.DrawPictureRotated90Degrees(int x, int y, Picture picture); 
                         
        [Example: BrainPad.Display.ClearPartOfScreen(int x, int y, int width, int height);  
BrainPad.Display.ClearPartOfScreen(int x, int y, int width, int height); - Clears only a certain section of the display where x & y are the starting positions and the last two values create the width and the height of the area to erase.  
 
        BrainPad.Display.ClearPoint(int x, int y); - Clears a pixel located at the display’s x and y coordinate.  
        BrainPad.Display.ClearScreen() -- Clears the entire screen from the display memory/buffer 
 
                 
        BrainPad.Display.InvertColors(bool invert); 
 
ALL the commands above, only affect the BrainPad’s display memory/buffer, and must be ‘committed’ to the actual display, by also running the method. BrainPad.Display.ShowOnScreen(), as the last command.  Methods below have the ShowOnScreen() method built into their methods and don’t require the BrainPad.Display.ShowOnScreen() as the last command. Keep in mind though these methods also Clear the entire screen before displaying new text. 
 
BrainPad.Display.ShowOnScreen() 
Display commands in this section change the memory/buffer and display to the BrainPad display instantly.  They do this by running 3 methods consecutively BrainPad.Display.ClearScreen(), BrainPad.Display.Draw...etc() and finally BrainPad.Display.ShowOnScreen().  
 
        BrainPad.Display.ShowOnScreen(); 
 
BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, long number); 
        BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, double number); 
BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, long number); 
        BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, double number); 
BrainPad.Display.DrawTextAndShowOnScreen(int x, int y, string text); 
BrainPad.Display.DrawSmallTextAndShowOnScreen(int x, int y, string text); 
BrainPad.Display.DrawScaledTextAndShowOnScreen(int x, int y, string text, int HScale, int VScale); 
 
BrainPad.LightBulb. 
 
BrainPad.LightBulb.TurnColor(double r, double g, double b) – Used to create a variety of colors based on varying degrees of red, green and blue (min. 0 – max 100) 
              
       BrainPad.LightBulb.TurnRed() 
BrainPad.LightBulb.TurnGreen() 
BrainPad.LightBulb.TurnBlue() 
 
       BrainPad.LightBulb.TurnWhite() 
BrainPad.LightBulb.TurnOff() 
 
BrainPad.LightSensor 
 
BrainPad.LightSensor.ReadLightLevel() 
 
BrainPad.ServoMotors  
 
BrainPad.ServoMotors.ServoOne { get; } 
BrainPad.ServoMotors.ServoTwo { get; } 
BrainPad.ServoMotors.ConfigureAsContinuous(bool inverted); 
BrainPad.ServoMotors.ConfigureAsPositional(bool inverted); 
BrainPad.ServoMotors.ConfigurePulseParameters(double minimumPulseWidth, double maximumPulseWidth); 
BrainPad.ServoMotors.Set(double value); 
BrainPad.ServoMotors.Stop(); 
 
BrainPad.TemperatureSensor  
 
BrainPad.TemperatureSensor.ReadTemperatureInCelsius() – Returns the Celsius temp from the BrainPad’s sensor as a double.  
BrainPad.TemperatureSensor.ReadTemperatureInFahrenheit()– Returns the Fahrenheit temp from the BrainPad’s sensor as a double. 
 
BrainPad.Wait  
 
BrainPad.Wait.Milliseconds(double milliseconds) - Pause the code for the duration of the parameter in milliseconds.  
        BrainPad.Wait.Seconds(double seconds) - Pause the code for the duration of the parameter in seconds. 
BrainPad.Wait.Minimum() – Pause the code for a default minimum duration.   
 
 
BrainPad.WriteToComputer 
 
BrainPad.WriteToComputer(string message) – Writes the string in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(int message) – Writes the integer in its parameter to the Visual Studio Debug Output Window.  
BrainPad.WriteToComputer(double message) – Writes the double in its parameter to the Visual Studio Debug Output Window.  
 