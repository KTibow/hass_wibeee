# Home Assistant: Wibeee Component

This is a custom component developed original for its integration with Circuitor Wibeee (3 Phases)

This concept has been proved on similar devices that are listed below:

| Device        | Model           | Link  |
| ------------- |:-------------:| -----:|
|Circuitor Wibeee| 3 phases | http://wibeee.circutor.com/index_en.html |
|Circuitor Wibeee| 1 phase |  http://wibeee.circutor.com/index_en.html  |
|Mirubee| Unknown models |  https://mirubee.com/es/3-productos |

## ToDo

There is a new project in Github, a CLI in Python for these devices that may be helpful for future integrations of this custom component:
https://github.com/fquinto/pywibeee


# How it works

Once the devices are installed and connected to local wireless network, current energy consumption values are exposed in xml format, the URL of the exposed web service is:

http://<wibeee_ip>/en/status.xml

Example XML are listed in hithub repository

# Home Assistant configuration

1.- Clone repo into `<hass_folder>/custom_components`
```
git clone https://github.com/abacao/hass_wibeee.git <hass_folder>/custom_components/wibeee
```

2.- Add device to home assistant configuration file configuration.yaml

```
sensor:
- platform: wibeee
  host: 192.168.xx.xx
```

Optional
3.- Add new created sensors to groups.yaml

```
supplies_view:
  view: yes
  name: Supplies
  #icon: mdi:network
  entities:
    - group.wibeee_phase1
    - group.wibeee_phase2
    - group.wibeee_phase3
    - group.wibeee_phase4
....

....
wibeee_phase1:
  name: 'Wibeee Phase 1'
  entities:
    - sensor.wibeee_phase1_active_energy
    - sensor.wibeee_phase1_active_power
    - sensor.wibeee_phase1_apparent_power
    - sensor.wibeee_phase1_capacitive_reactive_energy
    - sensor.wibeee_phase1_capacitive_reactive_power
    - sensor.wibeee_phase1_frequency
    - sensor.wibeee_phase1_inductive_reactive_energy
    - sensor.wibeee_phase1_inductive_reactive_power
    - sensor.wibeee_phase1_irms
    - sensor.wibeee_phase1_power_factor
    - sensor.wibeee_phase1_vrms
wibeee_phase2:
  name: 'Wibeee Phase 2'
  entities:
    - sensor.wibeee_phase2_active_energy
    - sensor.wibeee_phase2_active_power
    - sensor.wibeee_phase2_apparent_power
    - sensor.wibeee_phase2_capacitive_reactive_energy
    - sensor.wibeee_phase2_capacitive_reactive_power
    - sensor.wibeee_phase2_frequency
    - sensor.wibeee_phase2_inductive_reactive_energy
    - sensor.wibeee_phase2_inductive_reactive_power
    - sensor.wibeee_phase2_irms
    - sensor.wibeee_phase2_power_factor
    - sensor.wibeee_phase2_vrms
wibeee_phase3:
  name: 'Wibeee Phase 3'
  entities:
    - sensor.wibeee_phase3_active_energy
    - sensor.wibeee_phase3_active_power
    - sensor.wibeee_phase3_apparent_power
    - sensor.wibeee_phase3_capacitive_reactive_energy
    - sensor.wibeee_phase3_capacitive_reactive_power
    - sensor.wibeee_phase3_frequency
    - sensor.wibeee_phase3_inductive_reactive_energy
    - sensor.wibeee_phase3_inductive_reactive_power
    - sensor.wibeee_phase3_irms
    - sensor.wibeee_phase3_power_factor
    - sensor.wibeee_phase3_vrms
wibeee_phase4:
  name: 'Wibeee Phase 4 = Total'
  entities:
    - sensor.wibeee_phase4_active_energy
    - sensor.wibeee_phase4_active_power
    - sensor.wibeee_phase4_apparent_power
    - sensor.wibeee_phase4_capacitive_reactive_energy
    - sensor.wibeee_phase4_capacitive_reactive_power
    - sensor.wibeee_phase4_frequency
    - sensor.wibeee_phase4_inductive_reactive_energy
    - sensor.wibeee_phase4_inductive_reactive_power
    - sensor.wibeee_phase4_irms
    - sensor.wibeee_phase4_power_factor
    - sensor.wibeee_phase4_vrms
```

# Set Logger in Home Assistant

To setup logger for this custom component add following lines to configuration.yaml

```
logger:
  default: warn
  logs:
    custom_components.wibeee.sensor: info
```

Possible log levels: info, debug, warn, ...

# Example View in Home Assistant


![hass_view](https://community-home-assistant-assets.s3.dualstack.us-west-2.amazonaws.com/original/3X/8/4/84825f0d8c1653e37be87c0ed4fa68d4832c8bc0.png "Example View in Home Assistant")



# Useful links

Home Assistant community
https://community.home-assistant.io/t/new-integration-energy-monitoring-device-circutor-wibeee/45276

## custom_components examples

YR Sensor (async)
https://github.com/home-assistant/home-assistant/blob/dev/homeassistant/components/yr/sensor.py

RFLink Sensor (async)
https://github.com/home-assistant/home-assistant/blob/dev/homeassistant/components/rflink/sensor.py

Blueprint
https://github.com/custom-components/blueprint/blob/master/custom_components/blueprint/sensor.py

Youtube Sensor
https://github.com/custom-components/youtube/blob/master/custom_components/youtube/sensor.py

Linky Energy Sensor
https://github.com/home-assistant/home-assistant/blob/dev/homeassistant/components/linky/sensor.py

Other
https://github.com/kstaniek/hass-ampio/blob/master/custom_components/sensor/ampio.py
https://github.com/custom-components/sensor.versions/blob/master/custom_components/sensor/versions.py

Solax (async)
https://github.com/squishykid/home-assistant/blob/23ca4160036f26e9ad08729950ae496b0aabecd0/homeassistant/components/solax/sensor.py
