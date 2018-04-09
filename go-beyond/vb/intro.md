# Introduction to Visual Basic
---
Visual Basic is a very popular Microsoft .NET programming language. While being as powerful as other programming languages, it is perhaps a little easier for beginners.  Visual Basic is more like plain English than other programming languages, and you don't have to type a semicolon (;) at the end of each line like you do with C, C++, and C#.  

> [!Tip]
> Before you start you should have already gone through the [System Setup](../system-setup.md).  If not, do so before proceeding.

## Before you start

You should have already installed Visual Studio on your computer as well as the TinyCLR extension.  If not, please start with [System Setup](../system-setup.md) for instructions on how to do so.

Also, you need a BrainPad and a micro USB cable to continue.  Plug the BrainPad into the USB port of your computer.  The red power light on the BrainPad should be on.

## Hello World

The first step is to write some very simple code to see if the BrainPad will respond when we try to program it.  This is usually called a "hello world" program.

### Start a New Project
Open Visual Studio.  In the `File` menu select `New` and then `Project` to open the "New Project" dialog box.

![Start New Visual Studio Project](../csharp/images/introduction/start-new-project.png)

In the left panel of the  `New Project` window you can click on the small triangles to the left of each heading to expand the heading and show the options beneath it.

You should see the `Visual Basic` language listed under the "Installed" heading in the left panel of the "New Project" window.

Under "Visual Basic" select the "TinyCLR" option.

In the center panel of the "New Project" window select "BrainPad Application".

At the bottom of the "New Project" window you can change the name and location of your application or just stick with the default.  When starting out you may wish to click on the `Browse` button and select the folder "Desktop" (in the left panel) to make your application easier to find.

Click the `OK` button on the bottom right of the "New Project" window.  This will create a new blank project.

![Start New Project](images/introduction/new-project-window.png)

Once created, you'll be presented with a `Program.vb` tab.

![First Project](images/introduction/first-project.png)

### Add the Code  
In the `Program.vb` tab we will enter short sample program (our "Hello World" code). Cut and paste the following code into the `Program.vb` window.

```
Class Program
    Public Sub Main()
        BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")

        While True
            BrainPad.LightBulb.TurnWhite()
            BrainPad.Wait.Seconds(1)
            BrainPad.LightBulb.TurnOff()
            BrainPad.Wait.Seconds(1)
        End While
    End Sub
End Class

Public Class BrainPad
    Public Shared ReadOnly Property Accelerometer As Accelerometer = New Accelerometer()
    Public Shared ReadOnly Property Buttons As Buttons = New Buttons()
    Public Shared ReadOnly Property Buzzer As Buzzer = New Buzzer()
    Public Shared ReadOnly Property Display As Display = New Display()
    Public Shared ReadOnly Property LightBulb As LightBulb = New LightBulb()
    Public Shared ReadOnly Property LightSensor As LightSensor = New LightSensor()
    Public Shared ReadOnly Property ServoMotors As ServoMotors = New ServoMotors()
    Public Shared ReadOnly Property TemperatureSensor As TemperatureSensor = New TemperatureSensor()
    Public Shared ReadOnly Property Wait As Wait = New Wait()
End Class
```

### Deploy the Program

Let's run the program now to see the code come to life. If your BrainPad is not connected to your computer with a micro USB cable connect it now. Press the `F5` function key or the `Start` button (shown below) to copy the program from your computer to your BrainPad.

![Start Button](../csharp/images/introduction/start-button.png)

Visual Studio will now tell your BrainPad to run the code.  A few things will happen and the display will now show the text "Hello!" and the light bulb (or LED) will blink.

What happened exactly? Our application began by running the `BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")` line to instruct the display to show the text "Hello!"

The line `BrainPad.Display.DrawTextAndShowOnScreen(0, 0, "Hello!")` is known as a function call.  The name of the function is "DrawTextAndShowOnScreen()."  This function is part of the "Display" object, which is part of the "BrainPad" object.

The items listed in parenthesis (0, 0, "Hello!") are called the arguments of the function.  In this case the first zero tells the BrainPad to display the text at the left side of the BrainPad display.  If this number is increased the text will appear further to the right of the screen.  The second zero tells the BrainPad to print the text at the top of the display.  If this number is increased the text will be printed lower on the screen.  The third arugument, "Hello!," tells the BrainPad what text to display on the screen.

After `BrainPadSetup()` is finished, the `While True` loop starts running. Code placed inside this while loop is executed in an infinite loop. This is why the code that turns the LED on and then off never stops.
