# Person Identifier
This project aims to identify a human using the Raspberry Pi camera module.

Everytime a human passes through the camera lenses, the RPi will send a beep.

The video feed will be continuosly fed to the pre-trained object detection neural network in the webserver. Then, the server will send a "play a beep" command back to the RPi client.

The RPi will recieve this command and use the GPIO port to interact with a speaker.