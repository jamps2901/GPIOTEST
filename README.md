# GPIOTEST
 GPIO Pin diagnostic process for Raspberry Pi
 
 Source: http://abyz.me.uk/rpi/pigpio/download.html
 
 Download & Install
If the pigpio daemon is running it should be killed (sudo killall pigpiod) before make install and restarted afterwards (sudo pigpiod).

The initial part of the make, the compilation of pigpio.c, takes 100 seconds on early model Pis.  Be patient.  The overall install takes just over 3 minutes.
Download and install (V74)
wget https://github.com/joan2937/pigpio/archive/v74.zip
unzip v74.zip
cd pigpio-74
make
sudo make install


If the Python part of the install fails it may be because you need the setup tools.

sudo apt install python-setuptools python3-setuptools


To check the library
These tests make extensive use of GPIO 25 (pin 22).  Make sure nothing, or only a LED, is connected to the GPIO before running the tests.  Most tests are statistical in nature and so may on occasion fail.  Repeated failures on the same test or many failures in a group of tests indicate a problem.


sudo ./x_pigpio # check C I/F

sudo pigpiod    # start daemon

./x_pigpiod_if2 # check C      I/F to daemon
./x_pigpio.py   # check Python I/F to daemon
./x_pigs        # check pigs   I/F to daemon
./x_pipe        # check pipe   I/F to daemon


To compile, link, and run a C program
gcc -Wall -pthread -o foobar foobar.c -lpigpio -lrt
sudo ./foobar


To start the pigpio daemon
sudo pigpiod
To stop the pigpio daemon
sudo killall pigpiod

github
git clone https://github.com/joan2937/pigpio

Raspbian (raspberrypi.org image)
This may not be the most recent version.  You can check the version with the command pigpiod -v.
sudo apt-get update
sudo apt-get install pigpio python-pigpio python3-pigpio
