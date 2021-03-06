[Goto Readme](/README.md)

# Example: Pairing a device

Message flow example for pairing a device

Start pairing a basic+ thermostat.  (Push BOOST button long)

<a id="pairping">
### 1. The thermostat sends a PairPing
</a>

![](images/pairing_01.png)

Result after parsing:

![](images/pairing_02.png)

You see here:

* message type: PairPing
* deviceId:  This is the address of the device
* dest: destination.  000000 is a broadcast address, meaning not paired yet.   


### 2. a PairPong message is assembled and send to the device.

![](images/pairing_03.png)

This message is appended with the Zr string, to start receiving again.



### 3. The device answers

![](images/pairing_04.png)

Result after parsing:

![](images/pairing_05.png)


If we didn't receive a Ack message, culfw.step would stay at 1.

The device tries a few times to send a PairPing, so at the next PairPing we [start again](Example_pairing.md#pairping) 


#### Note:

In the original Cube software, pairing does a lot more.

When a device pairs with the Cube, the cube sends Associate messages to link the device to other partners in the same group.  The new device is also send as pairing partner to the existing group devices.

For the moment, i do not implement groups, and i do not implement association with other devices.

<s>However, the associate command exists in the flow and it is tested.</s>
  






