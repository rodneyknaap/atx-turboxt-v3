# ATX Turbo-XT Mainboard V3

I hereby publish the third revision of my ATX Turbo-XT mainboard design.

No guarantees of function or fitness for any useful purpose is given, building this design is at the sole responsibility of the builder.

Do not attempt this project unless you have the necessary electronics assembly expertise and experience, and know how to observe electronics safety guidelines.

Besides the GPL3 license there are a few warnings and usage restrictions applicable:

This project was created out of historical reasons and for the purpose of enabling computing enthousiasts with a sufficient level of building and troubleshooting expertise to be able to experience the technology by building and troubleshooting the hardware described in this project.

It is not permitted to use the computer built from this design without the assumtion of the possibility of loss of data or malfunction of the connected device.

If you plan to use this design or any part of it in new designs, the acknowledgement of the designer and the design sources and inspirations, historical and modern, of all subparts contained within this design should be included in your publication, to accredit the hard work, time and effort dedicated by the people before you who contributed to make your project possible.

No guarantee for any proper operation or suitability for any possible use or purpose is given, loss of data is likely and to be expected when connecting any storage device or storage media to the resulting system from this design, or when configuring or operating any storage device or media with the system of this design.

When connecting this system to a computer network which contains stored information on it, it is the sole responsibility and risk taking of the person making the connection, no guarantee is given against data loss or data corruption, malfunctions or failure of the whole computer network and information contained inside it on other devices and media which are connected to the same network.

When building this project, the builder assumes personal responsibility for troubleshooting it and using the necessary care and expertise to make it function properly as defined by the design. Timing issues are likely to occur which require certain components to be of a suitable type to be able to meet the timing requirements for proper function. The prototype of the developer is proof of concept, please refer to the detailed partslist which includes type and manufacturer where necessary, however each new build may pose it's own challenges to bring it to success. This design is by nature not a turnkey solution and will only function 100% reliably when using all the components of similar timing and behaviour as was used in the prototype. Determining the right components may likely be experimental in nature and require expertise, effort and persistance. 

After soldering the project, it's a strong recommendation to use proper lighting and magnification and systematically inspect all soldering points to detect any short circuits or open solder joints before powering up the system for testing. Short circuits which are not detected are likely to damage ICs and introduce hidden defects into your project which will be much more difficult to detect after the damage is done.

If you do not agree or do not wish to accept the above risks and terms, do not make any attempts to build and operate the hardware in these design specifications.

# Acknowledgements

This project was inspired by:
- IBM Corporation who introduced the industry standard PC concept and design schematics
- Taiwanese clone XT builders who produced their own modifications in the turbo XT which also inspired this project
- testing with the Super PC/Turbo XT BIOS https://www.phatcode.net, 
- Sergey's HD floppy drive BIOS extension https://github.com/skiselev/floppy_bios
- concept and software of the XT-IDE universal BIOS https://www.xtideuniversalbios.org
- datasheets, application notes and specifications by:

LG Semiconductors (Goldstar) (GM82C765 FDC, GM16C550)
Standard Microsystems Corporation (FDC37C65C datasheet, FDC register access table)
Texas Instruments (GD75232)
Realtek (RTL8019AS)
NCR (53C400 SCSI)

Acknowledgements of people who were instrumental in preceeding developments on which this design was elaborated:

[IBM PC development team](https://www.ibm.com/ibm/history/exhibits/pc25/pc25_birth.html)
[Some historical info](https://arstechnica.com/gadgets/2017/06/ibm-pc-history-part-1/)
[Bill Lowe](https://www.ibm.com/ibm/history/exhibits/builders/builders_lowe.html)
[Don Estridge](https://www.ibm.com/ibm/history/exhibits/builders/builders_estridge.html)

[Sergey Kiselev](http://www.malinov.com/Home/sergeys-projects/xi-8088)
[His HD Floppy BIOS](https://github.com/skiselev/floppy_bios)
I was inspired after seeing and reading about his 8088 projects, he also created the HD floppy BIOS extension.
 
[Super PC/Turbo XT BIOS by Plasma (Jon Ρetrosky and Ya'akov Miles)](https://www.phatcode.net)
An excellent BIOS for XT machines, far superior in stability and function to anything else I have tested.

Tilmann Reh and others (16 bit to 8 bit translation of IDE I/O in computer hardware for example as described in TCJ #53)
I have used my own adaptation of [J. Chapman's version(Glitchworks)](https://minuszerodegrees.net/xtide/rev_4/XT-IDE%20Rev%204%20-%20general.htm) of XT-IDE schematic after extensive testing with several circuit and component variations on an Amstrad PPC640. I studied all revisions of the circuits first before creating my own variations.
More information about the creation of XT-IDE hardware can be found [here](https://minuszerodegrees.net/xtide/XT-IDE%20-%20Basics.htm).

[XT-IDE universal BIOS project development team for developing the XT-IDE BIOS](https://www.xtideuniversalbios.org)
Amazing and extremely efficient software, fast disk access for XT and various AT computers.
Works with every IDE drive I have tested. Still under active development earlier in 2023.

I have taken time to think about above acknowledgements. If anyone or anything is left out, that is not intentional, please contact me and I will update this page.

BIOS for operation of this mainboard is composed as follows, top to bottom in the ROM:
8k   Super PC/Turbo XT BIOS (project by Jon Petrosky and Ya'akov Miles)
8k   XT-IDE BIOS file (by XT-IDE universal BIOS team)
configured to port 300 308 and XT-IDE v2 hardware, corrected for checksum=0
8k   XT HD-Floppy BIOS extension (by Sergey Kiselev)
configuration of floppy drives according to instructions by Sergey
40k  blank space "00" hex code
This comprises a 64k BIOS image, the design accommodates two BIOS images in the 128k ROM, the page to be used can be switched by a jumper or switch. For testing it's advised to program two identical BIOS images into the ROM first. Initially it's best to use an EPROM which cannot be erased by software if there is any software trying to write into the BIOS region.

Schematic diagram and PCB design are made in KiCad 5.1.7. I know this is an older release however I am used to working in this version and I don't want to change for now. It's also compatible with screenshots of JLCPCB guidelines of settings for creating the files for manufacturing.






