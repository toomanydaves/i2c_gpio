# MCP23017 GPIO
*Home-Assistant component and platforms for Raspberry Pi GPIO via MCP23017 Chips*

## MCP23017 GPIO Component
The `mcp23017_gpio` component shares the general functionality found in the component, `rpi_gpio`. Its purpose is the extension of available I/O, which in `rpi_gpio` is limited to the roughly 30 pins on the Pi itself (the exact number depending on model) to the 124 additional pins available when daisey-chaining MCP23017 GPIO expansion chips together. 

Like the `rpi_gpio` component, there is no set up needed for the component itself. All configuration is done via the individual platforms.

## MCP23017 GPIO Switch Platform
The `mcp23017_gpio` switch platform allows you to control switches on MCP23017 epansion boards connected to your Raspberry Pi via its I2C bus (Pins 3 & 5 on the Model 3).

To use this component, add the following to your configuration.yaml file:
```
  # Example configuration.yaml entry
  switch:
    - platform: mcp23017_gpio
      invert_logic: true
      switches:
        - address: 0x20
          register: A
          index: 0
          name: Track Lighting
        - address: 0x24
          register: B
          index: 7
          name: Overhead Fan
```
Configuration Variables:
+ **invert_logic** (Optional): If true, inverts the output logic to ACTIVE LOW. Default is false (ACTIVE HIGH).
+ **switches** array (Required): List of your switches
  + **address** (Required): The hex address of the MCP23017 device containing the switch on the Pi's I2C bus.
  + **register** (Required): The register (A or B) of the switch on the MCP23017 device.
  + **index** (Required): The 0-based index of the switch on the register.
  + **name** (Optional): Name to use in the frontend.
