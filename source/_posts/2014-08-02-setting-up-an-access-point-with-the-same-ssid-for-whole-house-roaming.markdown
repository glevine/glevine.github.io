---
layout: post
title: "Setting up an Access Point with the Same SSID for Whole House Roaming"
date: 2014-08-02 20:56:04 -0400
comments: true
tags: networking, routers, roaming, access point, wifi
---
My wife and I noticed a huge increase in our cell phone data usage after our daughter was born. It turned out that our wifi was brutal in the nursery and we spent a lot of time in there, on our phones, trying to get our newborn to sleep.

The house we lived in did not have any data lines running upstairs, so we didn't have the ability to add another router to the network. And we couldn't change the location of the router. We could have added a repeater or range extender, but I really didn't want to spend the money. We just learned to cope and reduce our data usage where we could.

## Position Access Points
I wanted to be prepared when we started to build our new house, particularly because we had a lot more area to cover. I didn't want to spend the money to run data lines to every room in the house -- especially because wired clients are going extinct -- and I wanted to be able to walk throughout the house without ever dropping wifi. So I needed to place wireless access points in the right locations and have them broadcast the same SSID.

I spent a fair amount of time drawing up various configurations to supply data lines to rooms where I knew heavy streaming would occur (family room, bonus room, and master bedroom) while paying close attention to where the need for a data line overlapped with a good location for an additional router -- to reduce the number of lines I was adding. I settled on adding data lines in the study, family room, bonus room, and master bedroom.

The primary router is located in a closet to the back of one side of the house, where the structured wiring cabinet is located. While it is not ideal to have a router hidden in a closet like that, it allows for the primary router to be close to the cable modem and to the switch supplying the ports throughout the rest of the house; cable lengths can have a dramatic effect on the performance of your network. I also knew that the positions of the access points in relation to the most used rooms would mean that the access points would be relied on more heavily than the primary router for wifi.

The family room and the study are next to each other, but I wanted to have data ports in both rooms. In the family room for streaming purposes. And in the study as a place for attaching network devices that belong in a home office, like a network printer. I chose to put the first access point in the study for four reasons.

1. I don't need four ports in the family room, at least yet. I only need one, so three ports would have gone unused. If I need to attach more devices in the future, then I can just add a network hub.

2. The study is at the front of the house, as far away from the primary router as possible, whereas the family room as at the back of the house. The broadcast overlap is minimal and the first floor is sufficiently covered, even to spots outside where we might want to use the internet.

3. The study is located at the bottom of the stairs, so the singal is stronger up the stairs than if the access point was stationed in the family room.

4. The router would have been hidden in a cabinet in the family room, but can be high up on the desk in the study to reduce interference.

With the first two routers positioned near the perimeter of the house -- as is the master bedroom on the second floor -- we actually got a decent signal for surfing and reading before bed. But once again, the singal was weak to non-existent in our daughter's bedroom. Luckily, the bonus room is located at the center of the house. By putting the third access point in the bonus room, there isn't a corner in the house where we can't get on the wifi.

One caveat is that the bonus room is situated at the top of the stairs. So it is very likely that the broadcast overlap is bad between the two additional access points. For this reason -- and because it's just a good idea -- I separated their channels. The primary router is on channel 157, the study router is on channel 153, and the bonus room router is on channel 161 (For 2.4GHz routers, channels 1, 6, and 11 are recommended.).

## Configure an Access Point
So with the router locations chosen, configuring the routers to use the same SSID was all that remained.

### Devices
**Primary Router** [NETGEAR WNDR3400v3](http://support.netgear.com/product/WNDR3400v3 "NETGEAR WNDR3400v3")

**Access Points** [NETGEAR WNDR3700v3](http://support.netgear.com/product/WNDR3700v3 "NETGEAR WNDR3700v3")

Your newest router should be used as your primary router or else you won't be able to take advantage of some of its newer features. And it is recommended that you only use routers by the same manufacturer to ensure compatibility -- unless you know what you are doing.

### Configure, Install, Repeat
1. Visit http://192.168.1.1 (or the address specified by your router's manufacturer) to access your primary router and log in with your router's username and password.
2. View the attached devices to find an unused IP address.
3. Restore the access point router to factory settings.
4. Disable wifi on your computer and connect it to the access point with an Ethernet cable.
5. Visit http://192.168.1.1 (or the address specified by your access point's manufacturer) and log in with your access point's default username and password.
6. Change the password.
    - *This is tremendously important and not enough people do it.*
    - *I use the same password for all of my routers to keep things simple.*
7. Give the access point a unique name, so you can identify it from your primary router.
8. Configure your access point's 2.4GHz wireless band.
    - **SSID** <network_name>
    - **Channel** Auto
    - **Mode** Up to 145 Mbps
    - **WPA2-PSK [AES]** <network_password>
9. Configure your access point's 5GHz wireless band.
    - **SSID** <network_name>-5g
    - **Channel** 161
    - **Mode** Up to 145 Mbps
    - **WPA2-PSK [AES]** <network_password>
10. Save/Apply these changes.
11. Uncheck the checkbox for "Use Router as DHCP Server" in your access point's LAN Setup.
    - *Your primary router should be the only router that hands out dynamic IP addresses.*
12. Enter the chosen IP address from #2 as the static IP address for this access point.
13. Save/Apply these changes.
14. Connect the access point to the wall port.
    - *Make sure you use one of the Ethernet ports, not the Internet port on the back of your access point.*
15. Power cycle both routers.
    - *You should now be able to reach the access point over wifi using the assigned IP address.*
16. Visit http://192.168.1.1 (or the address specified by your router's manufacturer) to access your primary router and log in.
17. Add an address reservation for the access point at the chosen IP address.
    - *Make sure the device name is unique, preferably matching the unique name you gave to the access point in #7.*

### Helpful Hints
- I learned when connecting my network printer to the access point in the study that any device that is directly wired to an access point will require an assigned IP address. This is because the access point is not a DHCP server; the IP addresses are handed out by the primary router. Devices connected wirelessly to the access point will get their IP address automatically because, as a wireless access point, the access point relays the IP address served from the primary router to the connected device -- but only for wireless connections.

- To update the firmware on your access point you will first need to download the latest firmware. Then log into the access point using its static IP address and update the firmware by browsing to and selecting the file you downloaded. I am not able to download and install the latest firmware when logged into the access point, but you maybe be able to. But downloading it to your computer and then installing it manually for each of your access points will mean you only have to download it once. So it might save you a small slice of time.

## Resources
- [Configuring two wireless routers with one SSID (network name) at home for free roaming](http://www.hanselman.com/blog/ConfiguringTwoWirelessRoutersWithOneSSIDNetworkNameAtHomeForFreeRoaming.aspx "Configuring two wireless routers with one SSID (network name) at home for free roaming") by Scott Hanselman
- [How To Convert a Wireless Router into an Access Point](http://www.smallnetbuilder.com/wireless/wireless-basics/30338-how-to-convert-a-wireless-router-into-an-access-point "How To Convert a Wireless Router into an Access Point") from SmallNetBuilder
- [Set up a wireless router as access point, and connected to 2nd main router](http://kb.netgear.com/app/answers/detail/a_id/19852 "Set up a wireless router as access point, and connected to 2nd main router") from NETGEAR Support