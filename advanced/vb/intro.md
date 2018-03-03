# Introduction to Visual Basic on the BrainPad

---

Visual Basic is a very popular Microsoft .NET programming language. While being as powerful as other programming languages, it is perhaps a little easier to start with.  Visual Basic is more like plain English than other programming languages, for example, and you don't have to type a semicolon (;) at the end of each line like you do with C, C++, and C#.  

---

## Before you start

You should have already installed Visual Studio on your computer as well as the TinyCLR extension.  If not, please go to [Using Visual Studio with the BrainPad](../visualstudio.md) for instructions on how to do so.

Also, you need a BrainPad and a micro USB cable to continue.  Plug the BrainPad into the USB port of your computer.  The red power light on the BrainPad should be on.

## Hello World

The first step is to write some very simple code to see if the BrainPad will respond when we try to program it.  This is usually called a "hello world" program.  This program has already been written and is installed on Visual Studio.  It was installed when you loaded the TinyCLR extension.

Open Visual Studio.  In the `File` menu select `New` and then `Project` to open the "New Project" dialog box.

![Start New Visual Studio Project](../csharp/images/introduction/StartNewProject.PNG)

In the left panel of the  "New Project" window you can click on the small triangles to the left of each heading to expand the heading and show the options beneath it.

You should see the "Visual Basic" language listed under the "Installed" heading in the left panel of the "New Project" window.

Under "Visual Basic" select the "TinyCLR" option.

In the center panel of the "New Project" window select "BrainPad Application".

At the bottom of the "New Project" window you can change the name and location of your application or just stick with the default.  When starting out you may wish to click on the `Browse` button and select the folder "Desktop" (in the left panel) to make your application easier to find.

Click the `OK` button on the bottom right of the "New Project" window.  This will create a new project with some sample code to get you started.

![Start New Visual C# Project](images/introduction/NewProjectWindow.PNG)

Once created, you'll be presented with a `Program.vb` tab.

![First C# Project](images/introduction/FirstProject.PNG)  

In the `Program.vb` tab you should see a short sample program (our "Hello World" code).  This program is automatically loaded when you first create a new project. The lines in green that begin with an apostrophe (`'`) are called comments, and they generally describe what the code does. Take a moment to review them.

You can create your own comments in a Visual Basic program by typing `'` before any comments you want to add. Comments have absolutely no effect on the program or how it runs.  Comments do absolutely nothing and are ignored by the BrainPad.

So why use comments?  Comments are used to make notes about how a piece of code works. They are very helpful when you go back to your program at a later date to modify it, add to it, or fix it.  They are also helpful if another programmer wants to understand or modify your code.  While adding comments takes longer intitially, you more than make up for the time spent when you have to maintain your code later -- especially for lengthy or complex programs.

Let's run the program now to see the code come to life. Connect the BrainPad and press the `F5` function key or the 'Start' button (shown below).

![Start Button](../csharp/images/introduction/StartButton.PNG)

Visual Studio will now tell your BrainPad to run the code.  A few things will happen and the display will now show the text "Hello!" and the light bulb (or LED) will blink.

What happened exactly? Our application began by running the `BrainPadSetup()` function. This function is runs one time, when the application starts, and is used to set things up. In this case, it executed the `BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")` line to instruct the display to show the text "Hello."

The line `BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")` is known as a function call.  The name of the funtion is "DrawTextAndShowOnScreen()."  This function is part of the "Display" object, which is part of the "BrainPad" object.

The items listed in parenthesis (0, 0, "Hello!") are called the arguments of the function.  In this case the first zero tells the BrainPad to display the text at the left side of the BrainPad display.  If this number is increased the text will appear further to the right of the screen.  The second zero tells the BrainPad to print the text at the top of the display.  If this number is increased the text will be printed lower on the screen.  The third arugument, "Hello!," tells the BrainPad what text to display on the screen.

After `BrainPadSetup()` is finished, the application calls `BrainPadLoop()`. Code placed inside this function is executed in an infinite loop. This is why the code that turns the LED on and then off again and never stops.

## Making changes to the code

Let's try changing the program to print your first name on the display.

After deploying the "hello world" program to the BrainPad, Visual Studio is in "debug mode."  We'll learn more about debug mode later, but for now you need to know that you cannot edit code while in debug mode.  To stop debug mode, hit the `Stop` button (as shown below) or hit `Shift` `F5`.

![Stop debugging](../csharp/images/introduction/StopDebugging.PNG)

If you try to edit code and see the message "Managed Compatibility Mode does not support Edit and Continue," you are trying to edit code while in debug mode.  Just stop debug mode (`Stop` button or `Shift` `F5`) and you can edit your program.

![Error trying to edit in debug mode](../csharp/images/introduction/EditDuringDebugError.PNG)

Use the mouse to place the cursor after the exclamation point in the `BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")` function call (as shown below).  This should be in line 5 of the program (line numbers are listed near the left edge of the program).

![Place cursor after hello](images/introduction/PlaceCursorAfterHello.PNG)

Use the `Backspace` key to erase "Hello!" and type in your first name.  Run the program by hitting the `F5` key.  The display on the BrainPad should now display your first name on the BrainPad.

Can you make the BrainPad display your name near the center of the screen?

## Changing the Light Bulb Code

> [!Tip]
> You may be confused by the use of "light bulb" (2 words) and LightBulb (1 word).  Light bulb (2 words) is correct English.  LightBulb (1 word) is a BrainPad object.  Object names in a program cannot contain spaces.  You will often find that object names and other names in a program cannot be written as proper English because of the rules of the programming language you are using.

Let's try to change the way the light bulb flashes.  We're going to add two lines of code to the end of the program:

```
BrainPad.LightBulb.TurnBlue()
BrainPad.Wait.Seconds(1)
```

Exit debug mode by hitting the `Stop` button with the mouse or by pressing `Shift` `F5`.

Now place the cursor after the last line of code (`BrainPad.Wait.Seconds(1);`) by pointing and clicking with the mouse as shown below.

![Place cursor after last line](images/introduction/PlaceCursor.PNG)

Now hit the `Enter` key.  This will move the cursor past the last line of the program and create a blank line where you can start typing your code.

Now type a "b" for BrainPad.  You will see a drop down box with a list of objects beginning with the letter "b."  You may have to type "br" to see BrainPad listed.

You can keep typing the word "BrainPad," but the easiest way to complete the word is to hit the period key(`.`).  This will complete typing the word "BrainPad" and place a period after it.  You can also use the mouse to select "BrainPad" from the list, or hit the `Space Bar` or `Enter` key.  You can also use the arrow keys to move up and down the list.  After "BrainPad." another small window with a list of objects that are part of the BrainPad object will appear.  Now start typing the word "lightbulb."  Another drop down list will appear.  Select "LightBulb" from the list.

![IntelliSense BrainPad](images/introduction/BrainPadIntelliSense.PNG)

Visual Studio's ability to provide a list of words to complete your code is called "IntelliSense."  IntelliSense makes it easier for programmers to enter code and to know which objects are part of the preceeding object.  Make your code look like the code in the picture below.

![Blinking blue light code](images/introduction/BlueLightBlinkCode.PNG)

When your code looks like the above example, hit the `F5` key to load the program into the BrainPad and run it.  The light bulb should follow the pattern:  White for 1 second, off for 1 second, blue for 1 second and repeat.  There is no delay between the end of the blue blink and the start of the white blink.  Do you know why?

Make sure you understand how this code works.  Feel free to alter the code with different color light bulb blinks for different durations.

```
LightBulb colors:
TurnBlue()
TurnGreen()
TurnRed()
TurnWhite()
```

Can you make to BrainPad light bulb flash like a police car?

## Slowing Down a Program
 
Copy and paste the code from Example 1 below into your project's 'BrainPadLoop()'.  It should look like the screen shot below the sample code.  If you select the old code before pasting the new code, you can erase the old program at the same time you put in the new one.

Example 1:
```
BrainPad.LightBulb.TurnGreen()
BrainPad.LightBulb.TurnOff()
BrainPad.LightBulb.TurnGreen()
BrainPad.LightBulb.TurnOff()
```

![Green Off Green Off Sample](images/introduction/GreenOffGreenOffSampleCode.PNG)

Now, press `F5` to run the code.  You should see the light bulb turn green and stay on. This happens because our code is executing faster than we can see. We never see the light bulb actually blink.  If you shake the BrainPad while looking at the green light you can see that it is actually blinking very rapidly.

Since applications run so quickly, slowing them down can help us solve problems in the program. Slowing down a program can help us see what is happening and see if the code performs as expected.  Visual Studio allows us to run code one line at a time.  This is called stepping through the code and allows us to see what the application is doing one instruction at a time.

## Stepping Through Code
First, if the debugger is running stop it by pressing the `Stop` button, hitting `Shift` `F5`, or selecting `Stop Debugging` in the `Debug` menu.

Add a breakpoint (stop point) at the first line of code inside of `BrainPadLoop()` by clicking on that line with the mouse and pressing the `F9` key as shown below.

You can also click in the grey area where the breakpoints appear (at the left edge of the window) to either remove or create new breakpoints. 

![Adding a Breakpoint](images/introduction/AddingBreakPoint.PNG)

Press `F5` to run the application. The project will be built and deployed but then the execution will stop at the breakpoint as shown below.

![Stopping at the Breakpoint](images/introduction/StopBreakPoint.PNG)

Now hit the `F10` key to step through the code one instruction at a time.  You can follow the program on the screen and watch the BrainPad light bulb turn green and turn off repeatedly as you hit the `F10` key.  Single stepping through a program is a very helpful way to see what is happening inside a program and is often used to fix problems within a program.

## Adding Delays to Code

Another way to see what's happening inside a program is to add delays between the instructions.

Copy and paste the code below into your project's `BrainPadLoop()`. 

Example 2:
```
BrainPad.LightBulb.TurnGreen()
BrainPad.Wait.Seconds(1)
BrainPad.LightBulb.TurnOff()
BrainPad.Wait.Seconds(1)
BrainPad.LightBulb.TurnGreen()
BrainPad.Wait.Seconds(1)
BrainPad.LightBulb.TurnOff()
BrainPad.Wait.Seconds(1)
```

Your code should look like the screen shot below:

![Delay Example Code](images/introduction/DelayExampleCode.PNG)

This program is the same as the previous program (Example 1) except a delay of one second is added after each instruction.  Run the code by pressing `START` and observe the light bulb again. It should now blink green much more slowly than before.

## More Light Bulb Colors

You may have noticed that in addition to the light bulb functions that turns the LED blue, green, red, white and off, there is a function called "TurnColor()" which is part of the LightBulb object.  The TurnColor() function takes three arguments which describe the color of the light bulb.  The first argument tells the light bulb how much red to use, the second how much green, and the third how much blue.  Each number is a percentage, or a number from 0 to 100 with 0 being off and 100 being full brightness.

The code in the Example 3 shows how this function is used.  Copy the code and paste it into `BrainPadLoop()`.  Now run the code.

The light bulb should cycle through colors starting at red, ending at white, and then repeating.  The light bulb should also get progessively brighter with red being the dimmest color and white being the brightest.  Also, the name of each color should appear on the BrainPad display.  The color names should start a the top of the screen and move down the screen.

Study the code to figure out how it works.  Feel free to modify the code to experiment with the light bulb and the display.

Example 3:
```
BrainPad.Display.DrawTextAndShowOnScreen(45, 0, "Red")
BrainPad.LightBulb.TurnColor(1, 0, 0)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(35, 8, "Green")
BrainPad.LightBulb.TurnColor(0, 2, 0)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(40, 16, "Blue")
BrainPad.LightBulb.TurnColor(0, 0, 5)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(29, 24, "Yellow")
BrainPad.LightBulb.TurnColor(10, 10, 0)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(41, 32, "Cyan")
BrainPad.LightBulb.TurnColor(0, 20, 20)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(25, 40, "Magenta")
BrainPad.LightBulb.TurnColor(50, 0, 50)
BrainPad.Wait.Seconds(2)

BrainPad.Display.DrawTextAndShowOnScreen(37, 48, "White")
BrainPad.LightBulb.TurnColor(100, 100, 100)
BrainPad.Wait.Seconds(2)
```

