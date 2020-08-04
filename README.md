# Dynamixel-Shield-Setup
Use Robotis Arduino Shield to find any connected servo and set to known baud rate and ID. In most cases, users will want a specific baud rate, which does not change, and will want many different ID's. So this program is set for one baudrate which you can adjust when first loading it, then it will ask for the ID each time it is run.

Note: It does NOT communicate via the Arduino USB adapter during normal operation, it uses an external USB / TTL serial adapter instead. 

BOM
qty | item | price | source
----|------|-------|---------------
1   | Arduino | ~$25 | Arduino.cc (please support Arduino by buying real parts?)
1   | Shield  | $20  | http://en.robotis.com/shop_en/item.php?it_id=902-0146-000
1   | TTL Serial USB adapter | ~$2 | Google CP2102 or e.g.<BR> https://www.amazon.com/Diymore-Converter-Support-Windows-Arduino/dp/B0776T51YT/ref=sr_1_9
1   | 12V adapter | ~$9 | Google AC/DC power adapter. e.g. <BR> https://www.amazon.com/Converter-Cigarette-Lighter-110-240V-Adapter/dp/B07DWXRD5F/ref=sr_1_4
1   | 4 pin JST cable | $? | ???

See: 
https://emanual.robotis.com/docs/en/parts/interface/dynamixel_shield/ 
for instructions and connections. 

### BUILD:
1. Install Dynamixel libraries into Arduino IDE (must be 1.8.5 or up) via menu: "Sketch" / "Include Libraries" / "Manage Libraries" and then search for Dynamixel. Select and then "Install" the DYNAMIXEL2Arduino and then DynamixelShield 
2. Download the .ino file above and place in folder of the same name under Arduino folder. e.g. Documents\Arduino\DynamixelShieldSetup\DynamixelShieldSetup.ino and open it. 
3. Modify the NEW_BAUDRATE value around line 50 to the one you want. 
4. Connect the Arduino /without the shield/ and program it. 
5. Connect the TTL serial adapter TTL Serial USB adapter to J3 on the shield. This is the small 4 pin connector off by itself near the green power terminal. 

Shield J3 pin | TTL adapter pin
-----------|----------------
G | GND
V | don't connect
R | TX
T | RX

6. Cut the 12 volt adapter wires and strip them, then /carefully/ test to see which wire is positive and which negative before connecting to the shield. Getting that backwards will cost rather a lot. 
7. Plug the shield onto the Arduino.

### OPERATE:
1. Plug the TTL Serial adapter into your PC USB. You will need to configure a serial terminal program like PuTTY, or RealTerm, or whatever to 115200 N 8 1 on whatever port that shows up on. 
2. Plug in a servo 
3. Check that the SW2 "UART" switch is in "DYANMIXEL" vs "UPLOAD"
4. Turn on the AC adapter and verify that the Arduino power LED comes on. You should see "Enter new ID" on your terminal program.
5. Turn on the SW1 servo "POWER" switch. Check that the Servo LED blinks. 
6. Enter an ID and watch it find the servo, change the baud rate, then change the ID.

### EXAMPLE:
In this case, NEW_BAUDRATE was set to 115200. After pressing re-set on the Arduino, the operator enters "3" at the "Enter new ID:" prompt. 

````
Enter new ID:3
SCAN PROTOCOL 2
SCAN BAUDRATE 1000000
ID : 1, Model Number: 1080
Baudrate has been successfully changed to 115200
SCAN PROTOCOL 2
SCAN BAUDRATE 1000000
SCAN BAUDRATE 57600
SCAN BAUDRATE 115200
ID : 1, Model Number: 1080
ID has been successfully changed to 3
Total 1 DYNAMIXEL(s) found!

````

<img src="https://user-images.githubusercontent.com/419392/89340621-de190500-d654-11ea-8f35-cad97d78e372.png">

<img src="https://emanual.robotis.com/assets/images/parts/interface/dynamixel_shield/pinmap.png">
