# ESPHome E-Ink Weather Calendar Wall Monitor
This project provides a complete solution for a wall-mounted e-ink display powered by ESPHome and tightly integrated with Home Assistant. It displays weather, calendar events, room temperatures, and Slovenian date/time, with smart refresh logic and support for dark/light modes.

**Element positioning was planned with this design simulator page (https://jnan.co/tools/displaysim/), which significantly reducing trial-and-error reflashing. I also used different AI to tweak some parts of the code, which again saved me a lot of time.**

# Hardware needed

+ Xiao 7.5" (https://www.seeedstudio.com/XIAO-7-5-ePaper-Panel-p-6416.html)
+ Can be powered via USB-C cable, left running on battery or **permanent power directly to +5V and GND PIN on ESP chip**

# Structure
## ESPHome Source (esphome-wall-monitor.yaml)
+ Defines the ESP32-based e-ink display configuration, including fonts, MQTT, API, WiFi, and display logic.

## Custom rendering for weather, calendar, and room temperatures.

+ Dark/Light mode selection.
+ Smart refresh logic via Home Assistant or API triggers.
+ Uses MQTT and Home Assistant sensors for data.
+ Home Assistant Automations & Templates (ha-*.yaml)

## Provide the backend logic and data for the display:

### ha-combine-calendar.yaml:
+ Collects events from multiple calendars, formats them in Slovenian, and publishes to MQTT for the display.
### ha-weather.yaml:
+ Fetches daily/hourly weather forecasts and exposes them as sensors for ESPHome.
### ha-slovenian_date.yaml:
+ Generates Slovenian-formatted date and time sensors.
### ha-refresh-screen.yam:
+ Smart refresh automation for the display, avoiding unnecessary updates at night and responding to activity.
### Fonts (fonts)
+ Custom TTF fonts for Slovenian characters and Material Design Icons.

# Features
## E-Ink Display:
Shows weather icons, forecasts, room temperatures, calendar events, date, and time.
## Slovenian Localization:
All date, time, and calendar text is localized.
## Smart Refresh:
Refreshes only when needed, with night-time suppression and activity triggers.
## Dark/Light Mode:
User-selectable appearance.
## MQTT & Home Assistant Integration:
Data is fetched and pushed via MQTT and Home Assistant sensors.
