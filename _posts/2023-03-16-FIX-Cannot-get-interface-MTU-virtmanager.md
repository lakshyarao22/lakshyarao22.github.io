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

```bash
## Installation
sudo apt install openvswitch-switch

## Enable openvswitch
sudo systemctl enable --now openvswitch-switch.service

## Check status of openvswitch-switch.service
sudo systemctl status openvswitch-switch.service
```


### Arch/Manjaro


```bash
## Installation
sudo pacman -S openvswitch

## Enable openvswitch
sudo systemctl enable --now ovs-vswitchd.service

## Check status of ovs-vswitchd.service
sudo systemctl status ovs-vswitchd.service
```

## Change bridge to NAT

Next we have to change bridge to NAT

1. Select NIC in Virtmanager Configuration

![](lakshyarao22/theinquisitive.xyz/assets/Select_NIC.png)

2. Select bridge device to NAT

![](lakshyarao22/theinquisitive.xyz/assets/Select_NAT.png)

3. Do the same for all your Devices

![](lakshyarao22/theinquisitive.xyz/assets/Do_the_same_for_all_devices.png)


## Booting up NICs before your OS

1. Go to boot options in virtmanager settings.

![](lakshyarao22/theinquisitive.xyz/assets/Go_to_boot_options.png)

2. Enable NICs to boot up

![](lakshyarao22/theinquisitive.xyz/assets/Enable_NICs_to_bootup.png)

3. Change Boot sequence and prioritize NIC using arrow keys.

![](lakshyarao22/theinquisitive.xyz/assets/Boot_sequence.png)

## Bootup

Now try booting into the guest machine. Also see ip address of guest machine using `ip a`.

## Check connectivity

Now from host machine try pinging the guest machine, If successful congratulations your guest is on the same network as host.

If not raise an [issue](https://github.com/lakshyarao22/theinquisitive.xyz/issues) on my github lets try to fix it together.