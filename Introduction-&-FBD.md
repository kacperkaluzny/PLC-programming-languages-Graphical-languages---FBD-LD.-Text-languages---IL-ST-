# *FBD practical examples*

I this part will be shown some practical examples of using FDB.

### Designing a control mechanism for a bottle sorting device
In this example the purpose is to design the control mechanism which would automatically sorting empty bottles. Workstation is controlled by controller with programmable PLC memory.
##### *The rules of workstation operation:*
- Turning on and turning off workplace is controlled by buttons S0 and S1
- After turning on the workstation engine M0 would work until detection a bottle by sensor F3 
- the engine will stop for 2s and in the same time detector F2 will deciding that is this bottle damaged or not
- If the bottle is demaged, electrovalve will turn on and the bottle will be pushed
- get back to point 2

##### Scheme of the workspace
![p4.1](https://i.pinimg.com/originals/c1/ec/6e/c1ec6e1279cf72ed7f76fa796e5af8b9.png)

*Table explaining parts of workspace*
| device | name on scheme | name in programm |
|:-:|:-:|:------:|
| control button | S0 |   I1   |
| control button | S1 |   I2   |
| optical sensor | F2 |    I3   |
| capacitive sensor | F3 |    I4   |
| contactor | K0 | Q1 |
| separating electrovalve 3/2 | Q1 | Q2 |

##### Solution made in programm LOGOV8. Structure in FBD is listed below:
![p4.2](https://i.pinimg.com/originals/1a/51/76/1a5176c970cc7398f7da02733a50a34b.png)
##### Example situations in programm
- workspace turned on, all inpouts are inactive
![p4.3](https://i.pinimg.com/originals/61/af/48/61af486f9badd8fb4690390d780e40fd.png)
- workspace turned on, engine is working
![p4.4](https://i.pinimg.com/originals/c7/75/b8/c775b86ac7850b429ab53e86b5044325.png)
- workspace turned on, undamaged bottle is detected, engine stopped
![p4.5](https://i.pinimg.com/originals/a7/6e/3e/a76e3e56d1087f4e91a2991a6499d262.png)
- workspace turned on, damaged bottle is detected, engine stopped and actuator pushed out the bottle
![p4.6](https://i.pinimg.com/originals/d5/d8/33/d5d8338f78259055e854ab0027eabb9a.png)

##### Conclusions

- During designing in FBD user can for testing lengthen or shorten time of detecting by sensors
- In more complicated schemes user should pay attention for transparent connections between elements of scheme

### Designing a control mechanism for a heater control system
In this example the purpose is to design the control mechanism which would automatically turning on one, two or zero of heaters. Workstation is controlled by controller with programmable PLC memory.

Device has 3 contactors W1-W3. By them device controlled heaters. For all temperatures (level of liquid in thermometer) is dedicated special heater configuration. In the case of incorrect information from thermometer (for exapmle sensors "a" and "c" are active but "b" is not) alarm lamp will turn on.

##### Scheme of the workspace
![p7.1](https://i.pinimg.com/originals/b2/86/c8/b286c8ac38ae9a8af3b939273e8614f8.png)
![p7.2](https://i.pinimg.com/originals/b2/40/13/b240132d4fa61e9b000c96031cb599e6.png)
*Table with inputs and outputs in workspace*
|device| name in programm | name on scheme |
|:-:|:-:|:-:|
|sensor 1|I1|a|
|sensor 2|I2|b|
|sensor 3|I3|c|
|sensor 4|I3|d|
|contactor 1|Q1|w1|
|contactor 2|Q2|w2|
|contactor 3|Q3|w3|

##### Karnough table used during designing alarm lamp
![p7.3](https://i.pinimg.com/originals/11/b8/1e/11b81e91ce553d2e788b0d752ca3ce75.png)
##### Solution made in programm LOGOV8. Structure in FBD is listed below:
![p7.4](https://i.pinimg.com/originals/68/e8/c9/68e8c9550e120b61d5660fcc87dd4df5.png)
##### Example situations in programm
- temperature is low and level of liquid is under level "a". Both heaters are working and they are connected in series.
![p7.5](https://i.pinimg.com/originals/82/d5/1c/82d51cae825e0c748a76e4d38833d79d.png)
- temperature is over level "a" but under level "b". Both heaters are working but in this time connected in parallel.
![p7.6](https://i.pinimg.com/originals/97/83/c7/9783c754271ebdc0a572f5ffa887b095.png)
- temperature is over level "b" but under level "c". Works only heater G1.
![p7.7](https://i.pinimg.com/originals/3f/49/06/3f4906208f08f78d687bfd081c64e53e.png)
- temperature is over level "c" but under level "d". Works only heater G2.
![p7.8](https://i.pinimg.com/originals/52/32/3c/52323c7be2adf152f60407a314ce7aa8.png)
- temperature is over level "d". No heater is working.
![p7.9](https://i.pinimg.com/originals/3e/64/e0/3e64e0971e8a9b98b280011c6f9bc2ea.png)
- in this case thermometer works incorrectly (sensors "a", "b" and "d" are active but "c" is not). Alarm lamp is signalling error with 10Hz frequency.
![p7.10](https://i.pinimg.com/originals/4d/2c/06/4d2c0677a8eaeccfcbd32d83b3cbee3b.png)

##### Conclusions
- language FBD enables making multi-level and more complicated schemes

### Designing a control mechanism for a elements sorting device
In this example the purpose is to design the control mechanism which would automatically sorting 3 types of elements. Elements are made from an aluminum, white and black plastic. Workstation is controlled by controller with programmable PLC memory.
Element recognition is done by 3 sensors: 
- inductive sensor
- capacitive sensor
- reflective sensor

##### Sensor operation table
 #

| type of material | inductive sensor  |capacitive sensor|reflective sensor|
|:-:|:-:|:-:|:-:|
|aluminum|1|1|1|
|white plastic|0|1|1|
|black plastic|0|1|0|

##### Table explaining parts of workspace
#
| device | name on scheme | name in programm |
|:-:|:-:|:------:|
| START button | S0 |   I1   |
| STOP button | S1 |   I2   |
| inductive sensor | B2 |    I3   |
| capacitive sensor | B3 |    I4   |
|reflective sensor|B4|I5|
| solenoid coil 3/2 pushing out elements made from aluminium |Y1 | Q1 |
| solenoid coil 3/2 pushing out elements made from white plastic | Y2 | Q2 |
| solenoid coil 3/2 pushing out elements made from black plastic | Y3 | Q3 |

##### Scheme of the workspace
![p3.1](https://i.pinimg.com/564x/59/b9/ab/59b9ab58a94ee408d7e4b40ce1e79c39.jpg)

##### Solution made in programm LOGOV8. Structure in FBD is listed below:
![p3.2](https://i.pinimg.com/originals/0b/03/62/0b036262a9738c6840aa27fc6d233f19.png)
##### Example situations in programm
- all inputs inactive, consequently all outputs are also inactive
![p3.3](https://i.pinimg.com/originals/7e/1e/96/7e1e96ca924194ab98857b11e6f33d47.png)
- detecting element made from aluminium
![p3.4](https://i.pinimg.com/originals/a9/bb/cd/a9bbcd28f8c19adb28db7446febfb934.png)
- detecting element made from white plastic
![p3.5](https://i.pinimg.com/originals/96/32/dc/9632dc3f6b4abe7aa7ac39958be06732.png)
- detecting element made from black plastic
![p3.6](https://i.pinimg.com/originals/2c/d9/7e/2cd97e38af0f2bdef4db5ed2678e948d.png)
- incorrect situation (informations from sensors do not fit to any material)
![p3.7](https://i.pinimg.com/originals/65/d6/88/65d688b79e311880730a5faf24ac2b4f.png)

##### Conclusions
- parts of scheme are identical so user can copy them to save time

### Designing a control mechanism for watering the garden
In this example the purpose is to design the control mechanism which would automatically watering the garden 2 times per day. Every cycle of watering is 2 rouds of turning on and off sprinklers. Workstation is controlled by controller with programmable PLC memory.


##### Table explaining parts of workspace
#
| device | name in programm |
|:-:|:------:|
| START button |    I1   |
| STOP button |    I2   |
| input responsible timing for watering | I3   |
| sprinkler 1| Q1 |
| sprinkler 2| Q2 |
| sprinkler 3| Q3 |
| sprinkler 4| Q4 |

##### Solution made in programm LOGOV8. Structure in FBD is listed below:
![p3.2](https://i.pinimg.com/originals/df/f4/4c/dff44c05ee73a6d7c4ff8ae184ac695b.png)
##### Example situations in programm
- all inputs inactive, consequently all outputs are also inactive
![p3.3](https://i.pinimg.com/originals/a8/e1/b7/a8e1b71c15af7aa4146bcbead42c0cc1.png)
- workspace turn on, but it is not time for watering
![p3.3](https://i.pinimg.com/originals/e8/7a/b4/e87ab49c899a3a995f7ef31ef7156bc0.png)
- workspace turn on, workspace is during first cycle, splinker 2 is turn on
![p3.3](https://i.pinimg.com/originals/9e/90/53/9e90534d1065192812f239d90574ef2e.png)
- workspace turn on, workspace is during second cycle, splinker 3 is turn on
![p3.3](https://i.pinimg.com/originals/a7/90/38/a790383bf3fce90b111ebed4876d44f9.png)

##### Conclusions
- in project wuth hour, weekly, year etc. timer user can simplified project for testing (for example changing weekly timer for normal input)
