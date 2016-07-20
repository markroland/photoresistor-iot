# Photoresistor

This project logs the light intensity measured by a photoresistor. The data is
graphed in near real-time on a web page.

# Parts

 - Arduino (Leonardo)
 - Raspberry Pi 3 (Model B v1.2)
   - Running Raspbian GNU/Linux 8 (jessie)
   - Requires Python 2.7
 - Power Supply for Raspberry Pi
 - USB to Micro-B cable
 - Breadboard
 - 10k Resistor
 - Photoresistor (Cad)
 - Jumper wires suitable for a breadboard

# Setup

1) Build the circuit on the breadboard

![Circuit Diagram](https://github.com/markroland/iot-photoresistor/blob/master/schematic/schematic.png)

2) Load the `Arduino/Photoresistor.ino` sketch to the Arduino board

3) Connect the Arduino to the Raspberry Pi (if not already connected)

4) Run the `log-serial.py` script on the Raspberry Pi. This will save a reading from
   the photocell to a CSV file every second.

```sh
python ./log-serial.py &
```

5) Run `server/server.py` script. This may require the installation of the Flask pip module.
   Run the following commands from the project root:

```sh
python ./server/server.py > /dev/null 2>&1 &
```

Or if running while logged in to the Raspberry Pi via ssh, you can execute the following
command to run the script in the background, and not stop when you log out. This also suppresses
the `nohup.out` file that is generated by default.

```sh
nohup python ./server/server.py > /dev/null 2>&1 &
```

# License

[Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
