---
description: Tour on how to Natar and PapARt
---

# Your device

## Connectivity

The first step is to connect your device to the internet. We recommand to use a Wifi connection, as the ethernet will be used for developpers. 

###  Local Network

We provide a small router and two ethernet cables for distant development. The best situation is to create a local network between the developper machines and the natar.

{% hint style="info" %}
The default IP for LAN is 192.168.2.1
{% endhint %}

## Assembly guide

You can access the guide on the forum \(in french\):

{% embed url="http://forum.rea.lity.tech/t/guides-de-montage-french-prototype-fab-lab/57" caption="Link to the guide in the forum" %}



{% hint style="warning" %}
You can request an access to this section of the forum after you bought the device.
{% endhint %}

## Update the device 

The distribution we chose has many updates every week. It is not necessary to follow them. However, it is good to stay up to date every month or so. 

We will push updates of the web adminstration, the examples and associated libraries. 

#### Update command 

```text
pacman -Syu
```

#### Update a library 

```bash
pacman -S natar-webserver
```

You can also update with the graphical interface. There is a button in the taskbar.





