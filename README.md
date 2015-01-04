# The TwoWire library for Arduino

This is the Arduino library for TWI (aka I2C). See History below to find
out where it came from.

This library is for AVR only. For architectures other than AVR you'll have
to use the standard library from Arduino.

# History

This library started out as a copy of the standard Wire library as
delivered with Arduino 1.5.8

The reason to create this copy were mainly because of the following:
* we needed some modifications
* the Arduino source is not maintained separately (as a normal library)
* we want to be able to work with version control (GIT)
* the original design specs are unclear and cannot be found anywhere

There are several questionable features in Arduino's TwoWire.
* why is the TwoWire class derived from Stream?
* why is the source split over Wire.cpp and twi.h

And now that we decided to create our own "fork" we can also reformat the
code to our own liking. We started with a copy of the code from
Arduino 1.5.8. The GIT repo will have a tag "arduino-1.5.8".
