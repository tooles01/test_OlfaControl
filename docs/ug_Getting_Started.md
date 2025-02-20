# Getting Started

<!--### Software Installation-->
## GUI Install

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


## Hardware setup

Need 1000cc input air (Alicat) (& corresponding power/control cables)

- Arduino cable to connect to computer
- 24V power to connect to PCB
<br>


# Quick Start

1. Activate virtual environment  
2. Run GUI: `python olfa_driver_48line.py`  
3. Connect to Arduino  
4. Load config file  
5. Optional: Connect to ZMQ server  
