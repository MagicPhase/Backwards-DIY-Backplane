# Backwards-DIY-Backplane

## Index
* [Usage with PISA/PCISA and Allen Bradley/Rockwell SBCs](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#usage-with-pisapcisa-and-allen-bradleyrockwell-sbcs)
* [Usage with ISA SBCs](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#usage-with-isa-sbcs)
* [JP1 Reset Function](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#jp1-reset-function)
* [JP2 and JP3 power pins](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#jp2-and-jp3-power-pins)
* [JP4 VBAT](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#jp4-vbat)
* [PCI Mapper Card](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pci-mapper-card)
* [Mounting](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#mounting)
* [PCB Layout](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pcb-layout)
* [Backwards V1.0 Schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#backwards-v10-schematic)
* [Known working SBC list](https://github.com/MagicPhase/Backwards-DIY-Backplane/blob/main/README.md#known-working-sbc-list)

The Backwards Backplane is a universal backplane compatible with "half-size" PISA/PCISA, Allen Bradley/Rockwell Automation, and ISA single-board computers (SBC). <ins>Please read ALL sections before using the Backplane!!</ins>
Active discussion about this project can be found on [VOGONS](https://www.vogons.org/viewtopic.php?t=102519) and [VCFED](https://forum.vcfed.org/index.php?threads/project-backwards-a-universal-backplane-for-pisa-pcisa-allen-bradley-and-isa-half-size-sbcs-seeking-volunteers-for-testing.1250989/)

<img src="https://github.com/user-attachments/assets/c95d8719-b80a-44b2-b4d6-e13d983e4513" width=50% height=50%><img src="https://github.com/user-attachments/assets/1b640abe-a5ca-4b1a-8a96-876619d50384" width=50% height=50%><br>

## Features:
* Two 188-pin PCI/ISA combination slots (Compatible with PISA/PCISA, Allen Bradley/Rockwell Automation, and ISA)
* One standard ISA slot
* Two standard PCI slots
* Integrated P.O.S.T. decoder
* Integrated ES1869F ISA sound chip
* IDE CD-ROM port
* ATX power input
* PCI mapper card

| SBC TYPE  | JUMPER CONFIGURATION |
| ------------- | ------------- |
| [PISA/PCISA](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#usage-with-pisapcisa-and-allen-bradleyrockwell-sbcs)  | [JP1](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp1-reset-function) (1-2) / [JP2](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp2-and-jp3-power-pins) (OPEN) / [JP3](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp2-and-jp3-power-pins) (OPEN) / [JP4](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp4-vbat) (OPEN) |
| [Allen Bradley/Rockwell](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#usage-with-pisapcisa-and-allen-bradleyrockwell-sbcs) | [JP1](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp1-reset-function) (2-3) / [JP2](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp2-and-jp3-power-pins) (CLOSED) / [JP3](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp2-and-jp3-power-pins) (CLOSED) / [JP4](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#jp4-vbat) (CLOSED) |
| [ISA](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main#usage-with-isa-sbcs) | NA |

| [SLOTS (IN ORDER)](https://github.com/MagicPhase/Backwards-DIY-Backplane/tree/main?tab=readme-ov-file#pcb-layout)  | CARD TYPE USAGE |
| ------------- | ------------- |
| SBC 1 (188-pin) | PISA/PCISA, Allen Bradley/Rockwell, ISA Card or SBC |
| SBC 2 (188-pin) | PISA/PCISA, Allen Bradley/Rockwell, ISA Card or SBC |
| ISA (98-pin) | ISA Card or SBC |
| PCI 1 (124-pin) | PCI |
| PCI 0 (124-pin) | PCI |
| PCI Mapper (36-pin) | PCI Mapper Card |

## -IMPORTANT- Issue with V1.0 boards!

Clearance on JP1 using SBC slot 1 is tight! The PCISA SBCs have slightly more clearance than the Allen Bradley's. Please ensure the card isn't being obstructed by JP1 when installing. You can bend JP1 slightly inward to maximize clearance. If this is a problem, consider using SBC slot 2 instead. *Planned fix for next board revision.

<img src="https://github.com/user-attachments/assets/80044e02-7af2-4576-a66e-f70abf9aaf0c" width=33% height=33%><br>
<img src="https://github.com/user-attachments/assets/c6cc2c2c-ecfe-4088-a294-4a70f97cf9a1" width=33% height=33%><br>

# PCB Layout

<img src="https://github.com/user-attachments/assets/ccfa76fb-d095-414d-8fd7-0bfb9796c920" width=50% height=50%><br>

# Usage with PISA/PCISA and Allen Bradley/Rockwell SBCs

<img src="https://github.com/user-attachments/assets/c9eb16d7-81dd-4909-844c-6396f2b70f79" width=50% height=50%><br>

The backplane has 3 SBC slots. While all are ISA compatible, slots 1 and 2 are dedicated to PISA/PCISA and Allen Bradley-style SBCs.

This is an example of a compatible PCISA SBC you can use in the Backwards backplane ([PCISA-C400R-RS-R20](https://www.ieiboards.net/iei/pcisa-c400r-rs-r20)). At its heart, the backplane is a purely passive device that connects the SBC to the other card slots. While none of the active hardware on the backplane is required, there are a few jumpers to be aware of.

JP1 (reset function) should be moved to position one (left 1-2). JP2 and JP3 CPU power jumpers as well as JP4 (VBAT) should be unpopulated! Please refer to the [PCB Layout](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pcb-layout).

Note that PISA refers to the PCI/ISA backplane specification put out by Kontron https://www.kontron.com/download/download?filename=/downloads/white_papers/pisad218.pdf. SBCs with the label "PCISA" refer to a similar standard that is mostly compatible with the exception of the PCI interrupt routing in some cases. While PISA and PCISA can be considered mostly compatible with respect to backplanes, proper interrupt routing is required for 100% functionality of the PCI cards. 
To make this backplane "universal", I've included a PCI mapper card that can be configured to any combination of interrupt and IDSEL for the PCI slots. The SBC manufacturer determines the interrupt and IDSEL for the PCI slots, which are a product of the physical wiring and BIOS hard-coded PCI identification.

<img src="https://github.com/user-attachments/assets/fc6877e8-5f03-43cd-bfa7-9aac37c5aa42" width=50% height=50%><br>

This is an example of an Allen Bradley 6189-1CPU233. It's important to note that the Allen Bradley-style SBCs require a physically taller card slot to be secured! The height difference is about 1/4" (6.35 mm) requiring a spacer or riser. This may also be problematic due to the location of external ports above a standard PC card slot. Install with caution or consider a full custom mounting solution for these SBCs.

<img src="https://github.com/user-attachments/assets/b83ff4c6-7840-4eaf-b3a4-d9f72029bcc3" width=50% height=50%><br>

The Allen Bradley SBCs use a proprietary implementation of the PCI/ISA SBC slot. The universal nature of this backplane requires special consideration for these differences. One important aspect is the need to inject 3.3V CPU power through 8 of the lower pins that are reserved for PCI functions as well as ground and reset in the PISA spec! These power pins are left floating under normal conditions. Also, the reset line for Allen Bradley SBCs is commonly a VCC power pin on the PISA spec. 

JP1 (reset function) should be in position 2 (right 2-3). Please continue reading for information about JP1, JP2, JP3, and JP4 as it pertains to proper operations for Allen Bradley SBCs. Also, refer to the [PCB Layout](https://github.com/MagicPhase/Backwards-DIY-Backplane?tab=readme-ov-file#pcb-layout).

# Usage with ISA SBCs

<img src="https://github.com/user-attachments/assets/0516259f-c003-428b-82a8-ad9159c8af59" width=50% height=50%><br>

This is an example of an ISA half-size SBC (Advantech PCA-6145B). 

The three SBC slots 1,2 and,3 are all compatible with ISA SBCs. This is possible in slots 1 and 2 due to their dual-level pin nature and the upper row being all pins related to the ISA BUS. While you can use ISA SBCs in any slot, there are a few things to remember. The pins of the SBC dual-level slots have reduced widths based on the slot type's specifications. This means the current carrying capability of these pins is also reduced. When using an ISA SBC, you should install this card into SBC slot 3 which is a true ISA slot. If using SBC slot 1 or 2, you may want to consider powering the SBC using its auxiliary power connection if you experience any instability. This aux power input will be specific to the manufacture and you should refer to the manual of the board you're using. 

It should also be noted that there is both series and parallel termination on the ISA BUS. The series termination happens between SBC slot 2 and the ISA slot (SBC 3) while the parallel termination happens elsewhere on the board. Please refer to the [schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane/blob/main/Backplane_V1.0_schematic.pdf) for more information. 

Only the ISA pins are connected when using ISA SBCs. JP1, JP2, JP3, and JP4 are not relevant here and you will not have reset function unless you jumper a compatible reset line from the SBC to the backplane. Refer to your SBC manual for an external reset line if present. 

# JP1 Reset Function

<img src="https://github.com/user-attachments/assets/b0a1a0da-0626-4539-8917-b73eb04b394a" width=50% height=50%><br>


JP1 controls which SBC slot pin is connected to the reset switch SW2. JP1 (reset function) needs to be set correctly while the SBC needs to support reset on the SBC slot to work. For PCISA cards, this is pin C22 (column C pin 22 lower row) on the SBC slot. This pin is pulled to ground through a 500 ohm resistor through the RESET switch SW2. Determining whether your SBC supports resetting through the slot pin might be found in the manual for your specific board, or simply trying the reset button on the backplane to see if it works. Also, your board may support resetting, but the connection may be unpopulated on the SBC itself. For instance, on my PCISA-C400R-RS, the reset line through R157 on the SBC was missing. After installing a 500 ohm resistor, the reset function works as expected.

<img src="https://github.com/user-attachments/assets/0929d033-185e-4cb8-8a08-d3a3c338e68c" width=33% height=33%><br>

The Allen Bradley SBCs use pin C43 (column C pin 43) on the SBC slots.

# JP2 and JP3 Power Pins

## -IMPORTANT- 
To double-check for correct configuration with PCISA SBCs, attach the ATX power supply with all other cards removed and power up the backplane. The LED indicators for the AB CPU 3.3V power should be unlit! This is important for proper function as the universal nature of the board utilizes these pins for CPU power on the Allen Bradley cards while conflicting with the PISA spec. While powering a PCISA card, the indicators may light up and that's normal. The important thing to consider is the indicators are unlit with no card installed!

<img src="https://github.com/user-attachments/assets/1e527c3c-2a17-4363-bd2a-bd9eb2ba5340" width=50% height=50%><br>

To properly use an Allen Bradley SBC, jumper JP2 and JP3 CPU power pins. To check for proper operations, attach ATX power with no cards installed and power up. You should see the CPU power indicators lit if the jumpers are installed and F1 fuse is good. F1 should be a 5A fuse.

<img src="https://github.com/user-attachments/assets/8dffa297-4125-4911-934f-8b2290447783" width=50% height=50%><br>

# JP4 VBAT.

<img src="https://github.com/user-attachments/assets/5af9674b-41d6-4c17-a7a7-aa7c6593c009" width=50% height=50%><br>


The Allen Bradley SBCs CMOS battery is located on the backplane in favor of a supercapacitor on the SBC. This CMOS battery line is injected through the SBC slot and is in conflict with the PISA spec. This CMOS line is powered through a diode from 3.3V and a CR2032 battery (through JP4) located on the backplane. This jumper is required for proper CMOS settings and timekeeping operation. 

## -Important-
Since the Allen Bradley SBC doesn't have a CMOS battery, it will lose its settings if left uninstalled in the backplane once its supercapacitor is depleted. Upon a fresh install, the SBC may remain non-functional for a period of time until the supercapacitor has been charged. Once charged you can power cycle the SBC to restore boot function.


# PCI Mapper Card

<img src="https://github.com/user-attachments/assets/cab62bd3-f264-4837-8fb7-d1391830cda5" width=50% height=50%><br>
<img src="https://github.com/user-attachments/assets/fb8db581-3757-430e-b493-7f4487c268f4" width=50% height=50%><br>

The mapper card is reversible. This is a picture with all positions filled which is NOT CORRECT!

### PISA/PCISA

The proper configuration of the mapper card for PISA consists of one IDSEL pin from PCI0 and PCI1 to be connected with one of the available PCI ADxx pins using a 100 ohm 0603 resistor. For reference, the PISA spec has PCI1 (0 in my design) connected to AD19 and PCI2 (1 in my design) connected to AD20. These PCI addresses are specific to the SBC and may vary depending on the adherence to the PISA spec. Next is the interrupt matrix that consists of 4 (INT) interrupt lines from the SBC. The idea is to connect one of the intersecting lines with a 0 ohm resistor between each row (SBC side) to one of the columns (PCI side). The PISA spec states a standard configuration as follows.

| PCI POSITION | IDSEL | SBC INT PIN | PCI INT PIN |
| ------------- | ------------- | ------------- | ------------- |
| PCI 0 | A19 | A | A | 
|  |  | B | B |
|  |  | C | C |
|  |  | D | D | 
| PCI 1 | A20 | A | D | 
|  |  | B | A |
|  |  | C | B |
|  |  | D | C | 
| PCI 1 (PCISA ALTERNATE) | A20 | A | B | 
|  |  | B | C |
|  |  | C | D |
|  |  | D | A | 

As stated above, not all SBCs work in this manner. You can try the PCI 1 alternate if you experience instability or lockups with the PCI 1 slot.

### Allen Bradley/Rockwell Automation

The proper configuration of the mapper card for Allen Bradley/Rockwell Automation consists of one IDSEL pin from PCI0 and PCI1 to be connected with one of the available PCI ADxx pins using a 100 ohm 0603 resistor and the interrupt matrix intersection connected with 0 ohm resistors. The Rockwell backplane connections are as follows. At the time of this writting, I'm only aware of one configuration set.

| PCI POSITION | IDSEL | SBC INT PIN | PCI INT PIN |
| ------------- | ------------- | ------------- | ------------- |
| PCI 0 | A28 | A | C | 
|  |  | B | A |
|  |  | C | D |
|  |  | D | B | 
| PCI 1 | A29 | A | B | 
|  |  | B | D |
|  |  | C | C |
|  |  | D | A | 

# Mounting

<img src="https://github.com/user-attachments/assets/a051c71e-e8e7-4669-abf9-af6583eb806c" width=50% height=50%><br>

The backplane has mounting options for two ATX positions. The left-most position "P1" offers two slots free for an ITX system in the same case and the "P2" position offers one space. There is clearance for cards slightly larger than 2, but some flexibility is lost. The total space available is limited to the PCI mapper card. The absolute max space is 50mm from the ITX PCIe slot to the side of the mapper card. If more space is needed, the PCI mapper card can be removed but only if both PCI slots are left unpopulated! 

<img src="https://github.com/user-attachments/assets/7d4a7a58-1ad2-48a4-9089-6059db5c5104" width=50% height=50%><br>

## -Important-

Be cautious when using screws with heads larger than 6.5mm! Depending on your case mounting, the standard 6/32" with 8mm head will NOT WORK and short the board possibly causing damage. I'd recommend using smaller than 6.5mm head screws with an isolation washer for installing the backplane. A larger pad may be introduced beyond V1.0. 

<img src="https://github.com/user-attachments/assets/cc4594e0-2ad8-470c-b0a9-c9e5b0cea972" width=50% height=50%><br>

Use extreme care when installing your SBC! The 188-pin slots are fragile and pin damage will occur if you install any card at an angle! 

<img src="https://github.com/user-attachments/assets/570bd0ce-b6bc-40f8-8044-f34d3999328a" width=50% height=50%><br>

# Backwards V1.0 Schematic
[Schematic](https://github.com/MagicPhase/Backwards-DIY-Backplane/blob/main/Backplane_V1.0_schematic.pdf)

# Known working SBC list

This is a list of SBCs known to work with additional information.

### PISA/PCISA Boards
* IEI PCISA-C400R-RS-R20 Ceneron 400Mhz -- WORKING
* PHOENIX TECHNOLOGIES LY20C390 (Fuba 3104ML) 1Ghz VIA -- WORKING


### Allen Bradley/Rockwell Automation Boards
* Allen Bradley 6189-1CPU233 (Rockwell Automation 140420-050) Socket 7 Intel MMX/AMD K6-2 -- WORKING
* Allen Bradley 6189-1CPU566 (Rockwell Automation 140573-010) Socket 370 Intel P3 -- WORKING

### ISA SBCs
* Advantech PCA-6145B -- WORKING
