# Buzzer
---
The BrainPad buzzer is an output device. It is really not a buzzer but a crude speaker that is even capable of playing voice or music, but with very poor quality. The buzzer commands allow you to make a beep sound of fixed frequency and duration. You can also tell the BrainPad to play a tone where you decide the frequency. The BrainPad will keep playing that sound until you tell it to stop. This allows you to play sound effects for games as well as simple melodies.
 
* BrainPad.Buzzer.Beep() - Plays a short duration beep on the BrainPad's buzzer.  
 
* BrainPad.Buzzer.StartBuzzing(double frequency) - Plays a sound of given frequency. Will keep playing untils told to stop. [Example: BrainPad.Buzzer.StartBuzzing(251.00)] 
* BrainPad.Buzzer.StopBuzzing() - Stops the buzzer if it is currently playing.