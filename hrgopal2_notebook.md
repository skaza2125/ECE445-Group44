# ECE445-Group44
Lab Notebooks of ECE445 Fall 2024 

**August 29th**
General description of idea, brainstorming
- Weird Rubik’s Cube solver
- Drone?
- Glove/camera translating sign language
- Depth sensor with display/laser for use in labs
- Sunglasses with visual display?

**September 1st**
Settling on an idea:
We have decided on the self-heating bed, through ventilation. Need to expand more on heating element, could be heating coils or some other material. Box will be below the bed, while ventilation will go under blankets and over foot of bed (clipped on by clamps). The main components will be a ventilation system, heating system and the controller, all of which work together to produce either room temperature air or heated air. We will be using an ATMega328, as it seems to have enough pins to accomodate our entire design. Additionally, we need to find ambient temperature readers such that reads can happen both inside the enclosure as well as outside.

**September 5th**
Working on design document:
Finished the components and block diagram. Were initially considering the ATMega328, but may be better to switch to a ESP32 module in case of simplicity.

**Week of 9/9**
Working on proposal in order to submit before deadline of Thursday. We've drawn up a simple schematic of what the system should look like, with the components box and the bed clamp being mounted on the foot of the bed.
![image](https://github.com/user-attachments/assets/9f151fe5-813a-4cf1-a9de-f5f05e997b6b)

Our components are currently the heating and ventilation system, both of whchi work in tandem for the system to be called successful. The heating system will mainly be a heating coil that has a thermistor to sense when our air gets to the correct temperature, while the ventilation subsystem requires two fans to keep itself running. There will be a speed modulator to communicate with the fans, one supplied by running PWM into the fans from the MCU itself.

![image](https://github.com/user-attachments/assets/f80e0a53-0fac-49a9-810d-9f68b52080c1)

**Week of 10/7**:
This week focused on preparing and presenting the design proposal to the TAs and instructors during the design review. The feedback and some of the questions from the review gave us the final adjustments to the system's design, which we then integrated into our block diagram and started on the part selection. We mainly discussed the airflow system, the integration of nichrome wire heating elements, and control using the ESP32 microcontroller. As such, I started on PCB design and completely integrated our system within a couple days, focusing mainly on the serial converter line and the outputs to our temperature sensors/fans. 
![image](https://github.com/user-attachments/assets/45bb87a7-b958-4705-9213-b734cad855d8)


**Week of 10/14**:
The first iteration of the PCB was designed and sent for manufacturing. This design integrated the fundamental components necessary for controlling the nichrome wire heating elements and managing temperature sensors. Such that we wouldn't waste too much time, we began prototyping the heating element and airflow mechanisms in parallel, ensuring that the system's core concepts were functional.

**Week of 10/21**:
Based on some of the feeedback from outside sources on the first PCB design, a second round of PCBs was ordered with corrections to improve component placement and routing. The team continued testing the nichrome wire heating system, experimenting with its wrapping around steel pipes and verifying temperature regulation with PID controls. We mainly wanted to do an on/off system, since it seemed the simplest and wouldn't require complex calculations to be made. Overcomplicating our design was very much a problem that we didn't want to get into, so we decided against going with a two/three component PID system and started with just a derivative controller. 

**Week of 10/28**:
Both the first and second round PCBs arrived this week, which allowed us to solder a couple components on and allow for testing. We realized that the serial converter system may not be the most reliable, so we backtracked and decided on removing it altogether, having JTAG lines in place of it. Additionally, the ESP32 doesn't seem to need a serial converter and may simply need twin data lines running from the USB-C to the chip, which means we can get rid of it altogether. We may also remove one of the buck converters, since we can route our power externally and disallow too many component being routed on the same board without space for each of the terminal blocks. During this week after our PCB testing, our attention shifted to refining the airflow system, ensuring that the fans effectively pushed heated air through the steel pipe enclosure and vented it under the bed. Testing also included verifying sensor accuracy in capturing temperature variations around our predicted enclosure, mostly making sure that the temperature sensors would work in our environment.
![image](https://github.com/user-attachments/assets/fff8ba88-73b5-4d7e-8610-09dddeebba8e)


**Week of 11/4**:
We worked on the rework of the PCB this week, taking out one of our power converters and completely removing the serial converter. Our individual progress reports were submitted, documenting each person's contributions so far. The team also began integrating the ESP32 into the system, testing its ability to manage the nichrome wire heating, fan control, and sensor data processing. The temperature sensor didn't seem to be too much of an issue, since the one wire data bus allowed us to put multiple on the same data line without having to worry about splitting off the data line or using separate ones. The fans blow a good amount of CFM, although we may have to consider the noise to airflow ratio. Our heating on the nichrome require a sweet spot that we're yet to find, but it's also taking an immense amount of power, which we're not sure our MOSFET or board can handle if we are to put it directly interfaced.
![image](https://github.com/user-attachments/assets/de669739-a89c-477b-8af1-214fab02829f)
![image](https://github.com/user-attachments/assets/2e798c36-b2d8-4b54-bce6-28fa6c7df591)



**Week of 11/11**:
Our final round of PCB orders was placed this week after confirming what made our previous designs fail and addressing some minor layout issues. We hope that it'll come soon, since Thanksgiving is coming up and most of us will not be here to test anything or solder anything to boot. The steel pipe enclosure was sent to the machine shop for fabrication, marking a significant milestone in the project's progress. Testing focused on finalizing the heating system and ensuring consistent airflow through the venting system. Our venting system should work quite well, since the air within the enclosure is reliably being pushed out within a smaller space. A couple of calculations were needed to be done for the nichrome, mostly simple V=IR to find out the current running through the wire at any given point. The power supply we're using currently is a 24V 20A power supply which _is_ quite large, but if our calculations are correct, the nichrome is conducting almost 6-8 amps constantly. The resistance is usually about 3.5 amps to allow the nichrome to glow red and seriously dissipate heat. Additionally, we realized that the steel we're wrapping the nichrome around is quite conductive, which foils a couple of our plans of heating it since the nichrome conducts through the steel rather than itself. The steel's resistance is not necessarily _lower_ than the nichrome's, but once enough nichrome is wrapped around the steel, the electricity takes the path of least resistance (usually shorting through the steel and leaving the nichrome unheated). As a result, we've bought Rustoleum, which has properties of both thermal and electrical insulation. In theory, this should insulate the steel pipe and allow it to simply act as a larger surface for the air to pass over and heat more quickly.  
![image](https://github.com/user-attachments/assets/6d38ba03-4734-4322-bd8e-2e6c59d43db4)


**Week of 11/18**:
The enclosure was received back from the machine shop, allowing the team to assemble the system fully. The final PCB iteration arrived and was soldered, enabling full integration of all components. The ESP32 was successfully flashed with firmware, although our JTAG input didn't work initially due to some soldering mistakes. The tests demonstrated functionality for nichrome wire heating, airflow control, and temperature monitoring under certain circumstances. The team conducted our mock demo as well, mostly showcasing the enclosure and how hot the nichrome actually got. The system is essentially fully built currently, but our main issue is with the MOSFET that conducts heat through the nichrome wire. The MOSFET is rated for our voltage and power, but it requires a heatsink even for the powers that we are running through it, one that we don't have. While experimenting, we burnt most of these power MOSFETs since the heat travelling through the substrate of the MOSFET was simply too high, conducting 62.5 C/W through Rds. Our calculations yielded a whopping 700C being shunted through our MOSFET, which simply will not work for our purposes. We will instead have to step back and get a relay externally to switch our power into the nichrome, rather than using just the MOSFET as a switch.
![image](https://github.com/user-attachments/assets/95906402-552d-4da0-a268-0b09dd80be5e)
![image](https://github.com/user-attachments/assets/5a1c5cee-07b9-43a6-a62e-4de97e3e33cc)
![image](https://github.com/user-attachments/assets/d6610a46-8f88-4107-a561-31d747f31205)
![image](https://github.com/user-attachments/assets/fb6706f5-f4d9-4d83-8669-627afeb79df3)


**Week of 11/25**:
This week involved rigorous testing of the fully assembled system to show that it was able to work under strained conditions. A couple of tests confirmed that the system successfully heated and ventilated the area:
- We let the product run for around 10 minutes to see if the new relay would work under a longer time than the MOSFET
- Tested different lengths of nichrome to see which gauge would be optimal along with which resistance would heat and not melt or heat insufficiently
- Used the oscilloscopes to check the healthiness of the PWM signal communicating to the fans from the ESP
The project is relatively ready for demo, but we also worked on getting the PCB enclosure mounted to the rest of the product. Along with this, new connectors were crimped for both the relay, external buck converter and power supply inputs. Of our high level requirements, we successfully fulfilled all three:
- Able to regulate temperature within 3deg of 90F, and cool down if user requires non-heated environment
- Power requirements severely under 750W, measuring in aroun 400 at most.
- Under 60dB consistently
![image](https://github.com/user-attachments/assets/8e5ff1bc-fd26-4dfe-938b-6b512e336c36)

![image](https://github.com/user-attachments/assets/33758218-0c50-42eb-ae0f-318532051c01)

 **Week of 12/2**:
Our last week on the project consisted of last wrap ups and tests we needed to do before our demo and presentation. A couple of issues cropped up during these final checks, mainly the buck converter snapping due to a short we accidentally caused, along with overvolting the ESP. Toasting the ESP was an issue that could only be solved by replacing the circuit board altogether, a lengthy process that resulted in us completely deconstructing the first and replacing the parts on a new PCB. Additionally, we had a couple of spare bucks on hand which did come in handy to replace our broken one. The end product worked within our high level requirements, and worked within demomonstration during our final demo.

https://github.com/user-attachments/assets/5ad44222-92b0-4147-9c3f-b190f8b11859


