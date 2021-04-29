# CSCP-MIDI

Provides connectivity and two-way comms between devices supporting the CSCP protocol and devices/software supporting the MIDI protocol
* Provides remote control over Calrec Audio mixers from a multitude of low-cost physical MIDI controllers

* Allows Calrec Audio mixers to control DAW software applications

This application has been developed and tested using:
* [Korg NanoKontrol2](https://www.korg.com/uk/products/computergear/nanokontrol2/) - A physical MIDI controller. 

* [Reaper](https://www.reaper.fm/) - DAW software 

* [Calrec Audio Brio](https://calrec.com/) - Live/Pro/Broadcast Audio mixer (supporting the CSCP protocol). 


### Usage
The following instructions relate to Calrec Brio & Summa mixers. For other Calrec mixer types, 
please refer to their installation manual for configuring CSCP.

* Connect one of the LAN ports on your Calrec Audio mixer to your PC (or to the same network your PC is on).

* Go to System-Settings>LAN config and set the mixer's IP address to one that is reachable from your PC 
(and set a static IP address on your PC if necessary).

* Go to System-Settings>Control-Protocols, check/set the TCP Port the mixer is using for CSCP and ensure CSCP is set to
enabled. 

* If using a physical controller, its midi port will automatically be available to select from the CSCP-MIDI application
if the controller is connected when CSCP-MIDI starts up.
    * CSCP-MIDI has been tested with the KorgNanoKontrol2
        * To use in its' default "CC" mode, selectable on the 
            controller by holding its SET MARKER & CYCLE buttons when connecting it to your PC.
        * To use in "Sonar" mode, hold the SET MARKER & RECORD buttons when connecting.
        * To request support for other MIDI modes, contact peter.allan.walker@gmail.com


* If using DAW software running on the same PC as this application on Windows, then 3rd party software is required to provide virtual midi ports (to allow midi comms between applications running in Windows)
    * Download [loopmidi](https://www.tobias-erichsen.de/software/loopmidi.html) by Tobias Erichsen. Open loopmidi and
    click the '+' button to add a MIDI port that will be accessible to your DAW and to CSCP-MIDI.

    * Configure your DAW for use with a MIDI controller, selecting the MIDI port/s created by loopmidi.
        * CSCP-MIDI has been tested with the Reaper DAW:
            * Reaper>Options>Preferences>Control-Surfaces, select "Add", choose "Makie Control Universal" and select the 
            midi ports created by loopmidi. Note, It is best to configure two MIDI ports in loop midi, one for input
            and one for output to avoid feedback loops. Ensure you select the correct ports here and in CSCP-MIDI when it
            starts.
            * Also in preferences, select Audio>MIDI-Devices and enable the MIDI I/O created from loopmidi.
            
* Start CSCP-MIDI using `python cscp-midi.py` or running the .exe. If it has been run before, you will be presented
with the last used settings. If you need to change the settings press 'n' and enter the mixer's IP address, CSCP port,
the MIDI ports you are using and the MIDI mode...
    * **You now have control comms between your Calrec mixer and your MIDI device/DAW!**      


## TODO / Known Issues

- [ ] Fix two-way control issues seen when using the Reaper DAW. Control in either direction is fine, but two-way control can cause feedback/control jitter. Not sure if this is specfic to Reaper, My CSCP GUI app works fine, might need to implement a similar data model to that to sit between rather than direct translation?? (for my GUI project I have a mid-point data model, and slow down the reads from the gui, works perfectly).


## Author

**Peter Walker**
Feedback/requests, email:peter.allan.walker@gmail.com

Note, this software is not currently being maintained by the author. 

I am not a professional software developer, this was a side-project in my spare time. It is 3rd party software that is not supported by Calrec, Korg, or Reaper.

This software is to be used at your own liability. Neither the author nor the vendors of the products the software has been tested with accept responsibility for use.