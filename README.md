# smart-cities
This repository contains all the artefacts related to the FAPEAL/FAPESP projects on Software Testing for Smart Cities

# Software Testing for Smart Cities - A computer vision approach to modern problems
Our projects main concern is to solve problems related to Smart Cities that can be solved using object recognition models. Thus, a connection with the real world and the virtual one must be done, and we will use a connected to the internet Raspberry Pi with a camera module to achieve it.

For this to work, we have chosen the **client-server architecture** as the main architecture of our project. As such, we must define the boundaries that delimit both our server and our clients.

### The server 
Will be held accountable for the communication between the deep learning model and ourselves (the humans and providers of this service), and will also be held accountable for sending the commands to the client.

### The client 
Will be in charge of sending the video input to the server and executing the commands that the server commands it to. These commands will be such as "blink a light" or "emit a sound".

# Problems that our project can solve
This project is able to solve each and every one of these problems, but some may need a little more configuration:
- Prohibited parking;
- Wild animals in the streets;
- Jaywalking;
- Analysis of the criminology of a place*;
- Identification of stolen vehicles.

# The repository
For a better organization, we'll separate this repository in three main folders:
1. The deep learning model and it's dependencies
2. The server-side of the application
    1. The backend of the webserver
    2. The frontend of the webserver
3. The client-side of the application (RPi code)


Each one will contain instructions of installation and a quick example for testing purposes.

In the root folder there's also a slide presentation that can be used as an introduction to Deep Learning: as it doesn't assumes you have any prior knowledge of the subject, it goes from a single Perceptron to a complex Computer Vision model.

# References
Our work is mostly done after scraping and searching in lots of different places. 

Overall, as we need speed for doing real-time analysis and accuracy at the same time, we could not accept some slacking algorithm. To achieve the high quality that we have, we chose [YOLO](https://github.com/AlexeyAB/ScaledYOLOv4) as our algorithm. 

YOLO can be found in AlexeyAB's [GitHub](https://github.com/AlexeyAB). Also, we've used Darknet as our framework - from him as well - because it's faster than Tensorflow. 

~~We have used Django and Flask for our webserver~~ and the majority of the project is built upon Python's foundation. 
