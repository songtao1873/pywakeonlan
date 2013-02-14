pywakeonlan
===========

A small python module for wake on lan.  
It has been tested both locally and externally using Python 2.7.3 and
Python 3.2.3  

The project is hosted on https://github.com/Trollhammaren/pywakeonlan  
For more information on the wake on lan protocol please take a look at
[Wikipedia](http://en.wikipedia.org/wiki/Wake-on-LAN)

This module is licensed under the WTFPL

Usage
-----

To wake up a computer using wake on lan it must first be enabled in the BIOS
settings. Please note the computer you are trying to power on does not have an
ip address, but it does have a mac address. The package needs to be sent as a
broadcast package.

### As a python module

  - Import the module

        import wakeonlan


  - Wake up a single computer by its mac address

        wakeonlan.send_magic_packet('ff.ff.ff.ff.ff.ff')


  - Wake up multiple computers by their mac addresses. Note that both dots and
    minus signs are allowed or no delimiters at all. The mac addresses are also
    case insensitive.

        wakeonlan.send_magic_packet([
                'ff.ff.ff.ff.ff.ff',
                '00-00-00-00-00-00',
                'FFFFFFFFFFFF'])


  - An external host may be specified. Do note that port forwarding on that host
    is required. The default ip address is 255.255.255.255 and the default port
    is 9.

        wakeonlan.send_magic_packet(
                'ff.ff.ff.ff.ff.ff',
                ip_address='example.com',
                port=1337)


### As a standalone script

    wol.py [-i ip_address] [-p port] mac_address

        -h              Show this help message.

        -i ip address   The broadcast ip address the magic packet should be
                        sent to.

        -p port         The port to which the package should be sent.

        mac_address     The mac address or hardware address of the computer
                        you are trying to wake.

Dependencies
------------
- Python2.x or Python3.x

