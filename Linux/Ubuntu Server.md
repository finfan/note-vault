#ubuntu #linux #/24staticip #static


#linuxip
STATIC I.P.
Ubuntu Linux uses netplan for i.p. Setup
On ubuntu servers it is in the following location

config file location
edit command
```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```
/etc/netplan/50-cloud-init.yaml

```yaml
# This file is generated from information provided by
# the datasource. Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}

network:
  version: 2
  ethernets:
    eth0:
      dhcp4: no
      dhcp6: no
      addresses:
        - 92.168.5.20/24
      routes:
        - to: default
          via: 192.168.5.254
      nameservers:
        addresses:
          - 192.169.5.13
          - 8.8.8.8
	
```

to apply this without reboot enter the following commands

  ```bash
  sudo netplan try
  sudo netplan apply
  ```


