# ECEN-361 Final Alternative:  EEPROM

## Overview / Objective
This project is proposed as an alternative to the final exam in ECEN-361.  This exercise is designed to demonstrate:

* Understanding of STM32 programming, I/O interfacing
* Ability to read an unfamiliar datasheet to interpret timing diagrams and operational specifications
* Specific understanding of SPI protocol and use to read/write from a peripheral


For this exam, the student is provided a pre-programmed non-volatile, serial memory device -- a Microchip 25AA0040A, 4K-bit, serial EEPROM.  This device has been programmed to contain a single question whose answer is to be written back into the same physical part.  Each device is unique.

## Instructions

1. Accept the pre-programmed physical part and envelope.  Note the Part# on the envelope.  This number is to be put into the assignment submission on iLearn.

2. Referring the [Datasheet](./media/Microchip-EEProm-25AA040A.pdf) for the  **Microchip EEProm 25AA0040**, connect the part to the the STM32-Nucleo476RG and dump the contents. 

3. There are three questions stored on the device.  You are free to choose any one of the three questions listed: Q1.), Q2.) or Q3.).

Formulate a brief (< 512 bytes) answer and store your answer back onto the physical part.  You can over-write the contents of the EEPROM with your answer. <br> Note that your answer needs to  include the Part# and your name.  See that on the EEPROM as given to you, at address 500 is:
```
500:      ID: WIN24-#xxx 
```
Please don't over-write the ID number of the chip. It's stored in the top 12 addresse: locations 500-511.

4. Return the part to the professor.  

5. Submit the part number on iLearn as demonstration of completion.

6. All work is to be individual.  You are not to share your code or use your H/W to help another student, or get help from other students on this assignment.

## Tips / Hints

1. Note that the total size of the memory space is 512 bytes.  Make sure your answer is less than that amount.  Note that I've asked you to not over-write the chip ID addresses, 500 - 511

2. Carefully read the datasheet about the a requirement to set the Write Enable latch (WREN) for each write.  Note too, the explanation that the latch gets reset after **every** write operation.  (See section 2.4)

3. The maximum bit rate speed of this part is 10Mhz.  The STM32 can do speeds faster than this, so programming of the SPI needs to consider the max. of the EEPROM.

4.  Note the write cycle time  (AC parameter #20 Twc) takes at least 5mS.  Writing too fast won't work.  This means you'll likely need to review the prescaler on the SPI.

5. Note that the SPI does not start in the default 8-bits/transmission.  You'll need to make sure the SPI configuration matches what's required by the datasheet of the EEPROM.

