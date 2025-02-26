### Lab 3 (ToF)

## Prelab

### I2C Address

From the data sheet for the Time of Fight (ToF) sensors, we know that they use I2C  to communicate with the Artemis board. The data sheet also tells us that the address of one sensor should be 0x52.

### 2 Sensor Approach

The car will have two ToF sensors. Both sensors have the same I2C adress, so we will need to set one of the sensors to a different address in order to differentiate them and use them at the same time. This is where the XSHUT pin is useful. It shuts down of the ToF sensors which allow us to communicate with the other and change it's I2C address. Then we can reboot the other sensor and use both at the same time. The XSHUT pin is connected directly to the Artemis. 

### Wiring Diagram and Sensor Placement

![wiringDiagram](wirindiagram.jpeg)

This is a diagram of the wiring. I chose to use both the longer cables for the ToF sensors as I am more likely to move them to different positions on the car for different types of labs. I see two useful configurations of the sensors. The first possibility is one on the front and one on the back which will be useful for determining what's around the robot as it goes forward, backward, and flips over very quickly. The second possibility is one in the front and one on the side which will be useful for mapping out the room or following a wall. I will likely start with one in the front and one in the back as I believe the next few labs involve doing stunts. However, using the longer cables for these sensors means that if I discover these aren't optimal configurations they will be pretty easy to move. The IMU will get the short cable because it is unlikely that it will need to be moved and the placement will probably be more central on the car than the ToF sensors. 

## Lab Tasks: 

# ToF Sensor Soldering

![wiringDiagram](solderingToF.jpeg)

# I2C Adressing

![I2C](I2CaddressScan.HEIC)

Here is a photo of Artemis scanning for an I2C device. As you can see, it finds a device with the address 0x29. This is slightly surprising as the datasheet tells us the device should have an address of 0x52. However, closer reading tells us that I2C uses the LSB as a Read/Write indicator bit. Ignoring the LSB turns 0x52 into 0x29, and the address makes sense. 

# Sensor Data Mode

# 2 ToF Sensors

# ToF Sensor Speed

# 2 ToF sensors and the IMU

# Time vs Distance (2 sensors)
 
# Time vs Angle