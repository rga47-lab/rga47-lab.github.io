# Lab 11 (Grid Localization using Bayes Filter (REAL))

The goal of this lab was to perform localization with the Bayes filter from lab 10 on my physical robot. This involved combing the simulation work from lab 10 with room mapping from lab 9. To begin, I set up the base code by copying lab11_sim.ipynb and lab11_real.ipynd into my notebooks directury and localization_extras.py into the root directory. I also copied base_ble.py, ble.py, connection.yaml, and cmd_types.py into the notebooks directory so that Bluetooth communication with my car worked correctly. 

## Localization Simulation

Once I had my python environment set up, I tested the Bayes filter using the simulator. Here is a photo of the end result: 

![sim](files/lab11_sim.png)

As you can see, the belief (blue) is very close to the ground truth (green) despite the odometry model (red) being very incorrect.

## Code Changes

The code on the Artemis side was very similar to that from lab 9. I adjusted the number of increments to 18, rotating 20 degrees every increment. An additional change I made was to create a new case that sent over my stored data seperately. 

On the python side, the perform_observation_loop function calls the MAP_ROOM case from lab 9 as well as the new send data case. 

![code](files/lab11_observation_loop_code.png)

## Localization Results and Discussion

Here are the localization results from each point: 

### Point (-3,-2)
![point1](files/lab11_-3_-2.png)
![point1](files/lab11_-3_-2_stats.png)

This was a very good result! The belief is very close to the ground truth. 

### Point (0,3)
![point2](files/lab11_0_3.png)
![point2](files/lab11_0_3_stats.png)

This pose, though slightly worse than (-3,-2), was still very accurate. The loss of accuracy may be because of drift in the spinning robot. Also, there are more farther walls at this point than at the last one. 

### Point (5,-3)
![point3](files/lab11_5_-3.png)
![point3](files/lab11_5_-3_stats.png)

Unlike the last two, this point was quite inaccurate. I suspect this has to do with the box, but I'm not sure exactly what the issue the filter has with this point is. I will have to run more trials in this spot later. 

### Point (5,3)
![point4](files/lab11_5_3.png)
![point4](files/lab11_5_3_stats.png)

This point is back to being pretty accurate! The belief is slightly off, but still pretty close to the ground truth. 

For most of these points, the localized pose is fairly close to the ground truth. That's pretty impressive and was very cool to see. The results of this lab overall seem very promising and I'm looking forward to lab 12!