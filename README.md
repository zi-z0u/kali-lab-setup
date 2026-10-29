# kali-lab-setup

Week 1 project for the Cybersecurity Internship at NetworkWalks.

## Overview

This repository documents the setup of a virtual cybersecurity lab using VirtualBox and Kali Linux. It includes the steps taken, the network configuration, and the problems encountered.

## Steps Completed

1. Installed 7-Zip and VirtualBox
2. Created a NAT Network (10.0.0.0/24) in VirtualBox Network Manager
3. Imported the Kali Linux VM from the official OVA
4. Configured the VM's network adapter to use the NAT Network
5. Set a static IP (10.0.0.1)
6. Took a snapshot of the VM after setup

## Troubleshooting

**Problem:** After setting a static IP on the Kali VM, `eth0` had no IPv4 address. `ip a` showed only the IPv6 link-local address, `ip route` still listed `default via 10.0.0.1`, and every ping failed with "Network is unreachable."

**Other symptoms:**
- `ping google.com` returned "Temporary failure in name resolution," which points to DNS.
- `nmcli con up "Wired connection 1"` failed with "IP configuration could not be reserved."

**Steps I took:**
1. Checked the interface state with `ip a` and the routing table with `ip route`.
2. Listed the NetworkManager connections with `nmcli con show` and found that "Wired connection 1" was not active on any device.
3. Tried to reactivate the connection with `nmcli con up`, which failed.
4. Removed the Kali Linux VM from VirtualBox, deleted its files, and reimported Kali Linux from the OVA.
5. After reinstalling, the VM received an IPv4 address and pinged 10.0.0.1 successfully.

## What I Learned

1. I learned how to configure and verify IPv4 addressing, and DNS settings in kali linux.
2. I learned that taking a snapshot before making changes gives me a recovery point if something goes wrong.


