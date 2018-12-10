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

Once one has ***UniPi Control Panel*** (which is the enviroment of the EVOK utility in your browser) active then the first needed step is done. Copy the adress from the console (the form is e.g. 78.230.110.45:8080) and paste it to the websocket node in form ws://[adress of the UniPi device]/ws (with the previous example of the adress it looks like: ws://78.230.110.45:8080/ws) and set the websocket node as ***connect to***.

#### Connection
Now only connect the *websocket input node* with *UniPi input node* 


#### Example of the flow
```
[{"id":"1183c4dd.40bdcb","type":"tab","label":"UniPi","disabled":false,"info":""},{"id":"dbb4f694.5f6858",
"type":"inject","z":"1183c4dd.40bdcb","name":"","topic":"","payload":"true","payloadType":"bool","repeat":"",
"crontab":"","once":false,"onceDelay":0.1,"x":265,"y":180,"wires":[["bda1b09.49cad5"]]},{"id":"b012802f.7d721","type":"debug","z":"1183c4dd.40bdcb","name":"","active":true,
"tosidebar":true,"console":false,"tostatus":false,"complete":"true","x":595,"y":119,
"wires":[]},{"id":"3fe20ea9.48b9c2","type":"unipi-input","z":"1183c4dd.40bdcb","name":"","alias":"","devices":"relay",
"circuits":"1.01","property":"","seedev":"0","seecirc":"0","orig":"0","x":425,"y":119,"wires":[["b012802f.7d721"]]},{"id":"bda1b09.49cad5","type":"unipi-output","z":"1183c4dd.40bdcb","name":"","cmd":"set","alias":"",
"devices":"relay","circuits":"1.01","enableFil":"1","inputFil":"","relayFil":"","digoutFil":"","analoutFil":"",
"analinFil":"","ledFil":"","x":425,"y":201,"wires":[["544c7cc1.949a74"]]},{"id":"544c7cc1.949a74","type":"websocket out","z":"1183c4dd.40bdcb","name":"","server":"7b985caa.4160b4","client":"","x":686,"y":201,"wires":[]},{"id":"cac3232a.e0135",
"type":"websocket in","z":"1183c4dd.40bdcb","name":"","server":"","client":"fa87ece.ccc5b1","x":184,"y":119,"wires":[["3fe20ea9.48b9c2"]]},{"id":"f855be37.5bcbd","type":"inject","z":"1183c4dd.40bdcb","name":"","topic":"","payload":"false",
"payloadType":"bool","repeat":"","crontab":"","once":false,"onceDelay":0.1,"x":262,"y":220,"wires":[["bda1b09.49cad5"]]},
{"id":"7b985caa.4160b4","type":"websocket-listener","z":"","path":"ws://78.230.110.45:8080/ws","wholemsg":"false"},
{"id":"fa87ece.ccc5b1","type":"websocket-client","z":"","path":"ws://78.230.110.45:8080/ws","tls":"","wholemsg":"false"}]
```


```
[{"id":"dfafc240.c812f","type":"hc2-server","z":"4b7c1c9a.a28214","name":"HC2","ip":"192.168.1.36","topic":"home/status","roommode":false,"x":330,"y":240,"wires":[["52dea3e6.dfa6dc"]]},{"id":"52dea3e6.dfa6dc","type":"debug","z":"4b7c1c9a.a28214","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":500,"y":240,"wires":[]},{"id":"619a504a.20b5b","type":"inject","z":"4b7c1c9a.a28214","name":"poll","topic":"","payload":"","payloadType":"date","repeat":"10","crontab":"","once":false,"onceDelay":0.1,"x":140,"y":240,"wires":[["dfafc240.c812f"]]},{"id":"2e761400.c913cc","type":"hc2-dispatcher","z":"4b7c1c9a.a28214","name":"HC2","ip":"192.168.1.36","x":430,"y":320,"wires":[["463dcc2f.f0d134"]]},{"id":"155434ba.bd0a7b","type":"mqtt in","z":"4b7c1c9a.a28214","name":"","topic":"home/command/#","qos":"2","broker":"e8ca2733.78d6a8","x":160,"y":320,"wires":[["2e761400.c913cc"]]},{"id":"463dcc2f.f0d134","type":"debug","z":"4b7c1c9a.a28214","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"false","x":690,"y":320,"wires":[]},{"id":"c00c082a.897a88","type":"inject","z":"4b7c1c9a.a28214","name":"reset","topic":"0","payload":"","payloadType":"num","repeat":"3600","crontab":"","once":false,"onceDelay":0.1,"x":130,"y":160,"wires":[["dfafc240.c812f"]]},{"id":"e8ca2733.78d6a8","type":"mqtt-broker","z":"","name":"nas","broker":"192.168.1.29","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"birthTopic":"","birthQos":"0","birthPayload":"","closeTopic":"","closeQos":"0","closePayload":"","willTopic":"","willQos":"0","willPayload":""}]
```
