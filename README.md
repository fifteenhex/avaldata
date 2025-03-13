# Aval data board info

## AVME 146

- mc68040 at 25MHz

### Jumpers

- dsw1 - Front panel, VME bus settings like syscon, base address etc
- dsw2 - for the avme-148 at least this is user defined, bits are visible in a register (Will confirm)
- dsw3 - see above (Will confirm)

## AVME 352

### jumpers
- w1, w2, w3 - Top bits of base address 1 + 2 on w1 is the MSB (I think)
- w4 1 + 2 - vme address space, shorted = extended, open = standard

### Memory map

```
0x0000 0000 - 0x0007 ffff - SRAM
 0x0000 0400 - 0x???? ???? - ROM copies itself here and jumps.
0x0c00 0000 - 0x???? ???? - ROM, mapped to 0x0 for the first few cycles?
0x00ff 0000 - 0x00ff 0fff - I think the dual port ram?
 - mb8421 x 2, I think 0xffc, 0xffd, 0xffe, 0xffe are the mailbox address that trigger interrupts.
```

### Memory dumps

Just powered on:

```
mvme147 =>md.w 0xf0c00000 0x1000
f0c00000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00010: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00030: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00040: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00050: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00060: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00070: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00080: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00090: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c000f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00100: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00110: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00120: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00130: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00140: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00150: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00160: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00170: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00180: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00190: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c001f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00200: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00210: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00220: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00230: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00240: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00250: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00260: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00270: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00280: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00290: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c002f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00300: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00310: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00320: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00330: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00340: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00350: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00360: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00370: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00380: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00390: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c003f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00400: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00410: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00420: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00430: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00440: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00450: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00460: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00470: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00480: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00490: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c004f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00500: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00510: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00520: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00530: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00540: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00550: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00560: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00570: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00580: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00590: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c005f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00600: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00610: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00620: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00630: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00640: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00650: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00660: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00670: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00680: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00690: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c006f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00700: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00710: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00720: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00730: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00740: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00750: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00760: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00770: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00780: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00790: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c007f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00800: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00810: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00820: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00830: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00840: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00850: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00860: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00870: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00880: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00890: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c008f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00900: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00910: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00920: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00930: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00940: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00950: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00960: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00970: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00980: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00990: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c009f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a00: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00a80: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00a90: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00aa0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ab0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ac0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ad0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ae0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00af0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b00: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b80: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00b90: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ba0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00bb0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00bc0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00bd0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00be0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00bf0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c00: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c80: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00c90: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ca0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00cb0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00cc0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00cd0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ce0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00cf0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d00: 0000 0000 0000 0000 0000 0000 8000 8000  ................
f0c00d10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d80: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00d90: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00da0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00db0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00dc0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00dd0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00de0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00df0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e00: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e80: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00e90: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ea0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00eb0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ec0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ed0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ee0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ef0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f00: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f10: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f20: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f30: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f40: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f50: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f60: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f70: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00f80: 524f 4d20 5479 7065 203d 2030 3030 3120  ROM Type = 0001 
f0c00f90: 4156 4d45 2d33 3532 2056 6572 2031 2e33  AVME-352 Ver 1.3
f0c00fa0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00fb0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00fc0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00fd0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00fe0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
f0c00ff0: 0064 a800 0000 0000 2d88 0000 0000 00ff  .d......-.......
f0c01000: c0ff c0ff ffff c0ff c0ff c0ff ffff c0ff  ................
f0c01010: feff feff feff feff feff feff fcff fcff  ................
```
0xff6 seems to be incrementing?

```
f0c00ff6: 00ad 5fe2                                .._.
mvme147 =>md.w 0xf0c00ff6 0x2
f0c00ff6: 00ad 601e                                ..`.
mvme147 =>md.w 0xf0c00ff6 0x2
f0c00ff6: 00ad 6058                                ..`X
mvme147 =>md.w 0xf0c00ff6 0x2
f0c00ff6: 00ad 6092                                ..`.
mvme147 =>
```
