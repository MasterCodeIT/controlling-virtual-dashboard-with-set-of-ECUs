#Controlling a virtual dashboard with a set of ECUs.
-ECUs exchange information over the CAN bus.
-Message catalog file describes all messages sent by the ECUs.
-Information about the data sent is included.
-Each board has its own task and is connected to bus.
-VirtualCockpit is added as an additional bus participant.



#ECU0-Monitoring:
-Light sensor: The light value received by the photo resistor connected to this board
should be sent to the bus.
-Door sensor:Two switches represents sensors included in the doors.
One switch for the left door and another switch for the right door.
-This ECU receives the fuel level and the engine coolant temperature.



#ECU1-Stability control:
-RPM: The potentiometer of this ECU should be used to read the RPM value.
This value must be sent to the bus. 
-Gear sensor: Two buttons on this ECU should be used as gear sensors. 
- One button should indicate that the user shifted up. 
The other button is for down shifting.
-In every case a signal including the gear should be sent to the bus. 
-At start up the gearbox is always in neutral (N). The 6-gear transmission should have the
following gears: R – reverse, N – neutral, 1, 2, 3, 4, 5, 6. One byte 
should be used to send the data.
-The Stability Control receives the speed of the drive wheels and the speed of 
the non-driven wheels. 
If the speed difference is bigger than 15 km/h a signal should be sent to the bus. 



#ECU2-Light control:
-Speed of non-driven wheels: The potentiometer is used to determine the speed of 
the non-driven wheels.
-This value must be sent to the bus. 
-The potentiometer value must be mapped to a value between 0 and 300.
-Light mode switch: A switch on this ECU is used as mode switch.
-The mode switch toggles between the manual and the automatic light mode on this ECU.
-This ECU implements two modes.
The first mode is the manual mode. In manual mode the ECU receives 6 signals which 
represent different light states. 
Each state switches a light on or off. A logical ‘0’ received means the light is switched on.
A logical ‘1’ should switch off a light.
-In automatic mode the low beam and the parking light is switched on automatically
if the light value falls below 512. 
-The message with ID 0x101 holds the light value.



#ECU3 – Door Control:
-Fuel level: The potentiometer is used to represent the fuel level of the car.
which is sent to the bus.
-Indicator switches: 3 switches are used to control the state of the indicators.
There should be a switch for the left and right indicator, and the last switch 
should be used for the hazard light (left and right indicator at the same time).
Note: To signalize that an indicator is switched on a logical ‘0’ is sent.
If it is switched off a logical ‘1’ must be sent.  
-This ECU receives the speed of the car and the state of the doors. 



#ECU4 – Engine Control:
-Engine coolant temperature: The potentiometer is used to determine 
the engine coolant temperature and must be sent to the bus.
-Headlight switches: 3 switches should be used as headlight switches.
One switch is used as high beam switch, another one as low beam switch,
and the third one as switch for the parking light.
A logical ‘0’ sent means the corresponding light is switched on and a logical ‘1’ 
should be sent if the light is switched off.
-This ECU should calculate the speed depending on gear and RPM.
The speed value must be sent to the bus.


 
      