# Financial-Institution-System-Network


Financial Network Design
Departments: HR, CS, MK (7th Floor – 40 PCs + 40 IP Phones + 1 AP each), LM, IT (8th Floor – 20 PCs + 20 IP Phones + 1 AP each). Each user may have VoIP phone.
Company owns LAN, WAN, external Server-Side site (DHCP, DNS, WEB, EMAIL). Secure WAN connectivity HQ ↔ Server Site. Dual ISP redundancy (Safaricom + JTL).


<img width="809" height="402" alt="Finance" src="https://github.com/user-attachments/assets/0ecb8e2f-584c-4ba2-8ea1-cf87ab223742" />



Devices: 2x Cisco Catalyst 2911 (HQ + Server-Side), 1x Cisco 2811 (HQ VoIP Gateway), 2x Multilayer Switch (HQ), 6x Access Switches (Departments).

IP Scheme:
Data: 192.168.20.0/24
Voice: 10.10.10.0/24 (Voice VLAN ID 120)
Public: 190.200.100.0

Design: Hierarchical model with redundancy at every layer.
Simulation Tool: Cisco Packet Tracer.

VLANs: Each department separate VLAN + subnet. Voice VLAN 120 global.
Subnetting: Based on department host requirements.

Inter-VLAN Routing: Multilayer switches (SVI) + router-on-a-stick where required.
Core Switches: L3 functionality (routing + switching) with assigned IPs.

DHCP:

* Data → Dedicated DHCP Server (Server-Side).
* Voice → Router-based DHCP (VoIP).
* Server devices → Static IP.

VoIP: Cisco 2811 telephony service, dial plan format (4xx). Internal calling between departments.

Routing: OSPF on routers + multilayer switches.

Security:

* ACL policy controlling HQ ↔ Server-Site access.
* Standard ACL on VTY (SSH access only from IT department).
* SSH configured on all routers + L3 switches.
* Port-Security (Server-Site switch): sticky MAC, violation shutdown.

NAT: PAT using outbound interface IP + ACL rule.

VPN: Site-to-site IPsec VPN (HQ ↔ Server-Side) + ACL rule.

Wireless: 1 AP per department.

ISPs: Each router connected to both ISPs (redundancy + load-balancing).

Basic Config: Hostnames, console & enable passwords, banner MOTD, service password-encryption, no ip domain-lookup.

Implementation: VLAN creation (data + voice), trunking, OSPF area config, DHCP scopes, NAT/PAT, IPsec VPN, SSH hardening, ACL filtering, VoIP configuration, WLAN setup.

Final: Full communication testing verified (Data, Voice, WAN, VPN, Internet, Inter-VLAN).

Scalable, secure, redundant financial enterprise network infrastructure.
