---
description: >-
  Subnetting is the process of dividing a network down into smaller networks,
  called subnets
---

# Subnetting

## Key Concepts:

* Subnet Masks: tell devices on a network what part of an IP address is the network portion and what part is the host portion
* CIDR (Classless Inter-Domain Routing) Notation: A way of showing which part of the IP address belongs to the network portion. Example: /24 (this means the first 24 bits of the IP belong to the network portion and the last 8 bits belong to the host portion).
* Network Address: The IP address that represents a network.
* Broadcast Address: The lasts IP in a subnet and is reserved to send messages to all hosts in that subnet.&#x20;

***

\= Subnetting helps break up a network into smaller chunks, like /26 or /27, to suit your needs (of how many available IP addresses you'd like).

\= It is performed on the subnet mask, not on a device IP (e.g., 192.168.0.1).

\= All that changes with subnetting is how the IP address will be interpreted on a subnet mask.

\= More rigid structures of subnets could lead to wastage of IP addresses. For example, there may be 65000 available IPs but you only have 50 hosts. There must be a more efficient allocation of IPs.

***

Example of Subnetting:



Original Mask: /16 -> 255.255.0.0

New Mask: /24 -> 255.255.255.0



\= We subnet /16 subnets into /24 subnets

\= Now, 8 bits are borrowed from the host portion of the subnet mask and given to the network portion.

\= Borrowing these 8 bits leads to 2^8 = 256 new /24 subnets that can be created

\= We now have the first 3 octets belonging to the network and 1 octet belonging to the host.

\= For each subnet, 8 bits are left for the host so we have 2^8 = 256 host addresses per subnet. Minus 2 (because one of the IPs will be for the network and the other will be for the network broadcast) = 254 usable host IP addresses in each of the 2^8 new hosts created.&#x20;

\= In each of these subnets, the third octet of the network address allocated is consistent with the third octet of the IP addresses of the usable hosts within that subnet. E.g., if a subnet had a network address of 192.168.3.0, its usable hosts would be 192.168.3.1 to 192.168.3.254. 192.168.3.0 is excluded as it 's allocated as the network IP and 192.168.3.255 is excluded as it's allocated as the network broadcast.



Summary:

We will look at subnetting 192.168.0.0/16 into 192.168.0.0/24

Before:

* IP Address Range: 192.168.0.0 to 192.168.255.255
* Subnet Mask: 255.255.0.0
* Total Host Bits: 16
* Total Network Bits: 16
* Total Addresses: 2^16 = 65536
* Total Usable Host IPs: 65536 - 2 = 65534
* Network Address: 192.168.0.0
* Broadcast Address: 192.168.255.255
* Number of subnets: 2^0 = 1 (0 host bits borrowed as of right now)



After:

* IP Address Range: 192.168.0.0 to 192.168.255.255 (same range as before split into smaller chunks - network still covers the same IPs but with 256 new subnets inside the network)
* Subnet Mask: 255.255.255.0
* Total Host Bits: 8
* Total Network Bits: 24
* Total Addresses: 2^8 = 256 (per new subnet made)
* Total Usable Host IPs: 254 (per new subnet made)
* Network Address: 192.168.0.0, 192.168.1.0, ... , 192.168.255.0 (each represent a new subnet created)
* Broadcast Address: 192.168.0.255, 192.168.1.255, ... , 192.168.255.255 (each represent the broadcast address for each of the new subnets created)
* Number of subnets: 2^8 = 256 (8 host bits borrowed by now)



> **Hint:** To find the broadcast IP of a subnet, add 1 to the number of hosts. Finally, add this number to the network IP address to find the broadcast IP. If the number exceeds 255, you may have to start incrementing the previous octet of the network IP address to find the broadcast IP.

{% hint style="info" %}
To find the broadcast IP of a subnet, add 1 to the number of hosts. Finally, add this number to the network IP address to find the broadcast IP. If the number exceeds 255, you may have to start incrementing the previous octet of the network IP address to find the broadcast IP.
{% endhint %}



