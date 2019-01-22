## Raspivid as a service

We use systemd to manage services. That’s why I recommend this page 109 to get started. Even though it looks kinda intimidating at first, this is just robust and rigorous. In the nutshell all you need to do:

create a simple service file (for example, let it be raspicam.service) which contains something like this:

```
[Unit]
Description=raspivid
After=network.target

[Service]
ExecStart=/usr/bin/raspivid -n ....

[Install]
WantedBy=default.target
```

put it in /etc/systemd/system/

sudo systemctl daemon-reload to let systemd know of this service

sudo systemctl start raspivid to test it out

sudo systemctl enable raspivid to enable on boot

https://community.emlid.com/t/raspivid-on-startup/5709

## raspivid to gstreamer command

```bash
raspivid -t 0 -h 720 -w 1080 -fps 25 -hf -b 2000000 -o - | gst-launch-1.0 -v fdsrc ! h264parse !  rtph264pay config-interval=1 pt=96 ! gdppay ! tcpserversink host=YOUR_RPI_IP_ADDRESS port=5000
```

https://raspberry-projects.com/pi/pi-hardware/raspberry-pi-camera/streaming-video-using-gstreamer

