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
