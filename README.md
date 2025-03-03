# midi2cv !!! This is a work in progress, please refere to the source of this fork for a stable version

<img src="/images/IMG_0776.JPG" alt="midi2cv" width="400"> <img src="/images/IMG_0777.JPG" alt="midi2cv" width="400">

This repository contains the code and schematic for a DIY MIDI to CV converter.  I installed this converter into a home-built analog synthesizer, allowing me to play the synthesizer with my Yamaha CP50 keyboard over MIDI.

The MIDI to CV converter includes the following outputs:

* Note CV output (88 keys, 1V/octave) using a 12-bit DAC
* Pitch bend CV output (0.5 +/-0.5V)
* Velocity CV output (0 to 4V)
* Control Change CV outout (0 to 4V)
* Trigger output (5V, 20 msec pulse for each new key played)
* Gate output (5V when any key depressed)
* Clock output (1 clock per quarter note, 20 msec 5V pulses)

## Parts
* Arduino Nano
* Optocoupler (I used a Vishay SFH618A, but there are plenty of alternatives out there)
* 2x MCP4822 12-bit DACs
* LM324N Quad Op Amp 
* Diode (e.g., 1N917)
* 220, 500, 3x1K, 7.7K (3K+4.7K), 10K Ohm resistors
* 3x 0.1 uF ceramic capacitors
* 5 pin MIDI jack
* 7x 4mm banana plug jacks
* 3-pin header and jumper *or* 3-way switch

The Arduino code uses the standard MIDI and SPI libraries, which can be found in the Arduino Library Manager. 
https://github.com/FortySevenEffects/arduino_midi_library


The schematic is illustrated at the bottom of this page (Eagle file included).  Input power (VIN) is 9-12V.  This is required for the Note CV op amp, used for the 0-7.3V note output.  1% metal film resistors are recommended for the 7.7K and 10K resistors, for a constant op-amp gain that does not change with temperature.  Note that 7.7K is not a standard resistor value.  I used a 3K and a 4.7K resistor in series, which are much more common values.  If precise tuning is desired, a trim pot can be added *or* the constant NOTE_SF can be adjusted in the code.  I opted for the latter.

<img src="/images/schematic.JPG" alt="schematic" width="800">




