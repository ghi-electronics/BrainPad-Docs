# Etch A Sketch
---
This classic game now works on the BrainPad. Simply use the buttons to sketch.

**Difficulty: Easy.**

**Objective: Gaming, Drawing.**

## How It Works
This program is simple. We draw a point on the screen and move it when the buttons are pressed.

## The Code
> [!Tip]
> Make sure the namespace in your program matches your project's namespace.  Your project's namespace can be found in the BrainPad Helper file by clicking on the BrainPad1.cs tab.  [**More Info**](../csharp/intro.md#a-few-words-about-namespaces).

```
using GHIElectronics.TinyCLR.BrainPad;

namespace ModifyThis {
    class Program {
        static void Main() {
            BrainPad.Display.DrawSmallText(0, 57, "Use Buttons to Draw");
            BrainPad.Display.DrawLine(0, 55, 127, 55);
            int x = 64, y = 32;

            while (true) {
                if (BrainPad.Buttons.IsDownPressed()) y++;
                if (BrainPad.Buttons.IsUpPressed()) y--;
                if (BrainPad.Buttons.IsLeftPressed()) x--;
                if (BrainPad.Buttons.IsRightPressed()) x++;

                if (x < 0) x = 0;
                if (y < 0) y = 0;
                if (x > 127) x = 127;
                if (y > 50) y = 50;

                BrainPad.Display.ClearPoint(x, y);
                BrainPad.Display.RefreshScreen();
                BrainPad.Wait.Minimum();

                BrainPad.Display.DrawPoint(x, y);
                BrainPad.Display.RefreshScreen();
            }
        }
    }
}
```