WLAN AP
=========

This Ansible script sets up a Wifi access point using NetworkManager's nmcli tool on RHEL 7 and derivatives like CentOS 7.

Requirements
------------

This role requires the NetworkManager command line interface binary (nmcli) to exist on the system.

Role Variables
--------------
```
wlan_physical_device
```
The device name of the wifi interface. Default value is `wlan0`

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
             wlan_physical_device: "<device name of your wlan adapter>",
             wlan_ap_ipaddress: "<your wanted ip>", 
             wlan_ap_ssid: "<your wanted ssid>", 
             wlan_ap_secret: "<your wanted wlan password>"}
```

with an inventory file like this for example:

```
[access_points]
access_point ansible_ssh_host=<ip-address> ansible_ssh_user=root
```

License
-------

GPLv3

Author Information
------------------

Joachim Schröder, jos@redhat.com
