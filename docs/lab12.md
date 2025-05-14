# Lab 12 (Path Planning and Execution)

## Objective

This lab brought together all the components developed throughout the semester to get the robot to navigate waypoints within a maze. The goal was to design and implement a path planning and control strategy to move the robot as accurately and efficiently as possible through these waypoints.

## Planning

The waypoints to hit were: 

    1. (-4, -3)    <--start
    2. (-2, -1)
    3. (1, -1)
    4. (2, -3)
    5. (5, -3)
    6. (5, -2)
    7. (5, 3)
    8. (0, 3)
    9. (0, 0)      <--end

I started by trying to get localization to work, but quickly encountered some major difficulties. As such, I decided to get a good run with just PID control and then return to localization if I had time (I did not :/ ).  

I decided to have my car drive along the most direct path between each waypoint. I know some people limited their robot to 90 degree turns, but my PID control was pretty good and I decided this wasn't necessary. 

The code structure I decided on was the following: I made a seperate case statement for each waypoint where orientation and linear control were both used to move the robot to the corresponding waypoint. I then called each waypoint case consecutively over BLE. This made testing incrementally and testing the path to different setpoitns individually easy. 

## PID Control

I did have to re-tune my orientation PID controller because I had removed the tape previously on my robot's wheels for stunt demos. Also I kinda hated the tape and didn't want to put it back on. A large challenge/annoyance I encountered during this lab was setting the min PWM value for the controller to be bounded by. To low and my car would get stuck while turning and be unable to overcome friction, and to high a value would cause the car to occasionally spin out of control while approching a setpoint. This by itself was fine, but the "good" min value would change as battery voltage ran low. Since this lab was long and involved running the car a lot, battery voltage was often low. I spent a lot of time waiting for batteries to charge. 

******INSERT CODE PIC HERE (ARDUINO)******

******INSERT CODE PIC HERE (PYTHON)******

## Results

### Best attempt 1: 
******INSERT VID HERE******

//describe attempt

### Best attempt 2: 
******INSERT VID HERE******

//describe attempt


### Localization

Unfortuntaely I was unable to get code that used localization to work correctly for this lab. Here's a video of my robot spinning in a circle though: 

******INSERT VID HERE******


## Conclusion

This has been a great semester and I really enjoyed taking this class! Shoutout to Prof. Helbling and all the TAs who made this class work. Thank you!

p.s. thanks for getting the second world setup outside the lab - that was really helpful