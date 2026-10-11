# USB HID Device Report Descriptor Corpus

A collection of sample USB HID device report descriptors from real devices

Big Mess o' Wires

These are the USB descriptors of about 200 HID devices, mostly keyboards and mice, that I
collected while testing the USB Wombat (a USB/ADB keyboard and mouse converter). They're useful
for testing any USB host or HID parser. Use them however you like.

There's one text file per device, named VID-PID plus the device name. xxxx means the ID is
unknown, or the device isn't real. Each file has:

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
