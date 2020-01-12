# Enviroplus-DietPi
Instructions for getting the Enviro+ sensorboard to work with DietPi. Not sure all the steps are needed, but following these steps gets it working.

# Installing DietPi 
## Minimal system
Go to https://dietpi.com/phpbb/viewforum.php?f=8 for instructions and guides to get to setup a minimal system.

## Additional setup to get the board running on DietPi
The complete guide for Enviro+ is found here: https://github.com/pimoroni/enviroplus-python/. For DietPi, do the following:

* `pip install enviroplus && pip3 install enviroplus`. 

You'll need to edit the DietPi config files. If editing from DietPi use `sudo nano /DietPi/config.txt`; otherwise edit /boot/config.txt as follows:

* Line 72: `dtparam=i2c_arm=on`
* Line 73: `dtparam=i2c1=on`
* Line 76: `dtparam=spi=on`
* Line 81: `enable_uart=1` (make sure that serial console is off)
* Line 99: `dtoverlay=pi3-miniuart-bt`

Install the following dependencies:

* `apt install python-numpy python3-numpy`
* `apt install python-smbus python3-smbus
*	`apt install python-setuptools python3-setuptools
* `apt install build-essential`
* `apt install gdb-multiarch`
*	`pip install spidev`
*	`pip3 install spidev`
*	`pip install requests`
*	`pip3 install requests`
* `pip3 install future`

## Clone repositories for examples and MQTT support

1. If git is not installed: `sudo apt install git`
2. Optional for MQTT: Clone hotplot's repository for MQTT: `sudo git clone https://github.com/hotplot/enviroplus-mqtt /usr/src/enviroplus-mqtt`
3. Optional: clone Pimoroni's repository for example files: `git clone https://github.com/pimoroni/enviroplus-python /usr/src/enviroplus`
4. Make sure you have a MQTT broker setup (local one works fine, check mosquitto https://dietpi.com/phpbb/viewtopic.php?f=8&t=5). Get the host ip (below, I use localhost).
5. Same as step 5 at https://github.com/hotplot/enviroplus-mqtt (make sure to update `User` field, and the <arguments>).
6. Same as step 6 at https://github.com/hotplot/enviroplus-mqtt
  
# Running the Enviro+ on DietPi

For the Enviro+ board, use `python /usr/src/enviroplus/*.py`. Tip: The PMS35003 will not initiate if you run combined.py before luftdaten.py.
As for MQTT, use `python3 /usr/src/enviroplus-mqtt/src/main.py <arugments>` For a list of arguments, see https://github.com/hotplot/enviroplus-mqtt#supported-arguments
