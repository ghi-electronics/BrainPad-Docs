# Tilt Etch A Sketch
This classic game now works on the BrainPad. Simply tilt the screen to show the sketch and press down to erase it.

Difficulty: Easy
Objective: Gaming, Drawing

# How It Works
Very simply, we draw a circle on the screen. The circle moves when we tilt the BrainPad by checking the accelerometer. Acceleration is basically the earth gravity.

# The Code

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
                if (BrainPad.Accelerometer.ReadY() > ACC_TOLERANCE) y--;
                if (BrainPad.Accelerometer.ReadY() < ACC_TOLERANCE * -1) y++;
                if (BrainPad.Accelerometer.ReadX() > ACC_TOLERANCE) x++;
                if (BrainPad.Accelerometer.ReadX() < ACC_TOLERANCE * -1) x--;
                if (x < 0) x = 0;
                if (y < 0) y = 0;
                if (x > 127) x = 127;
                if (y > 50) y = 50;
                BrainPad.Display.DrawCircle(x, y, 1);

                if (BrainPad.Buttons.IsDownPressed())
                    BrainPad.Display.ClearPartOfScreen(0, 0, 128, 55);

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