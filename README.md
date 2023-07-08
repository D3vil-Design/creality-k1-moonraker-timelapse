
# Moonraker-timelapse for the Creality K1

A fork of moonraker-timelapse for compatibility with an exploited Creality K1. The Creality K1 has a version of ffmpeg that does not support libx264. Considering that the mainboard for the K1 is based on MIPS, I'm unable to compile a new binary to replace the lacking version. Instead, I have modified the moonraker-timelapse component to support the default h264 encoder instead. There may be funkiness that I'll work out as needed, but it works for now. 

## Requirements

This requires you to have root access to your Creality K1. This is done through an exploit using a shadow gcode file. For more information, please check out https://github.com/giveen/K1_Files/tree/ab81d83ca6421c8420a7a85e456059eb0e641bd3/exploit

## Caveats

CRF is not supported with the default h264 encoder.

## Installation

1. Add the camera to Mainsail. URL stream is `http://<printer ip>:8080/?action=stream` and URL snapshot is `http://<printer ip>:8080/?action=snapshot`. Service is MJPEG-Streamer.


2. Download timelapse.py from this repo and place it into /usr/share/moonraker/moonraker/components.

3. Add the following configuration to your moonraker.cfg.
```
[timelapse]
output_path: /usr/data/printer_data/timelapse/
frame_path: /tmp/timelapse/printer
```
  
4. Add timelapse.cfg to your configuration and import it into printer.cfg.