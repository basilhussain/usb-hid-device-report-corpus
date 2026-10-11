USB HID Device Descriptors
Big Mess o' Wires, October 2026

These are the USB descriptors of 181 HID devices, mostly keyboards and mice, that I collected
while testing the USB Wombat (a USB/ADB keyboard and mouse converter). They're useful for testing
any USB host or HID parser. Use them however you like.

There's one text file per device, named VID-PID plus the device name. xxxx means the ID is
unknown, or the device isn't real. The files are sorted into folders by what the device is:

  keyboards                 including keyboards with built-in touchpads or pointing sticks
  mice                      including trackballs and gaming mouse dongles
  receivers-adapters-kvms   combo receivers, PS/2 adapters, KVMs
  other-devices             gamepads, tablets, presenters, security keys and other things that
                            have HID interfaces (some of them pretend to be keyboards or mice)
  examples-and-tests        HID specification examples and synthetic or malformed test
                            descriptors, not real devices

Each file has:

  - Where the data came from, and notes on anything odd about the device.
  - The interfaces: class, subclass, protocol and endpoint size.
  - Each interface's report descriptor, first annotated and then as plain hex bytes.
  - For some devices, the device and configuration descriptors too.
  - For some devices, input reports recorded from the real device. These include the report ID
    byte when the device uses report IDs.

Most of the descriptors come from bug reports and recordings that other people posted: libinput,
OpenRazer, QMK, DeskHop, the Linux kernel, hid-tools, udev-hid-bpf, Android CTS and others. Each
file links its source. Often the source had only the report descriptors, so the interface subclass
and protocol were inferred, and the file says so. A few descriptors were generated from firmware
source code (QMK, ZMK, TinyUSB, Arduino, KVMs), and a few are test descriptors or examples from
the HID specification. The "Type" line says which.

hid_annotate.py is the Python 3 script that made the annotated listings. Give it the hex bytes of
a report descriptor and it prints the same kind of listing:

    python hid_annotate.py descriptor.txt
    python hid_annotate.py --config config.txt
    python hid_annotate.py --device device.txt

https://www.bigmessowires.com
