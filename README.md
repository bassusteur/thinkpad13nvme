# Modifying the thinkpad 13 Gen 1 to unlock its full pcie potential
A Few weeks ago i acquired a Thinkpad 13 gen 1 on ebay, sold by a recycling company, it was listed for parts
and with the wrong model name in the title.  
Math done it only cost about 33 euro shipped so i decided to buy to check out what was wrong with it,  
as soon as it arrived i plugged it in to check for any signs of life and it immediately turned on, 
at the time i only checked it out using a usb stick equipped with a live image of linux.
Later on i did try using an ssd stolen from another device but with no luck, it would not show up in the bios nor did linux give any info about it, 
so i left it at that for the time being.  
Passed some i decided to check out the boardview and schematic of the lenovo laptop, to my unexperienced eyes nothing looked off and nvme should have just worked, being that in the schematic
it showed all the components for pcie present, but my friend i was talking to at the time checked out the specsheet and noticed it mentioned the m.2 slot being sata only,
not only that but on the schematic she mentioned the laptop manufacturer did not follow pcie spec, and put capacitors on the device side of one of the receiving pcie diffpairs.  
