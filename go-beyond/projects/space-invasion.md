# Space Invasion
---
![Space Invasion](images/space-invasion.jpg)

Difficulty: Medium
Objective: Gaming, Retro

---

This game was inspired by the Space Invaders game from the 80s. It is fun to play and easy to program.

Start a C# TinyCLR Application project. You can also use VB if you want to convert the code from [C# to VB](../vb/csharp-to-vb.md).

## The Ship
When you finish this section, you will have a ship on the screen that can be moved using the left and right buttons.

### The Main Loop
In our project, we need to have a loop where we process the different things we have moving on screen, like the ship.

Once everything is processed, we can `ShowOnScreen`. As always, we need to add a minimum delay to give the system time to proccess any other internal tasks.

```
static void Main() {
            
    while(true) {
        ProcessShip();
        BrainPad.Display.ShowOnScreen();
        BrainPad.Wait.Minimum();
    }
}
```

We also want to add two lines defining the play area
```
static void Main() {
    BrainPad.Display.DrawLine(90, 0, 90, 64);
    BrainPad.Display.DrawLine(0, 0, 0, 64);
    while (true) {
        ProcessShip();
        BrainPad.Display.ShowOnScreen();
        BrainPad.Wait.Minimum();
    }
}
```

### Sprites
In computer programming sprites are small pictures or objects that are shown on the screen and can be moved or manipulated as a single entity. In this game the space ship, the bullets, and the monster are all sprites. We will create a `sprite` class which will be used to keep track of each sprite's position and size. This class will also provide methods to and draw it and erase it.

```
class Sprite {
    Picture Pic;
    public int X, Y;
    public int Width = 8;
    public int Height = 5;
    public Sprite(Picture p) {
        Pic = p;
        Width = p.Width;
        Height = p.Height;
    }
    public void Clear() {
        BrainPad.Display.ClearPartOfScreen(X, Y, Pic.Width, Pic.Height);
    }
    public void Draw() {
        BrainPad.Display.DrawPicture(X, Y, Pic);
    }
}
```

### Creating The Ship
Let's use the Sprite class we made in the last step to create the Ship.

```
static Sprite Ship = new Sprite(BrainPad.Display.CreatePicture(8, 5, new byte[] {
0,0,0,1,1,0,0,0,
0,0,0,1,1,0,0,0,
0,1,1,1,1,1,1,0,
1,1,1,1,1,1,1,1,
1,0,0,0,0,0,0,1,
})) { Y = 64 - 5 , X = 50};
```

### Moving The Ship
The ship will always be at the bottom of the screen. Its Y location never changes. It's Y (vertical) position was set at the display max height (64) minus the ship height (5) when we created it.

We now need to check the buttons and update the ship's X (horizontal) position. We also check the X position to make sure the ship stays within the playing area.

```
static void ProcessShip() {
    Ship.Clear();
    if (BrainPad.Buttons.IsLeftPressed())
        Ship.X -= 5;
    if (BrainPad.Buttons.IsRightPressed())
        Ship.X += 5;
    if (Ship.X < 5) Ship.X = 5;
    if (Ship.X > 85 - Ship.Width) Ship.X = 85 - Ship.Width;
    Ship.Draw();
}
```

### Testing The Ship

Time to load the code and test it out. Here is the complete code.

```
using GHIElectronics.TinyCLR.BrainPad;
namespace SpaceInvasion {
    class Sprite {
        Picture Pic;
        public int X, Y;
        public int Width = 8;
        public int Height = 5;
        public Sprite(Picture p) {
            Pic = p;
            Width = p.Width;
            Height = p.Height;
        }
        public void Clear() {
            BrainPad.Display.ClearPartOfScreen(X, Y, Pic.Width, Pic.Height);
        }
        public void Draw() {
            BrainPad.Display.DrawPicture(X, Y, Pic);
        }
    }
    class Program {
        static Sprite Ship = new Sprite(BrainPad.Display.CreatePicture(8, 5, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,0,1,1,0,0,0,
            0,1,1,1,1,1,1,0,
            1,1,1,1,1,1,1,1,
            1,0,0,0,0,0,0,1,
            })) { Y = 64 - 5 , X = 50};
        static void ProcessShip() {
            Ship.Clear();
            if (BrainPad.Buttons.IsLeftPressed())
                Ship.X -= 5;
            if (BrainPad.Buttons.IsRightPressed())
                Ship.X += 5;
            if (Ship.X < 5) Ship.X = 5;
            if (Ship.X > 85 - Ship.Width) Ship.X = 85 - Ship.Width;
            Ship.Draw();
        }
        
    static void Main() {
    BrainPad.Display.DrawLine(90, 0, 90, 64);
    BrainPad.Display.DrawLine(0, 0, 0, 64);
    while (true) {
        ProcessShip();
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

## The Bullet
This section will add a bullet that shoots when the up button is pressed. A sound is added after.

### Creating The Bullet
The bullet will start at -10, outside the screeen. This way the player will not see it and it is also an indication to our code to not process it

```
static Sprite Bullet = new Sprite(BrainPad.Display.CreatePicture(2, 2, new byte[] {
    1,1,
    1,1,
    })) { Y = - 10 };
```

### Moving The Bullet
The bullet will always start at the middle of the ship and will go up untill it is outside the screen.

To generate a shooting sound, we somewhat cheat and use the Y location to calculate a sweeping frequency!

```
static void ProcessBullet() {
    if (Bullet.Y > - 5) {
        Bullet.Clear();
        Bullet.Y -= 5;
        Bullet.Draw();
        BrainPad.Buzzer.StartBuzzing(3000 - Bullet.Y * 30);
        }
    else {
        BrainPad.Buzzer.StopBuzzing();
        if (BrainPad.Buttons.IsUpPressed()) {
            Bullet.X = Ship.X + Ship.Width / 2;
            Bullet.Y = 55;
                    
        }
    }
}
```
### Testing The Bullet

This is the complete code. Things are getting more exciting!

```
using GHIElectronics.TinyCLR.BrainPad;
namespace SpaceInvasion {
    class Sprite {
        Picture Pic;
        public int X, Y;
        public int Width = 8;
        public int Height = 5;
        public Sprite(Picture p) {
            Pic = p;
            Width = p.Width;
            Height = p.Height;
        }
        public void Clear() {
            BrainPad.Display.ClearPartOfScreen(X, Y, Pic.Width, Pic.Height);
        }
        public void Draw() {
            BrainPad.Display.DrawPicture(X, Y, Pic);
        }
    }
    class Program {
        static Sprite Ship = new Sprite(BrainPad.Display.CreatePicture(8, 5, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,0,1,1,0,0,0,
            0,1,1,1,1,1,1,0,
            1,1,1,1,1,1,1,1,
            1,0,0,0,0,0,0,1,
            })) { Y = 64 - 5 , X = 50};
        static Sprite Bullet = new Sprite(BrainPad.Display.CreatePicture(2, 2, new byte[] {
            1,1,
            1,1,
            })) { Y = - 10 };
        static void ProcessBullet() {
            if (Bullet.Y > - 5) {
                Bullet.Clear();
                Bullet.Y -= 5;
                Bullet.Draw();
                BrainPad.Buzzer.StartBuzzing(3000 - Bullet.Y * 30);
             }
            else {
                BrainPad.Buzzer.StopBuzzing();
                if (BrainPad.Buttons.IsUpPressed()) {
                    Bullet.X = Ship.X + Ship.Width / 2;
                    Bullet.Y = 55;
                    
                }
            }
        }
        static void ProcessShip() {
            Ship.Clear();
            if (BrainPad.Buttons.IsLeftPressed())
                Ship.X -= 5;
            if (BrainPad.Buttons.IsRightPressed())
                Ship.X += 5;
            if (Ship.X < 5) Ship.X = 5;
            if (Ship.X > 85 - Ship.Width) Ship.X = 85 - Ship.Width;
            Ship.Draw();
        }
        static void Main() {
            BrainPad.Display.DrawLine(90, 0, 90, 64);
            BrainPad.Display.DrawLine(0, 0, 0, 64);
            while (true) {
                ProcessShip();
                ProcessBullet();
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


## The Monster
The monster (invador) simply goes left and right on the screen, while lowering closer and closer to our ship.

### Creating The Monster
```
static Sprite Monster = new Sprite(BrainPad.Display.CreatePicture(8, 8, new byte[] {
    0,0,0,1,1,0,0,0,
    0,0,1,1,1,1,0,0,
    0,1,1,1,1,1,1,0,
    1,1,0,1,1,0,1,1,
    1,1,1,1,1,1,1,1,
    0,0,1,0,0,1,0,0,
    0,1,0,1,1,0,1,0,
    1,0,1,0,0,1,0,1,
    })) { X = 41 };
```
### Moving The Monster
```
static int MonsterDelta = 5;
static void ProcessMonster() {
    Monster.Clear();
    Monster.X += MonsterDelta;
    if (Monster.X < 5 || Monster.X > 85-Monster.Width) {
        MonsterDelta *= -1;// Reverse
        Monster.Y += 10;
    }
    Monster.Draw();
}
```
### Testing The Monster
The monster will move down and go out of view. We do not process collisions yet. You can reset the board to see the monster again!

```
using GHIElectronics.TinyCLR.BrainPad;
namespace SpaceInvasion {
    class Sprite {
        Picture Pic;
        public int X, Y;
        public int Width = 8;
        public int Height = 5;
        public Sprite(Picture p) {
            Pic = p;
            Width = p.Width;
            Height = p.Height;
        }
        public void Clear() {
            BrainPad.Display.ClearPartOfScreen(X, Y, Pic.Width, Pic.Height);
        }
        public void Draw() {
            BrainPad.Display.DrawPicture(X, Y, Pic);
        }
    }
    class Program {
        static Sprite Ship = new Sprite(BrainPad.Display.CreatePicture(8, 5, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,0,1,1,0,0,0,
            0,1,1,1,1,1,1,0,
            1,1,1,1,1,1,1,1,
            1,0,0,0,0,0,0,1,
            })) { Y = 64 - 5 , X = 50};
        static Sprite Bullet = new Sprite(BrainPad.Display.CreatePicture(2, 2, new byte[] {
            1,1,
            1,1,
            })) { Y = - 10 };
        static Sprite Monster = new Sprite(BrainPad.Display.CreatePicture(8, 8, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,1,1,1,1,0,0,
            0,1,1,1,1,1,1,0,
            1,1,0,1,1,0,1,1,
            1,1,1,1,1,1,1,1,
            0,0,1,0,0,1,0,0,
            0,1,0,1,1,0,1,0,
            1,0,1,0,0,1,0,1,
            })) { X = 41 };
        static void ProcessBullet() {
            if (Bullet.Y > - 5) {
                Bullet.Clear();
                Bullet.Y -= 5;
                Bullet.Draw();
                BrainPad.Buzzer.StartBuzzing(3000 - Bullet.Y * 30);
             }
            else {
                BrainPad.Buzzer.StopBuzzing();
                if (BrainPad.Buttons.IsUpPressed()) {
                    Bullet.X = Ship.X + Ship.Width / 2;
                    Bullet.Y = 55;
                    
                }
            }
        }
        static void ProcessShip() {
            Ship.Clear();
            if (BrainPad.Buttons.IsLeftPressed())
                Ship.X -= 5;
            if (BrainPad.Buttons.IsRightPressed())
                Ship.X += 5;
            if (Ship.X < 5) Ship.X = 5;
            if (Ship.X > 85 - Ship.Width) Ship.X = 85 - Ship.Width;
            Ship.Draw();
        }
        static int MonsterDelta = 5;
        static void ProcessMonster() {
            Monster.Clear();
            Monster.X += MonsterDelta;
            if (Monster.X < 5 || Monster.X > 85-Monster.Width) {
                MonsterDelta *= -1;// Reverse
                Monster.Y += 10;
            }
            Monster.Draw();
        }
        static void Main() {
            BrainPad.Display.DrawLine(90, 0, 90, 64);
            BrainPad.Display.DrawLine(0, 0, 0, 64);
            while (true) {
                ProcessShip();
                ProcessBullet();
                ProcessMonster();
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
## Processing Collisions
Finally, we want to see if the bullet has hit our monster. In both cases, we want to play some cool sound effects.
```
if (Bullet.X >= Monster.X && Bullet.X <= Monster.X + Monster.Width &&
            Bullet.Y >= Monster.Y && Bullet.Y <= Monster.Y + Monster.Height) {
    for (int i = 0; i < 3; i++) {
        for (int f = 1000; f < 6000; f += 500) {
            BrainPad.Buzzer.StartBuzzing(f);
            BrainPad.Wait.Minimum();
        }
    }
    BrainPad.Buzzer.StopBuzzing();
    Bullet.Clear();
    Monster.Clear();
    Monster.Y = 0;
    Bullet.Y = -5;
}
```
Or if the monster has hit us!
```
if (Monster.Y > 40) {
    if (Ship.X > Monster.X && Ship.X < Monster.X + Ship.Width) {
        for (int f = 2000; f > 200; f -= 200) {
            BrainPad.Buzzer.StartBuzzing(f);
            BrainPad.Wait.Minimum();
        }
        BrainPad.Wait.Seconds(1);
        BrainPad.Buzzer.StopBuzzing();
        Monster.Clear();
        Monster.Y = 0;       
    }
}
```

## The Complete Project
```
using GHIElectronics.TinyCLR.BrainPad;
namespace SpaceInvasion {
    class Sprite {
        Picture Pic;
        public int X, Y;
        public int Width = 8;
        public int Height = 5;
        public Sprite(Picture p) {
            Pic = p;
            Width = p.Width;
            Height = p.Height;
        }
        public void Clear() {
            BrainPad.Display.ClearPartOfScreen(X, Y, Pic.Width, Pic.Height);
        }
        public void Draw() {
            BrainPad.Display.DrawPicture(X, Y, Pic);
        }
    }
    class Program {
        static Sprite Ship = new Sprite(BrainPad.Display.CreatePicture(8, 5, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,0,1,1,0,0,0,
            0,1,1,1,1,1,1,0,
            1,1,1,1,1,1,1,1,
            1,0,0,0,0,0,0,1,
            })) { Y = 64 - 5 , X = 50};
        static Sprite Bullet = new Sprite(BrainPad.Display.CreatePicture(2, 2, new byte[] {
            1,1,
            1,1,
            })) { Y = - 10 };
        static Sprite Monster = new Sprite(BrainPad.Display.CreatePicture(8, 8, new byte[] {
            0,0,0,1,1,0,0,0,
            0,0,1,1,1,1,0,0,
            0,1,1,1,1,1,1,0,
            1,1,0,1,1,0,1,1,
            1,1,1,1,1,1,1,1,
            0,0,1,0,0,1,0,0,
            0,1,0,1,1,0,1,0,
            1,0,1,0,0,1,0,1,
            })) { X = 41 };
        static void ProcessBullet() {
            if (Bullet.Y > - 5) {
                Bullet.Clear();
                Bullet.Y -= 5;
                Bullet.Draw();
                BrainPad.Buzzer.StartBuzzing(3000 - Bullet.Y * 30);
             }
            else {
                BrainPad.Buzzer.StopBuzzing();
                if (BrainPad.Buttons.IsUpPressed()) {
                    Bullet.X = Ship.X + Ship.Width / 2;
                    Bullet.Y = 55;
                    
                }
            }
        }
        static void ProcessShip() {
            Ship.Clear();
            if (BrainPad.Buttons.IsLeftPressed())
                Ship.X -= 5;
            if (BrainPad.Buttons.IsRightPressed())
                Ship.X += 5;
            if (Ship.X < 5) Ship.X = 5;
            if (Ship.X > 85 - Ship.Width) Ship.X = 85 - Ship.Width;
            Ship.Draw();
        }
        static int MonsterDelta = 5;
        static void ProcessMonster() {
            Monster.Clear();
            Monster.X += MonsterDelta;
            if (Monster.X < 5 || Monster.X > 85-Monster.Width) {
                MonsterDelta *= -1;// Reverse
                Monster.Y += 10;
            }
            Monster.Draw();
        }
        static void ProcessCollisions() {
            // Check the bullet
            if (Bullet.X >= Monster.X && Bullet.X <= Monster.X + Monster.Width &&
                        Bullet.Y >= Monster.Y && Bullet.Y <= Monster.Y + Monster.Height) {
                for (int i = 0; i < 3; i++) {
                    for (int f = 1000; f < 6000; f += 500) {
                        BrainPad.Buzzer.StartBuzzing(f);
                        BrainPad.Wait.Minimum();
                    }
                }
                BrainPad.Buzzer.StopBuzzing();
                Bullet.Clear();
                Monster.Clear();
                Monster.Y = 0;
                Bullet.Y = -5;
            }
            // Did we lose?
            if (Monster.Y > 40) {
                if (Ship.X > Monster.X && Ship.X < Monster.X + Ship.Width) {
                    for (int f = 2000; f > 200; f -= 200) {
                        BrainPad.Buzzer.StartBuzzing(f);
                        BrainPad.Wait.Minimum();
                    }
                    BrainPad.Wait.Seconds(1);
                    BrainPad.Buzzer.StopBuzzing();
                    Monster.Clear();
                    Monster.Y = 0;       
                }
            }
        }
        static void Main() {
            BrainPad.Display.DrawLine(90, 0, 90, 64);
            BrainPad.Display.DrawLine(0, 0, 0, 64);
            while (true) {
                ProcessCollisions();
                ProcessShip();
                ProcessBullet();
                ProcessMonster();
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

## What Is Next?
In the area on the right we need to show how many lives you have left. Perhaps show three ships on the top right that represent three lives?

We also need to show the score. Would the lower right corner be good place?

Just like before, add ProcessLives() and ProcessScore(). This should be a fun exercise.

Need more of a challange? The monster should run faster as the score increases.

