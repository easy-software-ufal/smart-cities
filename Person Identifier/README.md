# Person Identifier
This project aims to identify a human using the Raspberry Pi camera module.

Everytime a human passes through the camera lenses, the RPi will send a beep.

The video feed will be continuosly fed to the pre-trained object detection neural network in the webserver. Then, the server will send a "play a beep" command back to the RPi client.

The RPi will recieve this command and use the GPIO port to interact with a speaker.

# Timeline

At first, we decided that we wanted to recognize objects using a camera attached to a computer using tensorflow or keras in a python script. 

To get it done, we have learned about the best way to create a model from scratch or reutilize one previously created. 

We decided to use the YOLO model because it has a good amount of literature and plenty of applications. To get to know better, we tried simulating a detection and ended up being very happy about our result:

![](The%20Model/detections/detection1.png)
After this, we decided to focus on the Smart City context.
## Entering inside the context
Since there are many real world smart city problems, we thought about trying to apply our solution to a narrower scope, such as five little projects. But to understand better the functioning, we decided to focus solely on the best of the five proposed in the beginning.

The potential five projects were:
* IRREGULAR TRASH DISPOSAL
* ELDER AND DISABLED PARKING SLOTS
* LAZY TRAFFIC LIGHTS/ JAYWALKING DETECTOR
* PPI USE DETECTOR ON CIVIL CONSTRUCTIONS
* OVERCROWDED BUSES

Some of them were disregarded as projects because of the motivation and the benefit, that would be near none. In the end we chose the PPI detector as our primary focus and after getting this first project done we would select another one from those two:

* IRREGULAR TRASH DISPOSAL
* LAZY TRAFFIC LIGHTS/ JAYWALKING DETECTOR

Of course this list can grow any moment, but this is what we have in mind for now.

# Next steps
Since we already have a direction, we will look forward to implement this in a real world scope.


