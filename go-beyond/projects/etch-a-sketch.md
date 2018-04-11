# Etch A Sketch
---
This classic game now works on the BrainPad. Simply use the buttons to sketch.

**Difficulty: Easy**

**Objective: Gaming, Drawing**

## How It Works
This program is simple. We draw a circle on the screen and move it when the buttons are pressed.

## The Code

```
using GHIElectronics.TinyCLR.BrainPad;

namespace Etch_A_Sketch {
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
                
                BrainPad.Display.DrawCircle(x, y, 1);
                BrainPad.Display.ShowOnScreen();
                BrainPad.Wait.Minimum();
            }
        }
    }

    public static class BrainPad {
        public static Accelerometer Accelerometer { get; } = new Accelerometer();
        public static Buttons Buttons { get; } = new Buttons();
        public static Buzzer Buzzer { get; } = new Buzzer();
        public static Display Display { get; } = new Display();
        public static LightBulb LightBulb { get; } = new LightBulb();
        public static LightSensor LightSensor { get; } = new LightSensor();
        public static ServoMotors ServoMotors { get; } = new ServoMotors();
        public static TemperatureSensor TemperatureSensor { get; } = new TemperatureSensor();
        public static Wait Wait { get; } = new Wait();
    }
}
```