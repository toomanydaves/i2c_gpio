# I2C GPIO
*Home-Assistant component and platforms for Raspberry Pi GPIO via the available I2C bus*

## I2C GPIO Component
The `i2c_gpio` component shares the general functionality found in the component, `rpi_gpio`. It purpose is to expand the amount of available I/O, which in `rpi_gpio` is limited to the roughly 30 pins on the Pi itself (the exact number depending on model) to the literally 100s of pins available through the integration of GPIO expansion chips, like the MCP23017 –– the MCP23017 adds 16 digital I/Os on its own and can be daisey chained for up to 124 additional pins. 

(While the MCP23017 is the only device currently supported, its usage of the I2C protocol is not unique. For that reason, and its relative brevity, this component is named `i2c_gpio` and not `mcp23017_gpio`.)

Like the `rpi_gpio` component, there is no set up needed for the component itself. All configuration is done via the individual platforms.

## I2C GPIO Switch Platform
The `i2c_gpio` switch platform allows you to control GPIOs from MCP23017 epansion boards connected to your Raspberry Pi via its I2C bus (pins 3 & 5 on the model 3).

To use this component, add the following to your configuration.yaml file:
```
  # Example configuration.yaml entry
  switch:
    - platform: i2c_gpio
      switches:
        - address: 0x20
          register: A
          index: 0
        - address: 0x24
          register: B
          index: 7
```
configuration variables:
+ invert_logic (Optional): If true, inverts the output logic to ACTIVE LOW. Default is false (ACTIVE HIGH).
+ switches array (Required): List of your switches
  + mcp23017_address (Required): The hex address of the MCP23017 device containing the switch on the Pi's I2C bus.
  + register (Required): The register (A or B) of the switch on the MCP23017 device.
  + index (Required): The 0-based index of the switch on the register.
  + name (Optional): Name to use in the frontend.
