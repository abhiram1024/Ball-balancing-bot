# Ball-balancing-bot
A ball balancing plate that is controlled by arduino UNO and opencv
this was a project I worked on for a course I had in my college, the gyst of it is a robot that could centre a ping pong ball placed on a 20*20 cm^2 plate that would be controlled by 4 servos attached to the mid points of the edges of the plate.

![setup](https://github.com/user-attachments/assets/125ea2ac-05d7-4f16-8448-c76605c7626c)

the basic working goes like this - 
1) opencv tracks the position of the ball on the screen with the help of a camera placed directly above the setup, the opencv code detects all sorts of circular objects and is independent of color, the houghcircles    function was used to do this.

   ![tracking](https://github.com/user-attachments/assets/a437eb41-2360-4071-8704-f93dbaad9dd0)

   
3) It calculates the error of the ball as the distance between the centre of the ball and the centre of the plate, this would be more accurate if you placed a amrker on the middle of the plate but I just tried to      centre the camera as best as I could.

4) The pid then returns a correction value based on the distance and velocity of the ball away from the centre which is processed and scaled and returned as the angle that the servo motor should move up or down by
   data is transferred every .01s and an be changed by editing dt in the pid_control function, but fair warning before you do, making the value too small seems to lead to the system crashing after a certain amount     of time (around 30 seconds). I don't know exactly why this happens, but if your program crashes, this might be one of the reasons

That's it for the README

