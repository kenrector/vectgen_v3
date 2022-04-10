# vectgen_v3
kicad project for Wells-Gardner display controller

This is an ESP32 based interface to the Wells-Gardner 15v2000 BW X-Y display perhaps originally found
in the Atari Asteroids and Lunar Lander cocktail style arcade games.  The display is controlled by
X-Y voltages in the ranges +/- 0-10v and Z voltage 0-5v. 

The ESP32 processor is resident on a Wiretag WT32-ETH01 board and interfaces with client software via
the LAN connection.

Input commands from the client are move, draw, and zero, with related 12bit vector values sent to
X and Y MCP4922 DAC channels via the SPI interface.

Output from the DAC is translated to a bipolar voltage input to op amp integrator.  Integrator output is
input to the WG display.

Integrator input is switched by ADG201S CMOS switches controlled by the ESP32 software.  The integrators
are reset to zero by ADG201s switches also controlled by the ESP32.

A Z axis control to switch the CRT beam is provided by simple transistor logic.

