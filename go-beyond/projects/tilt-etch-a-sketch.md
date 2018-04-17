# Tilt Etch A Sketch
---
![Tilt Etch A Sketch](images/tilt-etch-a-sketch.gif)

A BrainPad version of the classic mechanical drawing toy. Simply tilt the screen to show the sketch and press the down button to erase it.

**Difficulty: Easy**

**Objective: Gaming, Drawing**

## How It Works
This program is simple. We draw a circle on the screen and move it when the BrainPad is tilted. We measure the force of the Earth's gravity on the BrainPad's accelerometer to measure how much the BrainPad is tilted.

## The Code

```
using GHIElectronics.TinyCLR.BrainPad;

namespace Etch_A_Sketch {
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
                BrainPad.Display.ShowOnScreen();

                if (BrainPad.Buttons.IsDownPressed())
                    BrainPad.Display.ClearPartOfScreen(0, 0, 128, 55);

                BrainPad.Wait.Minimum();

                BrainPad.Display.DrawPoint(x, y);
                BrainPad.Display.ShowOnScreen();
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