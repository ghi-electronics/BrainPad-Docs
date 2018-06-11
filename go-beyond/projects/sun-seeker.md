# Sun Seeking Robot
---

**Difficulty: Moderately easy, some assembly required**

**Objective: Servo control / simple robotics**

## How it Works
A toy car is programmed to stay in the sunlight and turn any time the light sensor senses shade. Both rear wheels of the car are driven by continuous servo motors. When the program starts both motors are driving the car forward. When the light sensor detects light below a given threshold, the program will stop one of the rear wheels causing the car to turn. When the sensor once again senses the sunlight both wheels push forward. The program alternates which wheel will stop when the light sensed is below the threshold.

## The Code

### Microsoft Makecode
Click [here](https://makecode.com/_PFX5r3bgLcPh) to go directly to the program on Microsoft MakeCode. You can also copy and paste the following JavaScript code into Microsoft MakeCode's JavaScript editor.

```
let Direction = 0
input.onLightConditionChanged(LightCondition.Dark, function () {
    if (Direction == 0) {
        pins.SERVO2.servoWrite(90)
        Direction = 1
    } else {
        pins.SERVO1.servoWrite(90)
        Direction = 0
    }
})
input.onLightConditionChanged(LightCondition.Bright, function () {
    pins.SERVO1.servoWrite(180)
    pins.SERVO2.servoWrite(0)
})
input.setLightThreshold(LightCondition.Dark, 250)
pins.SERVO1.servoWrite(180)
pins.SERVO2.servoWrite(0)
```

Microsoft MakeCode block program:

![Sun seeker block program](images/sun-seeker-blocks.png)