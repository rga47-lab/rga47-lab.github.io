# Lab 7 (Kalman Filter)

## Lab Tasks

### Estimating Drag and Momentum

Before implementing the Kalman filter, we needed to estimate the drag coefficient (d) and momentum (m) of the system. I achieved this by driving the robot towards a wall at a constant motor speed and logging the Time-of-Flight (ToF) sensor values along with the motor input. The robot was driven towards the wall with a PWM value between that is 78% (200/255) of the maximum PWM.

### Step Response Analysis:

The motor was driven at a constant speed until it approached the wall, and the distance data was logged.

From the collected data, I identified the steady-state speed and the time to reach 90% of the final speed. These values were used to estimate the drag and momentum of the robot. The key measurements were steady-state speed and 90% rise time (time it takes for the car to reach 90% of its max speed).

Using this data, drag and momentum were estimated and then used to make a Kalman Filter model. 

******INSERT PIC******

### Kalman Filter Initialization

The Kalman filter requires a state-space model of the car's dynamics. We used a discrete-time state-space model where the state vector consisted of the robot’s distance and velocity. The system matrices A (state transition) and B (control input) were derived based on the robot’s dynamics. As shown in the lecture slides: 

******INSERT PIC OF LECTURE SLIDES******

The measurement model (matrix C) defines how the ToF sensor relates to the system state. C=[-1 0] indicates that we measure the negative of the distance from the wall. 

### Process Noise and Sensor Noise

In order for the Kalman filter to work, it is crucial to define the process and sensor noise covariances (Sigma_u and Sigma_z). These values determine how much trust the fiter places in the model versus the sensor measurements. The following shows the code I used to calculate and account for noise: 

The value of sigma+3 was estimated from the ToF sensor's accuracy as specified by its data sheet. 

### Python Implementation

******INSERT PIC******

The preedicted state and the predicted covariance are computed using the system dynamics. The Kalman gain is computed to combine the prediction and the measurement update. Then the state estimate is updated using the gain and the measurement residual. Finally the covariance matrix is updated to reflect the uncertainty after incorporating the measurement. 

### Implementing on Car

Next I integrated the Kalman filter into the control loop, using the estimated distance and velocity to control the robot using the PID controller from lab 5. This allowed the robot to speed towards the wall while still stopping 1ft away. This happened much faster than it did in lab 5. 

******INSERT Video******

******INSERT Graphs******

### Conclusion


