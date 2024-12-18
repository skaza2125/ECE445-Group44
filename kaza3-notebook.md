# Week of 9/30:
This week was focused on finishing up our design document. We realized there were some gaps in our design, specifically around the safety aspects of the project, as well as the formulaic areas of our design document. We had not yet gotten to the calculations of our heating element which is the nichrome wire wrapped around stainless steel tubing. Therefore we did not know who wmuch power we weould need in our deployment. So we had to run these calculations and calcualte the power draw as well as the thermal output of our nichrome wire. Once we did these things, we added them into our design document as to show that we had verified our theories of heat transfer, and proceded to refine the document. We also were scouting potential enclosures. 

After working with the ECE supply shop and reviewing the options they offered, we realized that their enclosures might not fully meet our specific requirements due to sizing constraints. The primary issue was that we needed a larger area in the center of the box, along with a taller structure to allow for improved airflow and enhanced thermal transfer. These factors are critical to ensure proper heat dissipation and maintain optimal temperatures for our components. After searching online, we found a more suitable option on Amazon, which better fit our needs in terms of both the size and thermal management capabilities. We believe that this new enclosure is the ideal option, and will be working with Greg from the machine shop starting next week to look into how we can moutn our steel rods to the inside fo the box in a safe and secure manner.

# Week of October 2th:
We were still debating on our parts, but we decided to start modelling our enclosure, we had some difficulty finding an enclosure that worked for our purpose at the machine shop, so we had to seek outside sources. Furhthermore this is when we were still looking for blower units, but we are running into issues since many of the units that we are looking at are either very loud since they are industrial style blowers or do not move enough air flow. We found some high CFM fans that we believe will work, so we will probably be proceeeding with these that way we can move enough air around the enclosure while still retaining the low noise barrier.

Below you can see some of the CAD models that I have mocked up in order for us to get an understanding of our dimensions. We also use this CAD and Ansys to perform flow simulations so we can see how the air is going to be flowing and how the thermial transfer will occur.

![Enclosureotherside](https://github.com/user-attachments/assets/880336f1-e831-4f5b-8cb8-5975d4a616bb)
![Enclosiure v1](https://github.com/user-attachments/assets/9f50b3e3-2692-46cb-b5bb-763b7860bdf4)


# October 10th:
We met together in the ECEB, to work on the PCB design and schematic. We ran into some issues since we were unsure if we wanted to have the Buck Converter on the board or if we wanted to have it as a seperate module. We preferred seperate module since it allows us to have easy troubleshooting and unit testing, and the circuit for the buck converter is fairly complicated, so having to solder all of those SMDs perfeclty would be really difficult. Furthermore our PCB is already pretty complicated because we have alot of control aspects like the ESP and the ATMEGA module on the board. For now we decided to leave it on there but we also have the option to add it externally. 

# October 12th:
Today, we received the fans we ordered and immediately began testing to establish a baseline for their airflow performance. To conduct the test, we powered the fans using a bench PSU in the senior design lab. Our goal was to assess the baseline airflow measurment so we could see if this would move enough air that would make a difference when snaked up the tubing underneath the bed. We decided that if we had two fans that were blowing into a insulated container with smaller volume, we would have enough airflow. Furthermore we looked into the Frequency Generator(FG) pin on the pan, and how we could read this signal. It was very convenient since these are PWM fans that we can control the speed off, and we can also get a live speed reading off the fans using the FG pin, so we can create an accurate feedback loop system.

# October 17th:
Today we had another meeting with Greg at the machine shop, in order to discuss the parts that we need, and how we can mount he steel rods to the inside of the container. One thing we needed to make sure is that we dont transfer too much heat from the heated rods into the metal box itself, in order to ensure this we need to make sure we have an insulation material between the rod and the attatchment mechanism. Greg has showed us the potential steel rods, and we have also discussed the holes that we need for the intake for the fans and the exhaust vent. Once all the parts arrive we can take them to the machine shop and start building a unified enclosure.

# October 21st:
We had our final meeting with Greg just to get precise dimensions on the enclosure, the cut outs that we need etc. The rods should arrive tommorrow or later this week, and the enclosure should also arrive soon. Once these parts arrive, we can pick a day and start working with greg to incorporate them all together into our final product. We have also submitted the PCB for Second Round printing, the DRC has been verified and it passsed all checks on PCBWay, we decided to still build the buck converter circuit onto the board just in case, but we will for preliminary testing purposes use an external buck converter so that if something is wrong, we can unit test, with a known good buck converter. 

# October 27th:
Today we submitted our SMD orders to both the supply shop and on DigiKey. At this point we are mostly waiting for the arrival of our parts, so we are at a standstill in which we cannot proceed until the parts we ordered through myECE arrive, we are still discussing, but we cannot iterate since we do not have a PCB to test/work on. We are however working on our microcontroller, we ordered our temperature sensors seperatley for our temperature response system, so we started breadboarding out the connections so that we can start understanding how all these sensors communicate with each other and how we can read the data coming off of the sensor and use it in our PID algorithims

# November 11th+12th
We received our finished enclosure from the machine shop today. It was very well made, and it adhered to our specifications. We realized we had overlooked certain aspects, such as a hole to route the nichrome into the enclosure, since the PCB itself would be on the external sides of the box. This meant that we needed to drill an additional hole. Now that we had our fans back, we started on getting the fans powered, so that we can start getting an idea of the airflow that we would generate, and if the fans were going to be enough. We had many issues when were diagnosing the fans and we consulted our TA on these issues as well. The first issue is that our fans were 12V fans, but for some reason when they were powered from the bench top power supplies, the fans would drop to 6V. We spent alot of time debugging this issue, and eventually found a solution, but not an answer to the intial problem. When we powered the fans off the PSU that was incldued in our lab supply kits, we did not experience as severe of a voltage drop issue. Though the voltage dropped a little bit, this is to be expected, it still stayed near the operating voltage of the fan.

<img width="408" alt="Screenshot 2024-12-10 at 22 52 26" src="https://github.com/user-attachments/assets/3fa9a87a-0688-4dd4-b791-1340ea53c867" />




We ran into some issues on this, specifically library issues, where the library we wanted to use(LEDC) was deprectated in later versions of our boards firmware, but this was resolved and we continued on. It took trial and error in the parameters of the PWM wave that we were generating, such as figuring out what the ideal PWM frequency and resolution that we needed in order for the fan to accept the PWM signal. Once we got these working, we hooked up the fans, and through manipulating the duty cycle of the outputted PWM wave, we were able to speed up and slow down the fans accordingly. This gave us a great foundation for the speed control that we were aiming to achieve. 

LEDC Code to setup the PWM GPIO pin and generate the signal:
![image](https://github.com/user-attachments/assets/7ebcde03-91b4-4511-8dac-d1afed247baf)

Examples of two different PWM Waves with Two different Duty Cycles:
![thumbnail](https://github.com/user-attachments/assets/485c1546-49c8-4ccd-8ce8-df8d78bf807f)

![thumbnail](https://github.com/user-attachments/assets/f5f84a51-0428-4ca6-b262-ea0d4957d594)


# November 13th
On this day we started testing our Nichrome and power supply, we wanted to see if we would generate the amount of heat that we needed in order to make a reasonable and acceptable temperature delta between intake and exhaust temperatures. We had some inital issues with setting up the nichrome and how we would be testing the nichrome. Furthermore we had to figure out a length of nichrome that would heat the wire but not MELT the wire. This was a tough challenge than anticipated, since we had multiple lengths either melt shortly after plugging it in, or on the opposite end, we had some lengths just not heat enough. There were multiple hours spent testing this functionality and trying to find the right temperature.
![thumbnail](https://github.com/user-attachments/assets/44093f65-f4b6-4061-810b-42fe0a02ac1b)

![image](https://github.com/user-attachments/assets/f93a1deb-f22f-475f-bcf1-4f65e2680700)

As you can see in this image, this is one of the problems that we ran into. We didnt realize it at the time, but the power from the power supply ended up using the steel as the path of least resistance, and so the nichrome that was making contact with the steel, would not have any current passing through it, instead it would go through the steel itself. This was a huge problem as the steel would often draw more power than the nichrome could handle, which would result in the nichrome ends that were NOT in contact with the steel burning(and melting) cause the contact to be broken. Not only would this break the heating system, it was also HIGHLY unsafe, so we had to come up with an alternative way, or a solution to this contact with the steel.

# Week of November 18th
We previously realized that the contacting with the steel was a issue that crippled our entire project. This was because instead of the nichrome heating, the current would travel through the steel pipe, therefore nullifying our project. We did research and concluded that due to time constraints getting a new pipe element was not only not feasible, but would also be rather expensive. We then decided to proceed with painting the existing steel rods with a thermally insualtive and electricall non conductive material. We choose Rustoleum bed liner for this application. Furthermore we also decided to start testing with different gauges of nichrome wire. We need to experiment with different gauges of wire so that we can find the optimal setup. One that gets hot enough to heat the air, but also not too hot, so that it melts. We ordered more 18 gauge wire and are waiting for that to appear to start our testing with 18 gauge wire.

Another huge step today was getting our PCB in, we ordered our 4th and final revision and I was able to get all the componenents soldered. We had a couple different changes in this version of the PCB, we swapped to all screw terminals, and added a JTAG connector to flash the ESP controller. This made is easier than soldering the USB-C port onto the PCB. We also did alot of debugging today, since the JTAG connector wasnt working right away, and we needed to tune the baud rate and connection settings to fully get it to communicate.

Lastly, we worked on creating our PWM cure that would dictate how our system was heating and cooling. Since we knew we had controllable nichrome heating, this meant that we needed to figure out how to automatically turn the nichrome on and off, as well as crucially, ramping the fans up and down. This was important since we did not want to let the nichrome get so hot that it melted, or cause the paint to melt, but we also did not want the fans to move too much air, otherwise the air would not be heating. While we were testing our different gauges of wire, we also were testing different PWM curves that would get us our ideal temperature and keep it stable. Below is the PWM curve that we created and finalized on for our length of nichrome, this ensures that the exhaust temperature always reaches the goal temperature we set, while also incorporating safety measures to ensure that if we exceed safe operating temps, the fans ramp up to cool the nichrome as fast as possible.

<img width="560" alt="Screenshot 2024-12-12 at 15 35 41" src="https://github.com/user-attachments/assets/61152488-7a63-48cc-9eca-3b40b4972e48" />


# THANKSGIVING BREAK
Over break, one of our teammates was on campus, and we were working on getting our MOSFET issue resolved. We initially thought that we could use a MOSFET to control our nichrome and turn it on and off, however in our testing, we found that when we pushed the current through the mosfet into the nichrome, after about 10 seconds the MOSFET got either, incredibly hot, or simply exploded. We were not sure at first why this was happening, but after talking with our peers and consulting the data sheet we saw that the on resistance of the mosfet is inversely proportional to the gate voltage. So the ihgher the gate voltage, the lower the resistance of the mosfet. But since we were powering the pin of the mosfet off our ESP, it was only 3.3V, and this meant that the MOSFET had high ON resistance, leading to higher power disapated by the MOSFET, and the MOSFET would explode. This is represented by the equation below. 
<img width="845" alt="Screenshot 2024-12-12 at 13 39 26" src="https://github.com/user-attachments/assets/539f0b28-22a6-4d31-bd74-aab9d3c95f91" />

<img width="426" alt="Screenshot 2024-12-12 at 13 36 04" src="https://github.com/user-attachments/assets/0c8c9f4a-e966-4003-8083-8b1965b1b505" />

When we were testing in the lab, we realized that if we powered the MOSFET via 10V, the MOSFEt would no burn anymore, but it would get incredibly hot. After discussion, we decided that since we did not need the incredibly high switching rate that the MOSFET provided, we could instead swap to a physical relay switch that would be controlled via a IO signal from our ESP32 Module. THis allowed us to push the same amount of power through the nichrome, without worrying about the temperature of the MOSFET and the ineffeciency of adding even more buck converters to step down 24V to 10V to power the mosfet.

![image](https://github.com/user-attachments/assets/3dfc2c87-2b25-419c-8a3e-bfeb3f933a4a)


Once we got our relay. we also wanted to test if we could place two nichrome wires in parallel, in order to split the same amount of power through them, and cause an overall increase in heating, we tested this outside of the enclosure with our nichrome wrapped around our freshly coated steel rods, as you can see, in this photo they are now black, as a result of the rustoleum coating that we applied. 

<img width="697" alt="Screenshot 2024-12-12 at 13 43 35" src="https://github.com/user-attachments/assets/f9d2fb68-8a59-471b-9b5d-255f7f07477b" />

The coating not only worked to prevent MOST of the shorting of the nichrome, but having two pieces of nichrome in parallel also worked to our benefit, allowing us to power both off the singular 10A relay, controlled via the ESP.

# Monday, December 2nd

Today we started our final assembly of our unit, we worked through the night to get the box assembled, but we ran into many issues. First of all, our PCB randomly broke. we aren't sure why, as our ESP is still outputting signals, but somehow refuses to be programmed. We were unable to debug why the ESP is behaving this way, so we ended up having to solder a brand new PCB. However because today is the day before our demo, we do not have the componenets to solder on the integrated PCB buck converter onto the system, so we ended up having to use external power converters in order to power certain aspects of the PCB, like the 12V fans. However, once we soldered everything on, we tested the ESP and saw that it was accepted our code, as well as succesfully reading out of our sensor, so we had a working PCB, and went on to final PCB Assembly. 


![image](https://github.com/user-attachments/assets/f91979b5-6048-43fe-b163-45928f0d40d4)

The final problem that we ran into was that our buck converters kept exploding. In a literal sense. We were not pulling even 1A through the external buck converter, but as shown above, it exploded in our face. This happened twice, with two DIFFERENT buck converter models, so we are unable to narrow down why. However when we wired the final buck converter, it seems to work and is stable after running for almost an hour. 

<img width="418" alt="Screenshot 2024-12-12 at 15 13 36" src="https://github.com/user-attachments/assets/d30e02e8-c432-4aa4-be86-edeb6be6df59" />

We were able to get the final project working, and meet all of our high level requirements. The project was incredibly fun and I enjoyed working with my teammates, as well as learning alot about the various aspects of electrical, thermal, and firmware engineering!

![image](https://github.com/user-attachments/assets/1b59f8bf-4f0b-4e46-9687-42c233d38076)





