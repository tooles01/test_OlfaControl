# 8-line Olfactometer + Mixing Chamber

## Full System Overview

<p align="center"><img src="images/olfa_full_labeled.png" width="40%"></p>

<!--

<br>

<p align="center"><img src="images/Full System Schematic_11.png" width="70%"></p>
<br>

### Simplified:

<p align="center">
  <img src="images/Full%20System%20Schematic_simplified-clean%20air.png" width="40%">
  <img src="images/Full%20System%20Schematic_simplified-odor%20delivery.png" width="40%">
</p>
-->

## Getting Started

### Software Installation

**Python versions**: As of 4/29/2024: GUI is currently compatible with Python 3.9, 3.10, 3.12  

1. Download/clone the GUI at [OlfaControl_GUI](https://github.com/tooles01/OlfaControl_GUI/tree/shannon-branch).
    - It is highly recommended to do so via [Github Desktop](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop) in order to pull new commits (bug fixes/updates) in real time.
    - If not using GitHub Desktop:
        - Click the green "<>Code" button above
        - Click "Download ZIP"
        - Save the folder to a directory on your computer.
2. Open the command prompt and navigate to the directory the folder is stored in.
3. *Optional:* Create & activate a [virtual environment](Resources\virtual_environment.md)
4. Install the required packages by entering: ``` pip install -r requirements.txt ``` into the command prompt.
5. Run the GUI: ```python olfa_driver_48line.py```  
    (Big Program for running automated stuff/adding PID: ```python main.py```)  
<br>

### ZMQ
The olfa driver has a ZMQ subscriber socket, allowing it to receive messages from a ZMQ publisher. The default address is "tcp://127.0.0.1:5556" (can be manually edited in the heading of *olfa_driver_48line.py*).  

Strings received from a ZMQ publisher are sent directly to the master Arduino and **MUST** match the format outlined at [OlfaControl_Arduino](https://github.com/tooles01/OlfaControl_Arduino/blob/master/README.md), with the exception of setpoint updates.  Setpoint updates can be sent as SCCM values - they are parsed and converted into integer values within the olfa driver.  

#### Examples:
Setpoint update sent from ZMQ publisher:
```C
S_Sp_50_A1    // Set A1 setpoint to 50 SCCM (olfa driver converts from SCCM to integer before sending to master Arduino)
```
Setpoint update sent directly to master Arduino:
```C
S_Sp_547_A1   // Set A1 setpooint to 547 (integer value)
```

## Quick Start

1. Activate virtual environment  
2. Run GUI: `python olfa_driver_48line.py`  
3. Connect to Arduino  
4. Load config file  
5. Optional: Connect to ZMQ server  

## Calibration tables & Config files
### Calibration tables

To read from each flow sensor, the GUI uses a calibration table to convert the data from voltage to flow rate.  
<p align="center"> <img src="images/Flow Sensor-GUI-Calibration table.png" width="100%"></p>

Each flow sensor has a slightly different calibration, so it is recommended to use the calibration table specific to each individual sensor to ensure accurate flow control. (Further information on calibrating flow sensors can be found [here](Resources/flow_sensor_calibration.md).  

***Note:*** Calibration tables need to be in a folder called **calibration_tables** within the OlfaControl_GUI folder.  
### Config files

To easily load these calibration tables into the GUI, you can use a config file that lists the miniMFCs on your olfactometer and their corresponding calibration tables.  

This allows for quickly loading all calibration tables into the GUI all at once (as opposed to manually entering them into the Vial Details box for each line).  
*<p align="center"> *Example config file:*  </p>*
<p align="center"> <img src="images/setup_GUI_03_configFile.png" width="50%"></p>

With the GUI open, click "Load config file" and select the config file. (This must be done each time the GUI is closed and reopened.)  

![setup_GUI_02](images/setup_GUI_02_loadConfig.png)

To confirm that the config file loaded correctly, open up one of the Vial Details boxes and check that the intended calibration table for that miniMFC is selected.  
![setup_GUI_vialDetails](images/setup_GUI_vialDetails.png)