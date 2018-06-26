# Tilt Etch A Sketch
---
![Tilt Etch A Sketch](images/tilt-etch-a-sketch.gif)

A BrainPad version of the classic mechanical drawing toy. Simply tilt the screen to show the sketch and press the down button to erase it.

**Difficulty: Easy.**

**Objective: Gaming, Drawing.**

## How It Works
This program is simple. We draw a point on the screen and move it when the BrainPad is tilted. We measure the force of the Earth's gravity on the BrainPad's accelerometer to measure how much and in which direction the BrainPad is tilted.

## The Code in C#
> [!Tip]
> Make sure the namespace in your program matches your project's namespace.  Your project's namespace can be found in the BrainPad Helper file by clicking on the BrainPad1.cs tab.  [**More Info**](../go-beyond/csharp/intro.md#a-few-words-about-namespaces).

```
using GHIElectronics.TinyCLR.BrainPad;

namespace ModifyThis {
    class Program {
        static void Main() {
            BrainPad.Display.DrawSmallText(0, 57, "Tilt: Draw - D: Erase");
            BrainPad.Display.DrawLine(0, 55, 127, 55);
            int x = 64, y = 32;
            const double ACC_TOLERANCE = .20;

            while (true) {
                if (BrainPad.Accelerometer.ReadY() > -ACC_TOLERANCE) y--;
                if (BrainPad.Accelerometer.ReadY() < ACC_TOLERANCE) y++;
                if (BrainPad.Accelerometer.ReadX() > ACC_TOLERANCE) x++;
                if (BrainPad.Accelerometer.ReadX() < -ACC_TOLERANCE) x--;

                if (x < 0) x = 0;
                if (y < 0) y = 0;
                if (x > 127) x = 127;
                if (y > 50) y = 50;

                BrainPad.Display.ClearPoint(x, y);
                BrainPad.Display.RefreshScreen();

                if (BrainPad.Buttons.IsDownPressed())
                    BrainPad.Display.ClearPart(0, 0, 128, 55);

                BrainPad.Wait.Minimum();

                BrainPad.Display.DrawPoint(x, y);
                BrainPad.Display.RefreshScreen();
            }
        }
    }
}

```