# KrivikRepository
Níže bude README file pro:

# node-red-contrib-unipi
This module provides two nodes in Node-RED to quickly access the UniPi device. For more information about UniPi devices see <a href="https://www.unipi.technology/">here</a>.

For connection of the node with the UniPi device is required to install on the UniPi device the EVOK utility in version 2.0 or higher. See <a href="https://github.com/UniPiTechnology/evok">UniPi GitHub</a> for more information.

## Pre-requisites

The Node-RED-Dashboard requires <a href="https://nodered.org">Node-RED</a> to be installed.

## Install

To install the UniPi nodes use the `Menu - Manage palette` option and search for `node-red-contrib-unipi`, or run the following command in your Node-RED user directory (typically `~/.node-red`):

    npm i node-red-contrib-unipi

## Usage
Once you installed `node-red-contrib-unipi` into your Node-RED you have two nodes for use.

   - **UniPi input** node - primary a filter for UniPi data gets from the relevant websocket. Helps to easily access the needed data and work with them throw the flow/s.
   - **UniPi output** node - primary helps to see the all data by the request, filter the choosen data or to set the features like relay 
### Preparation








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

    zkusim tady neco
    
Any message received with a **msg.topic** other than those defined below is assumed to contain the current process value in **msg.payload** and the control algorithm will be run, passing on the required power in **msg.payload**.

The properties below can also be set using **msg.---**. For example, to change the setpoint you can set the message attribute **msg.setpoint** to the required value. Using this method, it is possible to set multiple PID properties using the same message. When using this method to set the properties **msg.payload** should contain the process value.
