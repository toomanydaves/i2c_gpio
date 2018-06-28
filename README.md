# i2c_gpio
Home-Assistant Component for GPIO expansion via the I2C bus of a Raspberry Pi

## I2C GPIO
The `i2c_gpio` component shares the general functionality found in the component, `rpi_gpio`. It purpose is to expand the amount of available I/O which in `rpi_gpio` is limited to the roughly 30 pins on the Pi itself (the exact # depends on model), to the literally 100s of pins available through the use of GPIO expansion chips, like the MCP23017 – the MCP23017 adds an additional 16 digital I/Os on its own, and can be daisey chained for up to 124). 

While the MCP23017 is the only device currently supported, its usage of the I2C protocol is not unique. For that reason (and it's relative brevity) this component was named `i2c_gpio` and not `mcp23017_gpio`.

Like the `rpi_gpio` component, there is no set up needed for the component itself. All configuration is done via the individual platforms.

## I2C GPIO Switch

## I2C GPIO Cover
