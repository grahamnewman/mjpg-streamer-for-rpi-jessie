# mjpg-streamer-for-rpi-jessie
This mjpg streamer works on Raspberry Pi 3 and Kernal 4x

## This repo o work in progress 

pull a couple of libraries
<code>
	```sudo apt-get install libjpeg62-turbo-dev```
</code>
<code>```sudo apt-get install cmake```
</code>
Then clone the mjpg streamer from jacksonliam, a fork from the and create a folder for it
<code>```git clone https://github.com/jacksonliam/mjpg-streamer.git ~/mjpg streamer```
</code>
then change the directoy
<code>```cd mjpg-streamer```</code>
An go into <code>```cd mjpg-streamer-experimental```</code>
build it
<code>```make clean all```</code>
make a directory in the xxxx
<code>```sudo mkdir /opt/mjpg-streamer```</code>
put everything in the new diretory <code>``` sudo mv * /opt/mjpg-streamer ```</code>
now comes the tricky bit, change to the home directory <code>``` cd ```</code>
Copy this line <code>``` LD_LIBRARY_PATH=/opt/mjpg-streamer/ /opt/mjpg-streamer/mjpg_streamer -i "input_raspicam.so -vf -hf -fps 15 -q 50 -x 640 -y 480" -o "output_http.so -p 9000 -w /opt/mjpg-streamer/www" > /dev/null 2>&1& ```</code>

then open the file <code>``` sudo nano /etc/rc.local```</code> before the ``` exit 0 ``` line, paste the copied code in.

The params for this file are xxxx

open up xx on port 9000