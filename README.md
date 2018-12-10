# KrivikRepository
Níže bude README file pro:

# node-red-contrib-unipi
This module provides two nodes in Node-RED to quickly access the UniPi device. For more information about UniPi devices see <a href="https://www.unipi.technology/">here</a>.

For connection of the node with the UniPi device is required to install on the UniPi device the EVOK utility in version 2.0 or higher. See <a href="https://github.com/UniPiTechnology/evok">UniPi GitHub</a> or <a href="https://www.unipi.technology/cs/content/evok-18">UniPi EVOK</a> for more information.

For connection - node and the UniPi device - use the websocket node which is set as `connect to` on the adress ws://[adress of the UniPi device]/ws.

## Pre-requisites

The Node-RED-Dashboard requires <a href="https://nodered.org">Node-RED</a> to be installed.

## Install

To install the UniPi nodes use the `Menu - Manage palette` option and search for `node-red-contrib-unipi`, or run the following command in your Node-RED user directory (typically `~/.node-red`):

    npm i node-red-contrib-unipi

## Usage

#### Basic information
Once one installed `node-red-contrib-unipi` into Node-RED there are two nodes for use.

   - **UniPi input** node - primary a filter for UniPi data which are get from the relevant websocket. Helps to easily access the needed data and work with them throw the flow/s.
   - **UniPi output** node - primary helps to see the ***all*** data by the request, ***filter*** the choosen data or to ***set*** the features *relay*, *digital output* and *led* -> to switch ON/OFF or set *analog output* to desired value. 
#### Preparation
Once one has already bought the UniPi device make oneself sure that the <a href="https://www.unipi.technology/cs/content/evok-18">EVOK</a> is installed on one's device.

Once one has ***UniPi Control Panel*** (which is the enviroment of the EVOK utility in your browser) active then the first needed step is done. Copy the adress from the console (the form is e.g. *78.230.110.45:8080*) and paste it to the websocket node in form ws://[adress of the UniPi device]/ws (with the previous example of the adress it looks like: ws://78.230.110.45:8080/ws) and set the websocket node as ***connect to***.









The properties below can also be set using **msg.---**. For example, to change the setpoint you can set the message attribute **msg.setpoint** to the required value. Using this method, it is possible to set multiple PID properties using the same message. When using this method to set the properties **msg.payload** should contain the process value.
