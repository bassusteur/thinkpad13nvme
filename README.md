# Modifying the thinkpad 13 Gen 1 to unlock its full pcie potential
A Few weeks ago i acquired a Thinkpad 13 gen 1 on ebay, sold by a recycling company, it was listed for parts
and with the wrong model name in the title.  
Math done it only cost about 33 euro shipped so i decided to buy to check out what was wrong with it,  
as soon as it arrived i plugged it in to check for any signs of life and it immediately turned on, 
at the time i only checked it out using a usb stick equipped with a live image of linux.
Later on i did try using an ssd stolen from another device but with no luck, it would not show up in the bios nor did linux give any info about it, 
so i left it at that for the time being.  

some weeks later i decided to check out the boardview and schematic of the lenovo laptop, to my unexperienced eyes nothing looked off and nvme should have just worked, being that in the schematic
it showed all the components for pcie present, but my friend i was talking to at the time took a look at the files and in the specsheets she noticed it mentioned the m.2 slot being sata only,
not only that but the design on the schematic by Quanta, she said, did not follow pcie spec, and put capacitors on the device side of one of the receiving pcie diffpairs.  

So enough talking done, i got to disassembling the laptop and getting down to desolder two capacitors, C224 and C237, and bridging them with some magnet wire,
it was kind of difficult but nothing some flux and holding a steady hand can't fix. 
![632d38f63c54eab7](https://github.com/user-attachments/assets/47bae9c3-e3e3-4adb-8fd6-e4970c90c5b4)
The end result isn't exactly eye candy but that's not what matters, what matters is that it works!


Laptop reassembled, with a drive chucked from my main machine, i tried booting it up but no luck the drive would not show up in the bios entries nor linux, 
though as a tip from my friend i would apparently also need to bridge two other pads (PEDET and GND) for the ssd to be detected by the PCH,  
because despite the components being present on the boardview and schematic they were not ultimately placed during assembly.
![c150c6af6f544226](https://github.com/user-attachments/assets/f1ebd3a9-682c-41c5-9b0f-7b0e58dfb861)
