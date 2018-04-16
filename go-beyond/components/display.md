# Display
---
The BrainPad display is an output device. The BrainPad has commands allowing you to display numbers and text and draw simple pictures and shapes. These shapes including points, lines, circles and rectangles. All display commands use pixels as units.

Display commands in this section only change the memory buffer of the display and are not seen until you also call the BrainPad.Display.ShowOnScreen() method.  
 
* BrainPad.Display.Height() - returns the BrainPad display's height in pixels (64). 

* BrainPad.Display.Width() - returns the BrainPad display's width in pixels (128).
 
* BrainPad.Display.DrawSmallNumber(int x, int y, long number) - Displays a number of type long in small text at the given x and y coordinates. [Example: BrainPad.Display.DrawSmallNumber(10, 20, 52)]

* BrainPad.Display.DrawSmallNumber(int x, int y, double number) - Displays a number of type double in small text at the given x and y coordinates.

* BrainPad.Display.DrawNumber(int x, int y, long number) - Displays a number of type long in large text at the given x and y coordinates.

* BrainPad.Display.DrawNumber(int x, int y, double number) - Displays a number of type double in large text at the given x and y coordinates. 

* BrainPad.Display.DrawSmallText(int x, int y, string text) - Displays a string in small text at the given x and y coordinates. [Example: BrainPad.Display.DrawSmallText(20, 20, "Hello")]  

* BrainPad.Display.DrawText(int x, int y, string text) - Displays a string in small text at the given x and y coordinates.

* BrainPad.Display.DrawScaledText(int x, int y, string text, int HScale, int VScale) - Displays text that can be made larger. Text size is multiplied by HScale to determing horizontal size and VScale to determine vertical size.
 
* BrainPad.Display.CreatePicture(int width, int height, byte[] data) - Used to store a picture for DrawPicture commands.

* BrainPad.Display.CreateScaledPicture(int width, int height, byte[] data, int scale) - Used to store a picture that will be displayed larger by a factor of scale.
 
* BrainPad.Display.DrawCircle(int x, int y, int r) - Draws a circle of radius r with the center located at the given x and y coordinates.  

* BrainPad.Display.DrawRectangle(int x, int y, int width, int height) - Draws a box at the given x and y coordinates.

* BrainPad.Display.DrawFilledRectangle(int x, int y, int width, int height) - Draws a filled box at the given x and y coordinates.   

* BrainPad.Display.DrawLine(int x0, int y0, int x1, int y1) - Draws a line from (x0, y0) to (x1, y1).  

* BrainPad.Display.DrawPoint(int x, int y) - Turns on a single pixel at the given x and y coordinates.
 
* BrainPad.Display.DrawPicture(int x, int y, Picture picture) - Draws the given picture at the given x and y coordinates.

* BrainPad.Display.DrawPictureFlippedHorizontally(int x, int y, Picture picture) - Flips the given picture horizontally and draws it at the given x and y coordinates.

* BrainPad.Display.DrawPictureFlippedVertically(int x, int y, Picture picture) - Flips the given picture vertically and draws it at the given x and y coordinates. 

* BrainPad.Display.DrawPictureRotated180Degrees(int x, int y, Picture picture) - Rotates the given picture 180 degrees and draws it at the given x and y coordinates. 

* BrainPad.Display.DrawPictureRotated270Degrees(int x, int y, Picture picture) - Rotates the given picture 270 degrees clockwise and draws it at the given x and y coordinates.

* BrainPad.Display.DrawPictureRotated90Degrees(int x, int y, Picture picture) - Rotates the given picture 90 degrees clockwise and draws it at the given x and y coordinates.
                         
* BrainPad.Display.ClearPartOfScreen(int x, int y, int width, int height) - Clears a rectangular section of the display where x and y are the top left corner of the rectangle of given width and height 
 
* BrainPad.Display.ClearPoint(int x, int y) - Clears the pixel located at the given x and y coordinates.  

* BrainPad.Display.ClearScreen() - Clears the entire screen buffer. 

* BrainPad.Display.InvertColors(bool invert) - Inverts the colors of the entire screen.

* BrainPad.Display.ShowOnScreen() - Writes the entire display buffer to the display. Used to show what has been drawn to the screen buffer on the display.
 
The above display commands only affect the BrainPad's display's memory/buffer, and must be 'committed' to the display by running the method BrainPad.Display.ShowOnScreen().

The display methods below have the ShowOnScreen() method built in and don't require the use of BrainPad.Display.ShowOnScreen(). Keep in mind though that these methods also clear the entire screen before displaying new text. The following commands run 3 methods consecutively: BrainPad.Display.ClearScreen(), BrainPad.Display.Draw..., and finally BrainPad.Display.ShowOnScreen().  
 
* BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, long number) - Clears the screen, draws a number of type long at the given x and y coordinates, and displays the number on the BrainPad display.

* BrainPad.Display.DrawNumberAndShowOnScreen(int x, int y, double number) - Clears the screen, draws a number of type double at the given x and y coordinates, and displays the number on the BrainPad display.

* BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, long number) - Clears the screen, draws a number of type long at the given x and y coordinates in small text, and displays the number on the BrainPad display.

* BrainPad.Display.DrawSmallNumberAndShowOnScreen(int x, int y, double number) - Clears the screen, draws a number of type double at the given x and y coordinates in small text, and displays the number on the BrainPad display.

* BrainPad.Display.DrawTextAndShowOnScreen(int x, int y, string text) - Clears the screen, draws a number of string at the given x and y coordinates, and displays the number on the BrainPad display.    

* BrainPad.Display.DrawSmallTextAndShowOnScreen(int x, int y, string text) - Clears the screen, draws a string at the given x and y coordinates in small text, and displays the number on the BrainPad display.    

* BrainPad.Display.DrawScaledTextAndShowOnScreen(int x, int y, string text, int HScale, int VScale) - Clears the screen, draws a string at the given x and y coordinates in scaled text, and displays the number on the BrainPad display.    