# ECEN-361 EEProm-Final

## Overview / Objective
This project is proposed as an alternative to the final exam in ECEN-361.  This exercise is designed to demonstrate:

* Understanding of STM32 programming, I/O interfacing
<br>
* Ability to read an previously-unknown datasheet, timing diagrams, and operational specifications
<br>
* Specific understanding of SPI protocol and use to read/write from a peripheral
<br>
For this exam, the student is provided a pre-programmed non-volatile, serial memory device -- a 25AA0040A, 4K-bit, serial EEPROM.  This device has been programmed to contain a single question whose answer is to be written back into the same physical part.

## Instructions

1. Accept the pre-programmed physical part and envelope.  Note the Part# on the envelope.  This number is to be put into the assignment submission on iLearn.
<br>
2. Referring the [Datasheet](./media/Microchip-EEProm-25AA040A.pdf) for the  **Microchip EEProm 25AA0040**, connect the part to the the STM32-Nucleo476RG and dump the contents. 
<br>
3. Answer the associated question as stored on the device.  Formulate a brief (< 512 bytes) answer and store your answer back onto the physical part.  You can over-write the contents of the EEPROM with your answer. <br> Note that your answer will include the Part# and your name.
<br>
4. Return the part to the professor.  
<br>
5. Submit the part number on iLearn as demonstration of completion.
<br>

## Tips / Hints

1. Note that the total size of the memory space is 512 bytes.  Make sure your answer is less than that amount.

2. Note the a requirement to set the Write Enable latch (WREN) for each write and that the latch gets reset after every write operation.  (See section 2.4)

3. The maximum bit rate speed of this part is 10Mhz.  The STM32 can do speeds faster than this, so programming of the SPI needs to consider the max. of the EEPROM.

4.  Note the write cycle time  (AC parameter #20 Twc) takes at least 5mS.  Writing too fast won't work.
