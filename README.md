# Smart Parking App with RaspberryPi and PubNub C-Core SDK
Smart Parking System based on Raspberry Pi and PubNub for providing realtime updates on parking availability using the PubNub C-Core SDK.  

##OVERVIEW
This project demonstrates how we can build an application on Raspberry Pi which can control a set of HC-SR04 ultrasonic sensors,via ATMega8 chip to detect the availability of a parking slot and update this information on a mobile app using the PubNub's realtime data stream network. This application makes use of the new PubNub C-Core SDK on the device side and Javascript client SDK on the mobile app.

##INTRODUCTION
This application is assumed to be installed in a public parking space where each parking slot is monitored using a HC-SR04 ultrsonic sensor connected to ATMega8 and ATMega8 connected with a Raspberry Pi via the UART interface.

Refer [Circuit Diagram](schematic.png)

The application has three parts

1) Master Controller / RPi-Server - This is the master controller module which runs on raspberry pi (model b+). It periodically get the status of parking slots within its jurisdiction, via UART communication from ATMega8.

2) Device Controller - This is the sensor controller module which runs on ATMega8. The ATMega8 directly interfaces with ultrasonic sensors to detect the presence or absence of a vehicle in a parking slot and updates this status periodically to master controller.

3) Mobile App - This is a cordova based simple mobile app which displays a map of the entire parking lot with color coded status indicators. It provides an instant update to the driver about the current availablity of free parking slots.


##BUILD AND INSTALL
Refer [Build and Install steps](BUILD.md)

##WORKING

1) Power up the hadrware setup and make sure that Raspberry  Pi has access to internet.

2) Make sure that the ultrasonic sensors are not obstructed 

3) Launch the mobile app and check that the initial status of the parking slots is green to indicate that all slots are free.

4) Obstruct one or more ultrasonic sensors with a object to simulate the presence of a vehicle. 

5) Observe the display of mobile app. After a few seconds the color for the corrosponding slot numbers should turn red to indicate that the slots have been occupied.

6) If the mobile app indicates grey status for any of the parking slot then this means that the sensor has a fault or is malfunctioning and the slot is currently unavailable. This can simulated in ultrasonic sensor by blocking the trigger signal or blocking the reception of echo.  


