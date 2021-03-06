# Python VXI-11 Readme

For more information and updates:
http://alexforencich.com/wiki/en/python-vxi11/start

GitHub repository:
https://github.com/alexforencich/python-vxi11

## Introduction

Python VXI-11 provides a pure Python VXI-11 driver for controlling instruments
over Ethernet.

## Requirements

* Python 2 or Python 3

## Installation

Extract and run

    # python setup.py install

## Usage examples

Connecting to Agilent MSO7104A via LXI:

    import vxi11
    instr =  vxi11.Instrument("192.168.1.104")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO7104A,MY********,06.16.0001'

Connecting to Agilent E3649A on GPIB address 5 via HP 2050A GPIB bridge:

    import vxi11
    instr = vxi11.Instrument("192.168.1.105", "gpib,5")
    print(instr.ask("*IDN?"))
    # returns 'Agilent Technologies,E3649A,0,1.4-5.0-1.0'

It is also possible to connect with VISA resource strings like so:

    import vxi11
    instr =  vxi11.Instrument("TCPIP::192.168.1.104::INSTR")
    print(instr.ask("*IDN?"))
    # returns 'AGILENT TECHNOLOGIES,MSO7104A,MY********,06.16.0001'

and:

    import vxi11
    instr = vxi11.Instrument("TCPIP::192.168.1.105::gpib,5::INSTR")
    print(instr.ask("*IDN?"))
    # returns 'Agilent Technologies,E3649A,0,1.4-5.0-1.0'

