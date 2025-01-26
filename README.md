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

![image](https://github.com/user-attachments/assets/406a34d1-5a97-41eb-8550-2ef8e5e4e6b5)

It's important to note that PISA refers to the PCI/ISA backplane specification put out by Kontron https://www.kontron.com/download/download?filename=/downloads/white_papers/pisad218.pdf. SBCs with the label "PCISA" refer to a similar standard that is mostly compatible with the exception of the PCI interrupt routing in some cases. While PISA and PCISA can be considered mostly compatible with respect to backplanes, proper interrupt routing is required for 100% functionality of the PCI cards. 
To make this backplane "universal", I've included a PCI mapper card that can be configured to any combination of interrupt and IDSEL for the PCI slots. The SBC manufacturer determines the interrupt and IDSEL for the PCI slots, which are a product of the physical wiring and BIOS hard-coded PCI identification.

<img src="https://github.com/user-attachments/assets/cab62bd3-f264-4837-8fb7-d1391830cda5" width=75% height=75%><br>



