# Backwards-DIY-Backplane

The Backwards Backplane is a universal backplane that's compatible with the PISA/PCISA and Allen Bradley/Rockwell Automation half-size single-board computers (SBC).

<img src="https://github.com/user-attachments/assets/c95d8719-b80a-44b2-b4d6-e13d983e4513" width=75% height=75%><br>
<img src="https://github.com/user-attachments/assets/559ba853-a072-47d8-a7b5-47c418ef2e72" width=75% height=75%><br>

## Features:
* Two 188-pin PCI/ISA combination slots
* One standard ISA slot
* Two standard PCI slots
* Integrated P.O.S.T. decoder
* Integrated ES1869F ISA sound chip
* IDE CD-ROM port
* ATX power input
* PCI mapper card

## Usage with PISA/PCISA SBCs

![PCISA-C400R-RS-R20](https://github.com/user-attachments/assets/c9eb16d7-81dd-4909-844c-6396f2b70f79)

This is an example of a compatible PCISA SBC you can use in the Backwards backplane ([PCISA-C400R-RS-R20](https://www.ieiboards.net/iei/pcisa-c400r-rs-r20)). At its heart, the backplane is a purely passive device that connects the SBC to the other card slots. While none of the active hardware on the backplane is required, there are a few jumpers to be aware of. Please refer to the board diagram sheet for more information. JP1 (reset function) should be moved to position one (left). JP2 and JP3 CPU power jumpers should be unpopulated, as well as JP4 (VBAT).

## -IMPORTANT- 
To double-check for correct configuration with PCISA SBCs, attach the ATX power supply with all other cards removed and power up the backplane. The LED indicators for the AB CPU 3.3V power should be unlit! This is important for proper function as the universal nature of the board utilizes these pins for CPU power on the Allen Bradley cards while conflicting with the PISA spec. While powering a PCISA card, the indicators may light up and that's normal. The important thing to consider is the indicators are unlit with no card installed!

<img src="https://github.com/user-attachments/assets/1e527c3c-2a17-4363-bd2a-bd9eb2ba5340" width=50% height=50%><br>

Note that PISA refers to the PCI/ISA backplane specification put out by Kontron https://www.kontron.com/download/download?filename=/downloads/white_papers/pisad218.pdf. SBCs with the label "PCISA" refer to a similar standard that is mostly compatible with the exception of the PCI interrupt routing in some cases. While PISA and PCISA can be considered mostly compatible with respect to backplanes, proper interrupt routing is required for 100% functionality of the PCI cards. 
To make this backplane "universal", I've included a PCI mapper card that can be configured to any combination of interrupt and IDSEL for the PCI slots. The SBC manufacturer determines the interrupt and IDSEL for the PCI slots, which are a product of the physical wiring and BIOS hard-coded PCI identification.

<img src="https://github.com/user-attachments/assets/cab62bd3-f264-4837-8fb7-d1391830cda5" width=75% height=75%><br>

The proper configuration of the mapper card consists of one IDSEL pin from PCI0 and PCI1 to be connected with one of the available PCI ADxx pins using a 100 ohm 0603 resistor. For reference, the PISA spec has PCI1 (0 in my design) connected to AD19 and PCI2 (1 in my design) connected to AD20. These PCI addresses are specific to the SBC and may vary depending on the adherence to the PISA spec. 

Next is the interrupt matrix that consists of 4 (INT) interrupt lines from the SBC. The idea is to connect one of the intersecting lines with a 0 ohm resistor between each row (SBC side) to one of the columns (PCI side). The PISA spec states a standard configuration as follows.

PCI1 (0 in my design)
* IDSEL A19
* SBC INT A to PCI A
* SBC INT B to PCI B
* SBC INT C to PCI C
* SBC INT D to PCI D

PCI2 (0 in my design)
* IDSEL A20
* SBC INT A to PCI D
* SBC INT B to PCI A
* SBC INT C to PCI B
* SBC INT D to PCI C

### As stated above, not all SBCs work in this manner and I've found alternate wiring for PCI2 (1 in my design).

PCI2 (1 in my design)
* IDSEL A20
* SBC INT A to PCI B
* SBC INT B to PCI C
* SBC INT C to PCI D
* SBC INT D to PCI A

The board supports RESET for the SBC with some conditions. JP1 (reset function) needs to be set correctly and the SBC needs to support reset on the SBC slot. For PCISA cards, this is pin C22 (column C pin 22 lower row) on the SBC slot. This pin is pulled to ground through a 500 ohm resistor through the RESET switch SW2. Determining whether your SBC supports resetting through the slot pin might be found in the manual for your specific board, or simply trying the reset button on the backplane to see if it works. Also, your board may support resetting, but the connection may be unpopulated on the SBC itself. For instance, on my PCISA-C400R-RS, the reset line through R157 on the SBC was missing. After installing a 500 ohm resistor, the reset function works as expected.

<img src="https://github.com/user-attachments/assets/0929d033-185e-4cb8-8a08-d3a3c338e68c" width=33% height=33%><br>





