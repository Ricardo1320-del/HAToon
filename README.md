NOTE: This component only works with rooted TOON devices. Toon's are Thermostats sold by Eneco a Dutch energy company.

More information about preparing for usage with this component can be found here: Eneco TOON as Domotica controller

This component reads the Thermostat Mode, Current Temperature and it's Setpoint. You can also control the thermostat Mode and Setpoint. (target temperature)

Installation
Copy directory toon_climate to your <config dir>/custom_components directory.
Configure with config below.
Restart Home-Assistant.
Usage
To use this component in your installation, add the following to your configuration.yaml file:

# Example configuration.yaml entry

climate:
  - platform: toon_climate
    name: Toon Thermostat
    host: IP_ADDRESS
    port: 10080
    scan_interval: 10
Configuration variables:

name (Optional): Name of the device. (default = 'Toon Thermostat')
host (Required): The hostname or IP address on which the Toon can be reached.
port (Optional): Port used by your Toon. (default = 10080)
scan_interval (Optional): Number of seconds between polls. (default = 60)
Screenshot
alt text

TOON Smart Meter sensor component
NOTE: This component only works with rooted TOON devices.

It reads Smart Meter data from your TOON, gathered by the meteradapter.

Installation
Copy directory toon_smartmeter to your <config dir>/custom_components directory.
Configure with config below.
Restart Home-Assistant.
Usage
To use this component in your installation, add the following to your configuration.yaml file:

# Example configuration.yaml entry

sensor:
  - platform: toon_smartmeter
    host: IP_ADDRESS
    port: 10080
    scan_interval: 10
    resources:
      - gasused
      - gasusedcnt
      - elecusageflowpulse
      - elecusagecntpulse
      - elecusageflowlow
      - elecusagecntlow
      - elecusageflowhigh
      - elecusagecnthigh
      - elecprodflowlow
      - elecprodcntlow
      - elecprodflowhigh
      - elecprodcnthigh
      - elecsolar
      - elecsolarcnt
      - heat
      
Configuration variables:

host (Required): The hostname or IP address on which the TOON can be reached.
port (Optional): Port used by your TOON. (default = 10080)
scan_interval (Optional): Number of seconds between polls. (default = 10)
resources (Required): This section tells the component which values to display, you can leave out the elecprod values if your don't generate power and the elecusage*pulse types if you use the P1 connection.
alt text

If you want them grouped instead of having the separate sensor badges, you can use this in your groups.yaml:

# Example groups.yaml entry

Smart meter:
  - sensor.toon_gas_used_last_hour
  - sensor.toon_gas_used_cnt
  - sensor.toon_power_use_cnt
  - sensor.toon_power_use
  - sensor.toon_p1_power_prod_low
  - sensor.toon_p1_power_prod_high
  - sensor.toon_p1_power_prod_cnt_low
  - sensor.toon_p1_power_prod_cnt_high
  - sensor.toon_p1_power_use_cnt_pulse
  - sensor.toon_p1_power_use_cnt_low
  - sensor.toon_p1_power_use_cnt_high
  - sensor.toon_p1_power_use_low
  - sensor.toon_p1_power_use_high
  - sensor.toon_p1_power_solar
  - sensor.toon_p1_power_solar_cnt
  - sensor.toon_p1_heat
Screenshots
alt text alt text alt text

TOON Boiler Status sensor component
NOTE: This component only works with rooted TOON devices. And installed BoilerStatus app via ToonStore.

It reads OpenTherm Boiler data from your TOON, gathered by the thermostat adapter.

Installation
Copy directory toon_boilerstatus to your <config dir>/custom_components directory.
Configure with config below.
Restart Home-Assistant.
Usage
To use this component in your installation, add the following to your configuration.yaml file:

# Example configuration.yaml entry

sensor:
  - platform: toon_boilerstatus
    host: IP_ADDRESS
    port: 10080
    scan_interval: 10
    resources:
      - boilersetpoint
      - boilerintemp
      - boilerouttemp
      - boilerpressure
      - boilermodulationlevel
      - roomtemp
      - roomtempsetpoint
Configuration variables:

host (Required): The hostname or IP address on which the TOON can be reached.
port (Optional): Port used by your TOON. (default = 10080)
scan_interval (Optional): Number of seconds between polls. (default = 10)
resources (Required): This section tells the component which values to display and monitor.
By default the values are displayed as badges.

If you want them grouped instead of having the separate sensor badges, you can use this in your groups.yaml:

# Example groups.yaml entry

Boiler Status:
  - sensor.toon_boiler_intemp
  - sensor.toon_boiler_outtemp
  - sensor.toon_boiler_setpoint
  - sensor.toon_boiler_pressure
  - sensor.toon_boiler_modulation
  - sensor.toon_room_temp
  - sensor.toon_room_temp_setpoint

Dont make it my self: Plz thanks the developer: https://github.com/cyberjunky/home-assistant-custom-components
