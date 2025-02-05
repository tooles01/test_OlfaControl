## ZMQ
The olfa driver has a ZMQ subscriber socket, allowing it to receive messages from a ZMQ publisher. The default address is "tcp://127.0.0.1:5556" (can be manually edited in the heading of *olfa_driver_48line.py*).  

Strings received from a ZMQ publisher are sent directly to the master Arduino and **MUST** match the format outlined at [OlfaControl_Arduino](https://github.com/tooles01/OlfaControl_Arduino/blob/master/README.md), with the exception of setpoint updates.  Setpoint updates can be sent as SCCM values - they are parsed and converted into integer values within the olfa driver.  

### Examples:
Setpoint update sent from ZMQ publisher:
```C
S_Sp_50_A1    // Set A1 setpoint to 50 SCCM (olfa driver converts from SCCM to integer before sending to master Arduino)
```
Setpoint update sent directly to master Arduino:
```C
S_Sp_547_A1   // Set A1 setpooint to 547 (integer value)
```