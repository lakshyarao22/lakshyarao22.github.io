---
layout: page
title: "FIX: Cannot get interface MTU on virtmanager"
subtitle: "Configure NAT on virtmanager qemu"
date:   2023-03-16 22:50:21 +0530
categories: Linux
author: "Lakshya Rao"
sitemap:
  priority: 0.9
---

## Installing openvswitch-switch

Firstly we have to install openvswitch

### Ubuntu/Debian

```sh
## Installation
sudo apt install openvswitch-switch

## Enable openvswitch
sudo systemctl enable --now openvswitch-switch.service

## Check status of openvswitch-switch.service
sudo systemctl status openvswitch-switch.service
```


### Arch/Manjaro


```sh
## Installation
sudo pacman -S openvswitch

## Enable openvswitch
sudo systemctl enable --now ovs-vswitchd.service

## Check status of ovs-vswitchd.service
sudo systemctl status ovs-vswitchd.service
```

## Change bridge to NAT

Next we have to change bridge to NAT

- Select NIC in Virtmanager Configuration

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Select_NIC.png)

- Select bridge device to NAT

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Select_NAT.png)

- Do the same for all your Devices

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Do_the_same_for_all_devices.png)


## Booting up NICs before your OS

- Go to boot options in virtmanager settings.

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Go_to_boot_options.png)

- Enable NICs to boot up

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Enable_NICs_to_bootup.png)

- Change Boot sequence and prioritize NIC using arrow keys.

![](https://raw.githubusercontent.com/lakshyarao22/theinquisitive.xyz/main/assets/Boot_sequence.png)

## Bootup

Now try booting into the guest machine. Also see ip address of guest machine using `ip a`.

## Check connectivity

Now from host machine try pinging the guest machine, If successful congratulations your guest is on the same network as host.

If not raise an [issue](https://github.com/lakshyarao22/theinquisitive.xyz/issues) on my github lets try to fix it together.