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

# Alternative libraries

## standard Wire library in Arduino distribution

This one is based on TwoWrite.cpp and it seems to have been written by
Hernando Barragán, but this might be misinformation. In 2006 that source
was renamed to Wire.cpp because the Arduino developer (Nicholas Zambetti)
wanted to use the same name as the instantiated variable (i.e. Wire).

## The non-blocking Wire library by Gene Knight

This one is called nbwrite.cpp (all lower case). The nb stands for
non-blocking, I think. But it not immediately clear in what way it is
non-blocking. The code is mostly copied from the Arduino Wire.cpp.

Only one thing seems interesting about this version and that is written in
the comment "... The actual bytes read *is* given to the callback function,
though." The Arduino Wire library always returns the requested number of
bytes, whether they have been received or not.

The formatting sucks, big time. In fact, the code is a big mess.

## The I2C library by Wayne Truchsess

It promotes itself as follows.

 "This is a modified version of the Arduino Wire/TWI
  library.  Functions were rewritten to provide more functionality
  and also the use of Repeated Start.  Some I2C devices will not
  function correctly without the use of a Repeated Start.  The
  initial version of this library only supports the Master."

There are 5 revisions available (dd. 2014-01-04) and the latest version has
dropped the interrupt handling. It is now a polling version. That seems
unfortunate and the reason for it is unknown.

One nice feature of this implementation is that it can timeout the while
loops. This is important to avoid hanging systems.
