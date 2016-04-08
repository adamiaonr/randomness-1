# K22 SPI

Peripheral is called DSPI (Deserial/Serial Peripheral Interface). Provides:

1. SPI
2. DSI (Deserial/Serial Interface)
3. CSI (Combined Serial Interface)

- Internal Bus Clock = System Clock for SPI
- f_SPI_ = f_BusClk_ / 2
- All SPI Interrupts are OR'ed. Read `SPI_SR` to find which caused the interrupt.

### Microwire

1. Half-duplex
2. SPI Mode 0 (CPOL=0, CPHA=0)

#### Microwire/Plus

1. Full-duplex
2. SPI Mode 0 & 1

**NOTE:** LMX2571 probably uses Microwire/Plus

## Useful information

define an empty function in the preprocessor with `#define somemacro(param) ((void)0)`