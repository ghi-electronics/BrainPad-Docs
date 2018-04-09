# Pong

The classic pong game, the godfather of all games!

Difficulty: Easy
Objective: Gaming, Retro

# How It Works
Suprisingly, this very simple game requires about as much code is the [Space Invasion](space-invasion.md). It all starts with the ball that needs to bounce off walls and the player sticks. When teh ball bounce off the left or right walls, a score is increased for one of the players. Once the score reaches 5, you become a winner or a loser as the game is plaied vs. the computer.

# An Exercise

Modify the code to so tilt (the accelerometer) is used instread of buttons. Hint: Use the [Tilt Ech A Sketch](tilt-etch-a-sketch.md) for ideas.

# The Code
```
using System;
using System.Collections;
using System.Text;
using System.Threading;
using GHIElectronics.TinyCLR.BrainPad;

namespace Pong {
    class Program {
        static void Main() {
            double BallX = 10, BallY = 10, BallDX = 2.3, BallDY = 2.8;
            int ScoreL = 0, ScoreR = 0;
            int PlayerPos=30;
            int CompPros = 30;
            BrainPad.Display.DrawRectangle(0, 0, 128, 64);
            while (true) {
                // The Ball
                BrainPad.Display.ClearPartOfScreen((int)BallX, (int)BallY, 4, 4);
                BallX += BallDX;
                BallY += BallDY;
                if (BallX < 10 ) {
                    BallDX *= -1;
                    if (BallY >= CompPros - 1 && BallY <= CompPros + 12) {
                        // hit back
                        BrainPad.Buzzer.Beep();
                    }
                    else {
                        //win
                        for (int i = 0; i < 3; i++) {
                            for (int f = 1000; f < 6000; f += 500) {
                                BrainPad.Buzzer.StartBuzzing(f);
                                BrainPad.Wait.Minimum();
                            }
                        }
                        ScoreR++;
                        BrainPad.Buzzer.StopBuzzing();
                        BrainPad.Wait.Seconds(0.5);
                    }
                }
                if (BallX > 115) {
                    BallDX *= -1;
                    if (BallY >= PlayerPos-1 && BallY <= PlayerPos + 12) {
                        // hit back
                        BrainPad.Buzzer.Beep();
                    }
                    else {
                        // Loss
                        for (int f = 2000; f > 200; f -= 200) {
                            BrainPad.Buzzer.StartBuzzing(f);
                            BrainPad.Wait.Minimum();
                        }
                        ScoreL++;
                        BrainPad.Wait.Seconds(0.5);
                        BrainPad.Buzzer.StopBuzzing();
                    }
                }
                if (BallY < 5 || BallY > 55) {
                    BallDY *= -1;
                    BrainPad.Buzzer.Beep();
                }
                BrainPad.Display.DrawFilledRectangle((int)BallX, (int)BallY, 4, 4);
                // The Field
                for (var y = 0; y < 64; y += 10) {
                    // net
                    BrainPad.Display.DrawLine(64, y, 64, y + 5);
                }
                // Player
                BrainPad.Display.ClearPartOfScreen(120, PlayerPos, 2, 10);
                if (BrainPad.Buttons.IsUpPressed()) PlayerPos -= 4;
                if (BrainPad.Buttons.IsDownPressed()) PlayerPos += 4;
                if (PlayerPos < 5) PlayerPos = 5;
                if (PlayerPos > 50) PlayerPos = 50;
                BrainPad.Display.DrawFilledRectangle(120, PlayerPos, 2, 10);
                // Computer
                BrainPad.Display.ClearPartOfScreen(10, CompPros, 2, 10);
                if (BallY > CompPros+10) CompPros += 2;
                if (BallY < CompPros) CompPros -= 2;
                if (CompPros < 5) CompPros = 5;
                if (CompPros > 50) CompPros = 50;
                BrainPad.Display.DrawFilledRectangle(10, CompPros, 2, 10);

                // Score
                BrainPad.Display.DrawSmallNumber(50, 5, ScoreL);
                BrainPad.Display.DrawSmallNumber(74, 5, ScoreR);

                if (ScoreL >= 5) {
                    BrainPad.Display.DrawScaledText(0, 40, "You Lose!", 3, 1);
                    BrainPad.Display.ShowOnScreen();
                    BrainPad.Wait.Seconds(-1);
                }
                if (ScoreR >= 5) {
                    BrainPad.Display.DrawScaledText(0, 40, "You Win!", 3, 1);
                    BrainPad.Display.ShowOnScreen();
                    BrainPad.Wait.Seconds(-1);
                }
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