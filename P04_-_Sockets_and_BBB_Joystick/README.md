# Project 04
All assignments were done in the C++ and Python programming languages for the Operational Systems subject.
UFRN - 2017.

## Contributors
Gustavo Araújo Carvalho

Thiago César de Lucena

### Assignment 4:
This project is intended to implement a joystick-like input for a game of our choice using BeagleBone Black and electronic components, an then use sockets to make the communication between the joystick and the game. To do so, we forked an open source top-down shooter available on Github and modified the original project to fit this project's needings. One important detail is that the joystick and game codes were made in different programming languages to highlight the connection mechanism sockets provide.

#### Joystick
The electronic components used for specific functionalities on the joystick were a potentiometer, a LDR (Light Dependent Resistor) and a push button. To develop the joystick coding, it was necessary to use threads and mutexes to manage the reading and execution of each component's funcionality. The components' functions are listed below:

* Potentiometer, controlling player's horizontal position.
* Push button, controlling shooting action.
* LDR, used to change option on starting screen and to exit game while playing.

#### Sockets communication
Each component has its own thread and mutex, having no priority scheme due to the game mechanics. Furthermore, the socket thread shares access to each component's mutex. When a component's thread is acessing its critical region, the socket communication is blocked or vice versa, this means, either the read values are being updated, or they are being sent through the socket. Once the access is finished, the mutex(es) is/are released and any blocked thread that shares it/them continues to execute normally.

The communication uses UDP protocol. The game is executed as a server on the user's machine and the joystick code is executed as a client on the BeagleBone Black.

For more information about the game, BeagleBone configuration, and access to the source codes, check the forked repository: https://github.com/GustavoAC/PyGalaxian.
