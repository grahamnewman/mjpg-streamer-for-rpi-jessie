# Mjpg streamer for Rpi Jessie
## How to get an mjpg streamer working on a Raspberry Pi 3 with Debian Jessie OS in plain English. 


![3099-02](https://cloud.githubusercontent.com/assets/7692766/18231290/e8dfdd56-72ad-11e6-8083-13a78159eaf8.jpg)


## This repo is work in progress 

ssh into your pi and start with thse usual:
```
sudo apt-get update
```
Pull a couple of libraries:

```
sudo apt-get install libjpeg62-turbo-dev
```
and
```
sudo apt-get install cmake
```
Then clone the mjpg streamer from <a href="https://github.com/jacksonliam/mjpg-streamer.git" title="jackson liam"></a> and create a folder for it, all within in the same command:
```
git clone https://github.com/jacksonliam/mjpg-streamer.git ~/mjpg streamer
```
change the directory from home to the mjpg-streamer:
```
cd mjpg-streamer
```
Then into the mjpg-streamer-experimental:
```
cd mjpg-streamer-experimental
```
and build it:
```
sudo make clean all
```
make a new directory in the opt directory. Opt holds optional software and packages that you install that are not required for the system to run. In the old days, "/opt" was used by UNIX vendors like AT&T, Sun, DEC and 3rd-party vendors to hold "Option" packages;
```
sudo mkdir /opt/mjpg-streamer
```
Move everything into the new new directory:
```
sudo mv * /opt/mjpg-streamer
```
now comes the tricky bit, change to the home directory:
```
cd
```
Copy this line:
```
LD_LIBRARY_PATH=/opt/mjpg-streamer/ /opt/mjpg-streamer/mjpg_streamer -i "input_raspicam.so -vf -hf -fps 15 -q 50 -x 640 -y 480" -o "output_http.so -p 9000 -w /opt/mjpg-streamer/www" > /dev/null 2>&1&
```
Open te file from the command line:
```
sudo nano /etc/rc.local
```
and paste the code before the exit 0 line at the bottom

This line of code holds pramaeters that can be hang to your needs
insert screen grapb here
where
xxx
x
xx
Reboot the Rpi:
```
sudo reboot
```
go to your ip address:9000 and the mjpg-streamer will be up and running. That's it.
