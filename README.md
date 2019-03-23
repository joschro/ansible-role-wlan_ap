WLAN AP
=========

This Ansible script sets up a Wifi access point using NetworkManager's nmcli tool on RHEL 7 and derivatives like CentOS 7.

Requirements
------------

This role requires the NetworkManager command line interface binary (nmcli) to exist on the system.
IMPORTANT: You need to make sure that the wireless adapter supports access point mode! For a Raspberry Pi, the original PiHut USB Wifi Adapter is recommended: https://thepihut.com/collections/raspberry-pi-wifi/products/usb-wifi-adapter-for-the-raspberry-pi

Role Variables
--------------
```
wlan_ap_ipaddress
```
The ip address of the wifi interface, also serving as the gateway for all wifi clients connecting to this access point. Default value is 192.168.42.1/24.

```
wlan_ap_ssid
```
The wifi network name aka SSID created by the wifi access point. Default is IoT-GW

```
wlan_ap_secret
```
The shared key for the WPA-PSK wireless network.

Please adjust above variables to your needs in vars/main.yml.

Dependencies
------------

None.

Example Playbook
----------------
```
- name: Set up a Wifi access point
  hosts: access_points
  remote_user: root

  roles:
    - {role: "ansible-role-wlan_ap", 
             wlan_ap_ipaddress: "<chosen ip>/24", 
             wlan_ap_ssid: "<chosen ssid>", 
             wlan_ap_secret: "<chosen wlan password>"}
```
(replace each <...> with the values of your choice)

With an inventory file like this for example:

```
[access_points]
access_point ansible_ssh_host=<ip-address> ansible_ssh_user=root
```

License
-------

GPLv3

Author Information
------------------

Joachim Schröder, jos (at) redhat.com
