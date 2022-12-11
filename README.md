# Set the charging tresholds for a Thinkpad battery via systemd service

## Create service file 

e.g. /etc/systemd/system/charge-tresholds.service with the following content:

```
[Unit]
Description=Set the charge tresholds at startup.
After=default.target

[Service]
Type=oneshot
ExecStart=/bin/sh -c 'echo 75 > /sys/class/power_supply/BAT0/charge_start_threshold'
ExecStart=/bin/sh -c 'echo 85 > /sys/class/power_supply/BAT0/charge_stop_threshold'

[Install]
WantedBy=default.target
```

## Enable service

```
sudo systemctl enable charge-tresholds.service
```

## Start service (or reboot)

```
sudo systemctl start charge-tresholds.service
```
