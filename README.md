# Modifying the Thinkpad 13 Gen 1 to unlock its full PCIe potential
A Few weeks ago i acquired a Thinkpad 13 Gen 1 on ebay, sold by a recycling company, it was listed for parts
and with the wrong model name in the title.  
Math done it only cost about 33 euro shipped so i decided to buy it,  
as soon as it arrived i plugged it in to check for any signs of life and it immediately turned on, 
at the time i only checked it out using a usb stick equipped with a live image of linux.
Later on i did try using an SSD stolen from another device but with no luck, it would not show up in the BIOS nor did Linux give any info about it, 
so i left it at that for the time being.  

Some weeks later i decided to check out the boardview and schematic of the Lenovo laptop, to my unexperienced eyes nothing looked off and NVMe should have just worked, being that in the schematic
all the components for PCIe were present.
Talking to my friend who took a look at the files she pointed out that the design by Quanta,
is not exactly ideal as it would be when [correctly implemented for NVMe](https://github.com/user-attachments/assets/8c6cde96-698f-4264-8fcb-caac52429b33), as they [added extra components required in SATA-only configuration.](https://github.com/user-attachments/assets/84771b44-804d-449d-a28c-5a9eb1dad497).
We later discovered that the specsheet listed SATA m.2 as the only [storage option.](https://github.com/user-attachments/assets/08a2fda6-a2ea-44c7-a890-eeec80adb582).

So enough talking done, i got to disassembling the laptop and getting down to desolder two capacitors, C224 and C237, and bridging them with some magnet wire,
it was kind of difficult but nothing some flux and holding a steady hand can't fix.  
![image](https://github.com/user-attachments/assets/47bae9c3-e3e3-4adb-8fd6-e4970c90c5b4)   
The end result isn't exactly eye candy but that's not what matters, what matters is that it works!


Or.. not, Laptop reassembled, with a drive chucked from my main machine, i tried booting it up but no luck the drive would not show up in the bios entries nor linux, 
though as a tip from my friend i would apparently also need to bridge two other pads [(PEDET and GND)](https://github.com/user-attachments/assets/807ed9ac-0f56-4f43-aea4-028ddc73a5bb) for the SSD to be detected, because despite the components being present on the boardview and schematic they were not ultimately placed during assembly.
![image](https://github.com/user-attachments/assets/f1ebd3a9-682c-41c5-9b0f-7b0e58dfb861)  

Preparing for what should be the final test i once again borrowed an ssd from my main laptop, which runs debian btw, painstakingly reseated the keyboard and 
booted the machine.

It worked! the ssd is now recognized with just a single lane which gets me approximately 1GB/s throughput, 
though UEFI won't let me boot from it i can access the files from a live iso, so it could just be a matter of updating uefi entries for this machine or trying to install
an OS from scratch on a new drive.
![image](https://github.com/user-attachments/assets/fc76c305-e988-4225-9e03-555e460800b7)  
![image](https://github.com/user-attachments/assets/b0a3e3ff-e26d-47cf-b1c6-aaf974d52678)  

One last thing to notice is: the extra pcie lanes going to the slot all have capacitors that have not been populated, so if you wanted a speedier link you would have [to solder them on as well](https://github.com/user-attachments/assets/058d3fbe-3e6c-4f1c-a9fd-9d0444f03298).

Credits to the mind behind the operation: [wifi](https://github.com/a-little-wifi).
