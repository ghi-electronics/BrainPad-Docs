# Accelerometer
---
The accelerometer is an input device that measures the force of acceleration in three axes (x, y, and z). This is commonly referred to as g-force and is expressed as a multiple of the force of gravity. For example an airplane pilot experiences of force of 2 g in a 60 degree banked turn. This means he is being pushed into his seat with a force that is double his weight. Fighter pilots may experience up to 9 g.

If the BrainPad is laying flat on a table with the display away from you on the right side, the x-axis runs horizontally left and right, the y-axis goes horizontally toward you and away from you, and the z-axis extends vertically straight up and down. If the BrainPad is stationary in this position the x and y axes would read 0 g, but the z-axis would read -1 g. This is because the force of gravity is pushing down on the accelerometer with force equal to 1 g (the force of the Earth's gravity). If you turn the BrainPad upside down, the z-axis would read 1 g. The only time all axes read zero is when the BrainPad is free falling.  

* `BrainPad.Accelerometer.ReadX()` - returns a double precision value in the range of -2 to 2 based on the BrainPad's x-axis acceleration.
 
* `BrainPad.Accelerometer.ReadY()` - returns a double precision value in the range of -2 to 2 based on the BrainPad's y-axis acceleration.

* `BrainPad.Accelerometer.ReadZ()` - returns a double precision value in the range of -2 to 2 based on the BrainPad's z-axis acceleration.
