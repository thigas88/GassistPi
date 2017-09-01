# GassistPi

*************************************************  
#LET'S GET STARTED!  
*************************************************  

*************************************************  
#FOR USERS WITH AIY KIT START HERE  
*************************************************  
#UPDATE KERNEL  

sudo apt-get update  

sudo apt-get install raspberrypi-kernel  

#RUN SCRIPTS FOR VOICE HAT  

#download voice hat audio drivers from the github page onto a thumb drive  

#open the folder and copy folders named "audio drivers" and "src" and paste it onto /home/pi directory  

#FOR INSTALLING AUDIO SCRIPTS COPY PASTE BELOW IN TERMINAL  

cd /home/pi/audio-drivers/scripts  

chmod u+x ./configure-driver.sh  

chmod u+x ./install-alsa-config.sh  

sudo ./configure-driver.sh  

sudo ./install-alsa-config.sh  

#(run the above 2 commands till you get .bak notification in the terminal)  

#RESTART RASPBERRY PI  

#CHECK THE SPEAKER'S WORKING IN TERMINAL  

speaker-test -t wav  

*********************************************************************  
#COMMON PROCEDURE STARTS FROM HERE  
#(FOR BOTH VOICE HAT AND NON-VOICE HAT USERS)  
**********************************************************************  
FOR USERS WITHOUT AIY KIT START HERE AFTER SETTING UP AUDIO DEVICE
**********************************************************************   

#1.download credentials--->.json file  

#2.place the .json file in/home/pi directory  

#3.rename it to assistant--->assistant.json  

#IN TERMINAL:copy paste the following commands one by one  

sudo apt-get update  

sudo apt-get install python3-dev python3-venv  

python3 -m venv env  

env/bin/python -m pip install --upgrade pip setuptools  

source env/bin/activate  

#TO ACTIVATE LED FOR HOTWORD DETECTION ..CONNECT LED to GPIO 25  

pip install RPi.GPIO  

#Get the library and sample code  

python -m pip install --upgrade google-assistant-library  

#INSTALL AUTHORIZATION TOOL  

python -m pip install --upgrade google-auth-oauthlib[tool]  

#RUN THE TOOL(client id already renamed to assistant) just copy paste below  


google-oauthlib-tool --client-secrets /home/pi/assistant.json --scope https://www.googleapis.com/auth/assistant-sdk-prototype --save --headless  

#COPY THE LINK FROM TERMINAL AND PASTE IT IN THE BROWSER  

#COPY THE AUTHORIZATION CODE FROM THE BROWSER AND PASTE IT IN THE TERMINAL  

#DOWNLOAD THE src FILE PROVIDED IN from the github page AND PLACE IT IN /home/pi     
#MAKE gassist.sh EXECUTABLE  

cd /home/pi/src  

chmod u+x ./gassist.sh  

#CLOSE AND REOPEN TERMINAL  

sudo /home/pi/src/gassist.sh  

#TEST BY GIVING SOME VOICE COMMANDS BY TRIGGERING "HEY GOOGLE" FOLLOWED BY YOUR REQUEST  

#AFTER EVERYTHING IS WORKING PRESS "CTRL+C" TO COME OUT OF GOOGLE ASSISTANT  

*************************************************  
#Autostart Headless As A Service  
*************************************************  
1. Make the service installer executable  

sudo chmod +x /home/pi/scripts/service-installer.sh  

2. Run the service installer  

sudo /home/pi/scripts/service-installer.sh  

3. Enable the service  

sudo systemctl enable gassistpi.service  

4. Start the service  

sudo systemctl start gassistpi.service  

******RESTART and ENJOY*************************  

************************************************  
#For Neopixel Indicator
************************************************  
#Replace the main.py in src folder with the main.py from Neopixel Indicator Folder.  

#REBOOT  

#Change the Pin numbers in the given sketch according to your board and upload it.  

#Follow the circuit diagram given.  

************************************************  
#Now you have your Google Home Like Indicator  
************************************************  
