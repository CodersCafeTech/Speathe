Speathe : Speaking Through Breathing
=============
An innovative and evolving communication method for the paralyzed who are gone speechless after paralysis. Even if there are methods for the paralyzed Speathe lends a helping hand by converting one's breath into auditory sounds and transferable texts. I hope there will be great evolution of this code and I request all the enthusiasts to work upon this to make this an effective communication for our paralyzed fellow beings.

Hardware Components
---------------
![alt text](https://hackster.imgix.net/uploads/attachments/575957/untitled-1_i6ofaysauf_7rMjIBfOOw.png)
Walabot will listen to the breath and classify it to short and long breaths. Raspberry will assign dots and dashes to short and long breaths respectively and appends them to form an alphabet. There are collections of 3 lettered acronyms which have predefined meanings to simplify the communication. Raspberry will determine the word speathe by user and assigns a value for a variable and posts the data to the server running in python. The mobile application is developed using react-native which sends continuous requests to the server seeking the value of the variable. Whenever a not null value is received mobile app displays it. We also provide extension for people to reply back to paralyzed by posting the text typed by user back to server and pronouncing it loudly to the paralyzed.

Software Developement
---------------
**1. Setting up Walabot SDK and Programming using Python**

 If you don't have the Python IDE installed, Python3 is available at : https://www.python.org/downloads/

 Once that's done, you can download the Walabot SDK for your OS. Detailed information about the Walabot Python API is available at :  https://walabot.com/api/_pythonapi.html

 Once you've installed the.deb file you can find various example programs written for both C++ and Python in the source directory.The    example programs are also available on the Walabot API website. For this project, I would recommend going through Breathing example.

**2. Breath detection and letter matching**
   
   The ability of walabot to determine energy of breathing is used to determine long and short breaths. We'll take 10-15 successive loops  and if in them the energy is considerably high than a threshold value then it is assigned to be long breath and if energy is lower than  threshold it is a short breath. In that for these one time calibration may be needed for each person.

   After detecting long and short breaths successive breaths and arranged in an array with '-' for long breaths and '.' for short breaths which may form a Morse code like ['-.-.-']. Specific Morse code patterns and predefined for letters and if breaths matches them that letter is pronounced.

**3. Letters, Words, Sentences, Feelings**
  
  We in the first version of Speathe, have developed three lettered acronyms for common phrases used in day to day life, so that the paralyzed will not speathe too much. If a three lettered acronym match is found the value of variable which is taken by mobile application is replaced with the corresponding phrase. Thus an effective communication is possible for those who are fully paralyzed.

**4. Server**
  
  The server is running on raspberry pi and is completely controlled by python. Flask module is used to run the server in Raspberry Pi. A static IP is set on Raspberry Pi and server is started on some port (say 80).

  *How to set Static IP*
    
   1. Type `sudo nano /etc/dhcpcd.conf` at the command prompt.
    
   2. Scroll to the bottom of the script, and add the following lines:

        ```interface eth0
           static ip_address=192.168.43.211
           static routers=192.168.43.1
           static domain_name_servers=192.168.43.1
           interface wlan0
           static ip_address=192.168.43.211
           static routers=192.168.43.1
           static domain_name_servers=192.168.43.1
         ```

   3. Save the file with `ctrl + o` and then exit nano with `ctrl + x`.
   4. Reboot with `sudo reboot`.

**5. Mobile Application**

   The mobile application is developed in react-native. React-native requests for the value at the same port of server. When a value is found it is displayed in the User Interface. And if user wants to return something back, react-native post the data to some variable in server and python code checking the value of that variable will pronounce it louder so that the paralyzed and hear and make a reply, if needed.
 

![Mobile app searching for client](https://hackster.imgix.net/uploads/attachments/576005/whatsapp_image_2018-09-09_at_10_24_48_pm_kqa689yPsb.jpeg?auto=compress%2Cformat&w=680&h=510&fit=max)


![App recieved message from paralyzed](https://hackster.imgix.net/uploads/attachments/576007/whatsapp_image_2018-09-09_at_10_24_49_pm_usyYJVajwx.jpeg?auto=compress%2Cformat&w=680&h=510&fit=max)


![Message to paralysed](https://hackster.imgix.net/uploads/attachments/576010/whatsapp_image_2018-09-09_at_10_24_49_pm_(1)_IVA76GR4lR.jpeg?auto=compress%2Cformat&w=680&h=510&fit=max)


**6. Testing**
   
   Run the python files in Raspberry Pi and Set a static IP address for your Raspberry Pi. Change the IP address and port address in the JavaScript code and render the apk. In my case I have set IP address to 192.168.43.211 and the debug apk is given in the repository. After the apk is generated connect Raspberry Pi to android device via Wi-Fi and connect walabot to Raspberry Pi. Just open the application and start Speathing.
 
 
 [![Speathe Demo](https://hackster.imgix.net/uploads/attachments/576005/whatsapp_image_2018-09-09_at_10_24_48_pm_kqa689yPsb.jpeg?auto=compress%2Cformat&w=680&h=510&fit=max)](http://opxyc.cf/speathe/sample.mp4)
 
 

