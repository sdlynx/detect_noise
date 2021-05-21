Simple script for detecting noise level. Uses `sox` with USB microphone set to `card 1, device 0`. Needs `node` and `http-server` library.

# Installation

1. Install dependencies
2. Update permissions `chmod u+x detect_noise_level.sh`
3. Run `make install` after all dependencies are installed

This creates two services, `detect_noise` and `detect_noise_api`. Control with `systemd`.

# Home Assistant Sensor

Add this to your `configuration.yaml`:

```
sensor:
  - platform: scrape
    resource: http://10.0.0.161:1111/noise.html
    select: "span"
    name: "AC Noise"
```

Replace `10.0.0.161` with the IP/hostname for where you have the detect_noise scripts running. Must be on the same network.
