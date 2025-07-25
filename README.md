# Black Smoke Probe

## Einleitung
Die Black Smoke Probe ist eine Open Source Hardware, die kompatibel ist zur Black Magic Probe v2.1e.

Ich habe den letzten öffentlich zugänglichen [Schaltplan](https://black-magic.org/_downloads/5a984c502435264dc19bc5e08c8b55cd/bmpm_v2_1e_schematic.pdf) genommen und die Micro-USB durch eine USB-C Buchse ersetzt. 

Da die Platine leicht von Hand zu bestücken sein sollte, ist das Layout single sided und einige Bauteile als auch die Diemensions der Platine größer gewählt als beim Original. Diesen Maßnahmen ist die UART zum Opfer gefallen und ist nur noch als Testpoints auf der Bottom Seite verfügbar (Ohne Level-Shifter). 

## Original Firmware
[https://github.com/blackmagic-debug/blackmagic](https://github.com/blackmagic-debug/blackmagic)

## iBOM
[ibom.html](https://html-preview.github.io/?url=https://github.com/casartar/Black-Smoke-Probe/blob/main/Hardware/bom/ibom.html)

## Flashen

### Flashen des Bootloaders
```
st-flash write blackmagic_native_bootloader.bin 0x08000000
```

### Flashen der Applikation
```
dfu-util -d 1d50:6018,:6017 -s 0x08002000:leave -D blackmagic_native_firmware.bin
```

## Testen

[https://github.com/casartar/BlackPillUniversalTester](https://github.com/casartar/BlackPillUniversalTester)