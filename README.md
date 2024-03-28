This is a basic configuration for the Primare A32 power amplifier
for esphome integration.

I wrote this because I found I kept forgetting to turn the power amp
off and that wastes a fair bit of power.

To use, connect a MAX3232 module to GPIO pins 16 and 17. Don't use a
MAX232; it has 5V logic. You can power the MAX3232 from the 3.3V supply
on the ESP32 dev kit.

If you prefer to use the hot standby rather than hard power off mode,
you can adjust the turn off command. The format of the serial string is

0x02 0x57 0x81 0xYY 0x10 0x03

where 0xYY is:

0=Standby mode 2 (default), 1=Standby mode 1, 2=Operate

Standby mode 2 is the hot standby.

Right now, we don't do any checking and just emit the serial commands.
If someone can think of a good reason to actually talk to the amp for
model/firmware/status, raise an issue and I'll give it a poke.

