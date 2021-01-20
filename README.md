# sd-mux

Fork of sd-mux-ctrl from the [Tizen git repository](https://git.tizen.org/cgit/tools/testlab/sd-mux/).
This version supports SDReWire as well as SDWire. To use this version make sure
to set the product string.


List the SDReWire devices

```
$ sudo sd-mux-ctrl --list --vendor=0x0403 --product=0x6015
Number of FTDI devices found: 1
Dev: 0, Manufacturer: SliwaIO, Serial: SDRW00004, Description: sd-re-wire
```

Use the "set-serial" command to write serial as well as product string:

```
sudo sd-mux-ctrl --device-serial=SDRW00004 --vendor=0x0403 --product=0x6015 --device-type=sd-re-wire --set-serial=SDRW00004
```

With that you should be able to switch between DUT (device under test) and TS
(test system) mode:
```
$ sudo sd-mux-ctrl --device-serial=SDRW00004 --vendor=0x0403 --product=0x6015 --dut
$ sudo sd-mux-ctrl --device-serial=SDRW00004 --vendor=0x0403 --product=0x6015 --ts
```

Note: Since `sd-mux-ctrl` needs full device access using `sd-mux-ctrl` does not
allow you to use the USB to UART tty at the same time. This fork is meant as a
stop-gap/migration solution.
