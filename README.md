# KrivikRepository
My first repozitory


node-red-contrib-pid
=====================

A [Node-RED] node which operates as a PID loop controller node intended for the control of real world processes.


Install
-------

Run the following command in the root directory of your Node-RED install

    npm install node-red-contrib-pid


Usage
-----

Pass the node a process value in **msg.payload** at regular intervals and configure (or pass in via a message) a setpoint and tuning parameters and the algorithm will generate a required power output between 0 and 1 in **msg.payload** using a Proportional+Integral+Derivative algorithm.
    
Any message received with a **msg.topic** other than those defined below is assumed to contain the current process value in **msg.payload** and the control algorithm will be run, passing on the required power in **msg.payload**.

The properties below can also be set using **msg.---**. For example, to change the setpoint you can set the message attribute **msg.setpoint** to the required value. Using this method, it is possible to set multiple PID properties using the same message. When using this method to set the properties **msg.payload** should contain the process value.

Example and Tuning Guide
------------------------
