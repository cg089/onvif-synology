# onvif-synology

A JS CLI tool that attempts to bridge the gap between your ONVIF camera's motion detection and Synology Surveillance Station.

## Why?
Some cameras have a PIR sensor, eg https://www.amazon.de/gp/product/B07RX521X6/, but the PIR sensor is unsupported by Synology Disk Station.

However, the event (PIR motion) seems to be available with onvif.

This tool connects to an ONVIF camera and subscribes to these messages. When the motion state changes, it calls the surveillance station event (you have to enable that first) to start capturing video.

## Install

```bash
npm install -g onvif-synology
```

## Usage

```bash
onvif-synology --help
usage: onvif-synology [-h] -s SYN_BASE_URL -U SYN_USERNAME -P SYN_PASSWORD -c HOSTNAME
                         [-u USERNAME] [-p PASSWORD]


ONVIF motion detection events bridge to Synology Surveillance Station

Optional arguments:
  -h, --help            Show this help message and exit.
  -s SYN_BASE_URL, --syn-base-url SYN_BASE_URL
                        Base URL for the Surveillance Station instance
  -U SYN_USERNAME, --syn-suername SYN_USERNAME
                        Username for the Surveillance Station instance
  -P SYN_PASSWORD, --syn-password SYN_PASSWORD
                        Password for the Surveillance Station instance
  -c HOSTNAME, --hostname HOSTNAME
                        hostname/IP of the ONVIF camera
  -u USERNAME, --username USERNAME
                        username for the ONVIF camera
  -p PASSWORD, --password PASSWORD
                        password for the ONVIF camera
```

**Example**

```bash
  onvif-synology \
      --syn-base-url 192.168.1.100 \
      --syn-username username
      --syn-password password
      --hostname 192.168.1.55 \
      --username supersecretusername \
      --password dontshareme
```
```
[monitor 1]: Started
[monitor 1]: CellMotionDetector: Motion Detected: true
Setting monitor 1 to state true
[monitor 1]: CellMotionDetector: Motion Detected: false
Setting monitor 1 to state false
[monitor 1]: CellMotionDetector: Motion Detected: true
Setting monitor 1 to state true
[monitor 1]: CellMotionDetector: Motion Detected: false
```
