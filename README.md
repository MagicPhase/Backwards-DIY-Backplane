# Backwards-DIY-Backplane

## Index
* [Usage with PISA/PCISA and Allen Bradley/Rockwell SBCs](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#usage-with-pisapcisa-and-allen-bradleyrockwell-sbcs)
* [JP1 Reset Function](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#jp1-reset-function)
* [JP2 and JP3 power pins](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#jp2-and-jp3-power-pins)
* [JP4 VBAT](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#jp4-vbat)
* [PCI Mapper Card](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pci-mapper-card)
* [Mounting](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#mounting)
* [PCB Layout](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pcb-layout)
* [Backwards V1.0 Schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#backwards-v10-schematic)
* Known working SBC list

The Backwards Backplane is a universal backplane that's compatible with the PISA/PCISA and Allen Bradley/Rockwell Automation half-size single-board computers (SBC).

<img src="https://github.com/user-attachments/assets/c95d8719-b80a-44b2-b4d6-e13d983e4513" width=75% height=75%><br>

## Features:
* Two 188-pin PCI/ISA combination slots
* One standard ISA slot
* Two standard PCI slots
* Integrated P.O.S.T. decoder
* Integrated ES1869F ISA sound chip
* IDE CD-ROM port
* ATX power input
* PCI mapper card


# Usage with PISA/PCISA and Allen Bradley/Rockwell SBCs

<img src="https://github.com/user-attachments/assets/c9eb16d7-81dd-4909-844c-6396f2b70f79" width=50% height=50%><br>

This is an example of a compatible PCISA SBC you can use in the Backwards backplane ([PCISA-C400R-RS-R20](https://www.ieiboards.net/iei/pcisa-c400r-rs-r20)). At its heart, the backplane is a purely passive device that connects the SBC to the other card slots. While none of the active hardware on the backplane is required, there are a few jumpers to be aware of. Please refer to the board diagram sheet for more information. [Layout](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pcb-layout). JP1 (reset function) should be moved to position one (left). JP2 and JP3 CPU power jumpers as well as JP4 (VBAT) should be unpopulated!

Note that PISA refers to the PCI/ISA backplane specification put out by Kontron https://www.kontron.com/download/download?filename=/downloads/white_papers/pisad218.pdf. SBCs with the label "PCISA" refer to a similar standard that is mostly compatible with the exception of the PCI interrupt routing in some cases. While PISA and PCISA can be considered mostly compatible with respect to backplanes, proper interrupt routing is required for 100% functionality of the PCI cards. 
To make this backplane "universal", I've included a PCI mapper card that can be configured to any combination of interrupt and IDSEL for the PCI slots. The SBC manufacturer determines the interrupt and IDSEL for the PCI slots, which are a product of the physical wiring and BIOS hard-coded PCI identification.

<img src="https://github.com/user-attachments/assets/fc6877e8-5f03-43cd-bfa7-9aac37c5aa42" width=50% height=50%><br>

This is an example of an Allen Bradley 6189-1CPU233.

The Allen Bradley SBCs use a proprietary implementation of the PCI/ISA SBC slot. The universal nature of this backplane requires special consideration for these differences. One important aspect is the need to inject 3.3V CPU power through 8 of the lower pins that are reserved for PCI functions as well as ground and reset on the PISA spec! These pins are left floating under normal conditions. Also, the reset line for Allen Bradley SBCs is commonly a ground pin for the PISA spec. Please continue reading for information about JP1, JP2, JP3, and JP4 as it pertains to proper operations for Allen Bradley SBCs. 

# Usage with ISA SBCs

<img src="https://github.com/user-attachments/assets/0516259f-c003-428b-82a8-ad9159c8af59" width=50% height=50%><br>

This is an example of an ISA half-size SBC (Advantech PCA-6145B). 

The three SBC slots 1,2 and,3 are all compatible with ISA SBCs. This is possible in slots 1 and 2 due to their dual-level pin nature and the upper row being all pins related to the ISA BUS. While you can use ISA SBCs in any slot, there are a few things to remember. The pins of the SBC dual-level slots have reduced widths based on the slot type's specifications. This means the current carrying capability of these pins is also reduced. When using an ISA SBC, you should install this card into SBC slot 3 which is a true ISA slot. If using SBC slot 1 or 2, you may want to consider powering the SBC using its auxiliary power connection if you experience any instability. This aux power input will be specific to the manufacture and you should refer to the manual of the board you're using. 

It should also be noted that there is both series and parallel termination. The series termination happens between SBC slot 2 and the ISA slot (SBC 3) while the parallel termination happens elsewhere on the board. Please refer to the [schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane/blob/main/Backplane_V1.0_schematic.pdf) for more information. 

# JP1 Reset Function

JP1 controls which SBC slot pin is connected to the reset switch SW2. JP1 (reset function) needs to be set correctly while the SBC needs to support reset on the SBC slot to work. For PCISA cards, this is pin C22 (column C pin 22 lower row) on the SBC slot. This pin is pulled to ground through a 500 ohm resistor through the RESET switch SW2. Determining whether your SBC supports resetting through the slot pin might be found in the manual for your specific board, or simply trying the reset button on the backplane to see if it works. Also, your board may support resetting, but the connection may be unpopulated on the SBC itself. For instance, on my PCISA-C400R-RS, the reset line through R157 on the SBC was missing. After installing a 500 ohm resistor, the reset function works as expected.

<img src="https://github.com/user-attachments/assets/0929d033-185e-4cb8-8a08-d3a3c338e68c" width=33% height=33%><br>

The Allen Bradley SBCs use pin C43 (column C pin 43) on the SBC slots.

# JP2 and JP3 power pins

## -IMPORTANT- 
To double-check for correct configuration with PCISA SBCs, attach the ATX power supply with all other cards removed and power up the backplane. The LED indicators for the AB CPU 3.3V power should be unlit! This is important for proper function as the universal nature of the board utilizes these pins for CPU power on the Allen Bradley cards while conflicting with the PISA spec. While powering a PCISA card, the indicators may light up and that's normal. The important thing to consider is the indicators are unlit with no card installed!

<img src="https://github.com/user-attachments/assets/1e527c3c-2a17-4363-bd2a-bd9eb2ba5340" width=33% height=33%><br>

To properly use an Allen Bradley SBC, set JP1 (reset function) to position 2 (right). Jumper JP2 and JP3 CPU power pins. To check for proper operations, attach ATX power with no cards installed and power up. You should see the CPU power indicators lit if the jumpers are installed and F1 fuse is good. F1 should be a 5A fuse.

<img src="https://github.com/user-attachments/assets/8dffa297-4125-4911-934f-8b2290447783" width=33% height=33%><br>

# JP4 VBAT.

![image](https://github.com/user-attachments/assets/5af9674b-41d6-4c17-a7a7-aa7c6593c009)


The Allen Bradley SBCs CMOS battery is located on the backplane in favor of a supercapacitor on the SBC. This CMOS battery line is injected through the SBC slot and is in conflict with the PISA spec. This CMOS line is powered through a diode from 3.3V and a CR2032 battery (through JP4) located on the backplane. This jumper is required for proper CMOS settings and timekeeping operation. 

## Important
Since the Allen Bradley SBC doesn't have a CMOS battery, it will lose its settings if left uninstalled in the backplane once its supercapacitor is depleted. Upon a fresh install, the SBC may remain non-functional for a period of time until the supercapacitor has been charged. Once charged you can power cycle the SBC to restore boot function.


# PCI Mapper Card

<img src="https://github.com/user-attachments/assets/cab62bd3-f264-4837-8fb7-d1391830cda5" width=50% height=50%><br>
<img src="https://github.com/user-attachments/assets/fb8db581-3757-430e-b493-7f4487c268f4" width=50% height=50%><br>

The mapper card is reversible. This is a picture with all positions filled which is NOT CORRECT!

## PISA/PCISA

The proper configuration of the mapper card for PISA consists of one IDSEL pin from PCI0 and PCI1 to be connected with one of the available PCI ADxx pins using a 100 ohm 0603 resistor. For reference, the PISA spec has PCI1 (0 in my design) connected to AD19 and PCI2 (1 in my design) connected to AD20. These PCI addresses are specific to the SBC and may vary depending on the adherence to the PISA spec. Next is the interrupt matrix that consists of 4 (INT) interrupt lines from the SBC. The idea is to connect one of the intersecting lines with a 0 ohm resistor between each row (SBC side) to one of the columns (PCI side). The PISA spec states a standard configuration as follows.

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

## Allen Bradley/Rockwell Automation

The proper configuration of the mapper card for Allen Bradley/Rockwell Automation consists of one IDSEL pin from PCI0 and PCI1 to be connected with one of the available PCI ADxx pins using a 100 ohm 0603 resistor and the interrupt matrix intersection connected with 0 ohm resistors. The Rockwell backplane connections are as follows.

PCI1 (0 in my design)
* IDSEL A28
* SBC INT A to PCI C
* SBC INT B to PCI A
* SBC INT C to PCI D
* SBC INT D to PCI B

PCI2 (1 in my design)
* IDSEL A29
* SBC INT A to PCI B
* SBC INT B to PCI D
* SBC INT C to PCI C
* SBC INT D to PCI A

# Mounting

Be cautious when using screws with heads larger than 6.5mm! Depending on your case mounting, the standard 6/32" with 8mm head will NOT WORK and short the board possibly causing damage. I'd recommend using smaller than 6.5mm head screws with an isolation washer for installing the backplane. A larger pad may be introduced beyond V1.0. 

<img src="https://github.com/user-attachments/assets/cc4594e0-2ad8-470c-b0a9-c9e5b0cea972" width=50% height=50%><br>

Use extreme care when installing your SBC! The 188-pin slots are fragile and pin damage will occur if you install any card at an angle! 

<img src="https://github.com/user-attachments/assets/570bd0ce-b6bc-40f8-8044-f34d3999328a" width=50% height=50%><br>

# PCB Layout

<img src="https://github.com/user-attachments/assets/ccfa76fb-d095-414d-8fd7-0bfb9796c920" width=75% height=75%><br>

# Backwards V1.0 Schematic
[Schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane/blob/main/Backplane_V1.0_schematic.pdf)

# Known working SBC list

This is a list of SBCs known to work with additional information.

## PISA/PCISA Boards



## Allen Bradley/Rockwell Automation Boards


