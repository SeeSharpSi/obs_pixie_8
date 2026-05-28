---
title: Dynamic Host Configuration Protocol
source: https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol?wprov=sfla1
author:
  - "[[wikipedia.org]]"
published: 2001-10-07
created: 2026-05-21
description:
tags:
  - clippings
  - dhcp
---
The **Dynamic Host Configuration Protocol** (**DHCP**) is a [network management protocol](https://en.wikipedia.org/wiki/Network_protocol "Network protocol") used on [Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol "Internet Protocol") (IP) networks for automatically assigning [IP addresses](https://en.wikipedia.org/wiki/IP_address "IP address") and other communication parameters to devices connected to the network using a [client–server](https://en.wikipedia.org/wiki/Client%E2%80%93server "Client–server") architecture.[^4]<sup><span title="Page / location: Introduction">: Introduction</span></sup>

The technology eliminates the need for individually configuring network devices manually, and consists of two network components, a centrally installed network DHCP [server](https://en.wikipedia.org/wiki/Server_\(computing\) "Server (computing)") and client instances of the [protocol stack](https://en.wikipedia.org/wiki/Protocol_stack "Protocol stack") on each computer or device. When connected to the network, and periodically thereafter, a client [requests](https://en.wikipedia.org/wiki/Request%E2%80%93response "Request–response") a set of parameters from the server using DHCP.

DHCP can be implemented on networks ranging in size from [residential networks](https://en.wikipedia.org/wiki/Residential_network "Residential network") to large [campus networks](https://en.wikipedia.org/wiki/Campus_network "Campus network") and regional ISP networks.[^5] Many [routers](https://en.wikipedia.org/wiki/Router_\(computing\) "Router (computing)") and [residential gateways](https://en.wikipedia.org/wiki/Residential_gateway "Residential gateway") have DHCP server capability. Most residential network routers receive a [unique](https://en.wikipedia.org/wiki/Universally_unique_identifier "Universally unique identifier") IP address within the ISP network. Within a local network, a DHCP server assigns a local IP address to each device.

DHCP services exist for networks running [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") (IPv4), as well as version 6 ([IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6")). The IPv6 version of the DHCP protocol is commonly called [DHCPv6](https://en.wikipedia.org/wiki/DHCPv6 "DHCPv6").

## History

The [Reverse Address Resolution Protocol](https://en.wikipedia.org/wiki/Reverse_Address_Resolution_Protocol "Reverse Address Resolution Protocol") (RARP) was defined in 1984 for the configuration of simple devices, such as [diskless workstations](https://en.wikipedia.org/wiki/Diskless_workstation "Diskless workstation"), with a suitable IP address.[^6] Acting in the [data link layer](https://en.wikipedia.org/wiki/Data_link_layer "Data link layer"), it made implementation difficult on many server platforms. It required that a server be present on each individual network link. RARP was superseded by the [Bootstrap Protocol](https://en.wikipedia.org/wiki/Bootstrap_Protocol "Bootstrap Protocol") (BOOTP) defined in September 1985.[^7] This introduced the concept of a relay agent, which allowed the forwarding of BOOTP packets across networks, allowing one central BOOTP server to serve hosts on many IP subnets.

DHCP was first defined in October 1993.[^8] [^9] It is based on BOOTP, but can dynamically allocate IP addresses from a pool and reclaim them when they are no longer in use. It can also be used to deliver a wide range of extra configuration parameters to IP clients, including platform-specific parameters.[^10]

Four years later, the DHCPINFORM message type (used for [WPAD](https://en.wikipedia.org/wiki/Web_Proxy_Autodiscovery_Protocol "Web Proxy Autodiscovery Protocol")) and other small changes were added. This definition, from 1997,[^4] remains the core of the standard for IPv4 networks.

[DHCPv6](https://en.wikipedia.org/wiki/DHCPv6 "DHCPv6") was initially defined in 2003.[^11] After updates by many subsequent RFCs, its definition was replaced in 2018,[^12] where [prefix delegation](https://en.wikipedia.org/wiki/Prefix_delegation "Prefix delegation") and [stateless address autoconfiguration](https://en.wikipedia.org/wiki/Stateless_address_autoconfiguration "Stateless address autoconfiguration") were now merged.

## Overview

[Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol "Internet Protocol") (IP) defines how devices communicate within and across local networks on the Internet. A DHCP server can manage IP settings for devices on its local network, e.g., by assigning IP addresses to those devices automatically and dynamically.[^13]

DHCP operates based on the [client–server model](https://en.wikipedia.org/wiki/Client%E2%80%93server_model "Client–server model"). When a computer or other device connects to a network, the DHCP client software sends a DHCP [broadcast](https://en.wikipedia.org/wiki/Broadcasting_\(networking\) "Broadcasting (networking)") query requesting the necessary information. Any DHCP server on the network may service the request. The DHCP server manages a pool of IP addresses and information about client configuration parameters such as [default gateway](https://en.wikipedia.org/wiki/Default_gateway "Default gateway"), [domain name](https://en.wikipedia.org/wiki/Domain_name "Domain name"), the [name servers](https://en.wikipedia.org/wiki/Name_server "Name server"), and [time servers](https://en.wikipedia.org/wiki/Time_server "Time server"). On receiving a DHCP request, the DHCP server may respond with specific information for each client, as previously configured by an administrator, or with a specific address and any other information valid for the entire network and for the time period for which the allocation (*lease*) is valid. A DHCP client typically queries this information immediately after [booting](https://en.wikipedia.org/wiki/Booting "Booting"), and periodically thereafter before the expiration of the information. When a DHCP client refreshes an assignment, it initially requests the same parameter values, but the DHCP server may assign a new address based on the assignment policies set by administrators.

On large networks that consist of multiple links, a single DHCP server may service the entire network when aided by DHCP relay agents located on the interconnecting routers. Such agents relay messages between DHCP clients and DHCP servers located on different subnets.

Depending on implementation, the DHCP server may have three methods of allocating IP addresses:

Dynamic allocation

A [network administrator](https://en.wikipedia.org/wiki/Network_administrator "Network administrator") reserves a range of IP addresses for DHCP, and each DHCP client on the [LAN](https://en.wikipedia.org/wiki/LAN "LAN") is configured to request an IP address from the DHCP [server](https://en.wikipedia.org/wiki/Server_\(computing\) "Server (computing)") during network initialization. The request-and-grant process uses a lease concept with a controllable time period, allowing the DHCP server to reclaim and then reallocate IP addresses that are not renewed.

Automatic allocation

The DHCP server permanently assigns an IP address to a requesting client from a range defined by an administrator. This is like dynamic allocation, but the DHCP server keeps a table of past IP address assignments, so that it can preferentially assign to a client the same IP address that the client previously had.

Manual allocation

This method is also variously called *static DHCP allocation*, *fixed address allocation*, *reservation*, and *MAC/IP address binding*. An administrator maps a unique identifier (a *client id* or [MAC address](https://en.wikipedia.org/wiki/MAC_address "MAC address")) for each client to an IP address, which is offered to the requesting client. DHCP servers may be configured to fall back to other methods if this fails.

DHCP services are used for [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") (IPv4) and [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6"). The details of the protocol for IPv4 and IPv6 differ sufficiently that they may be considered separate protocols.[^14] For the IPv6 operation, devices may alternatively use stateless address autoconfiguration. IPv6 hosts may also use [link-local addressing](https://en.wikipedia.org/wiki/Link-local_addressing "Link-local addressing") to achieve operations restricted to the local network link.

## Operation

![[330px-DHCP_session.svg.png]]

An illustration of a typical non-renewing DHCP session; each message may be either a broadcast or a unicast, depending on the DHCP client capabilities. 4

The DHCP employs a [connectionless](https://en.wikipedia.org/wiki/Connectionless "Connectionless") service model, using the [User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol "User Datagram Protocol") (UDP). It is implemented with two UDP port numbers for its operations which are the same as for the bootstrap protocol ([BOOTP](https://en.wikipedia.org/wiki/BOOTP "BOOTP")). The server listens on UDP port number 67, and the client listens on UDP port number 68.

DHCP operations fall into four phases: server discovery, IP lease offer, IP lease request, and IP lease acknowledgement. These stages are often abbreviated as DORA for discovery, offer, request, and acknowledgement.

The DHCP operation begins with clients broadcasting a request. If the client and server are in different [Broadcast Domains](https://en.wikipedia.org/wiki/Broadcast_domain "Broadcast domain"), a [DHCP Helper or DHCP Relay Agent](#Relaying) may be used. Clients requesting renewal of an existing lease may communicate directly via UDP [unicast](https://en.wikipedia.org/wiki/Unicast "Unicast"), since the client already has an established IP address at that point. Additionally, there is a BROADCAST flag (1 bit in 2 byte flags field, where all other bits are reserved and so are set to 0) the client can use to indicate in which way (broadcast or unicast) it can receive the DHCPOFFER: 0x8000 for broadcast, 0x0000 for unicast.[^4] Usually, the DHCPOFFER is sent through unicast. For those hosts which cannot accept unicast packets before IP addresses are configured, this flag can be used to work around this issue.

### Discovery

The DHCP client broadcasts a DHCPDISCOVER message on the network subnet using the destination address *255.255.255.255* (limited broadcast) or the specific subnet [broadcast address](https://en.wikipedia.org/wiki/Broadcast_address "Broadcast address") (directed broadcast). A DHCP client may also request an IP address in the DHCPDISCOVER, which the server may take into account when selecting an address to offer.

For example, if HTYPE is set to 1, to specify that the medium used is [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet"), HLEN is set to 6 because an Ethernet address (MAC address) is 6 octets long. The CHADDR is set to the MAC address used by the client. Some options are set as well.

<table><caption>Example Ethernet frame with a DHCPDISCOVER message</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32"><i>Destination MAC (<i>FF:FF:FF:FF:FF:FF</i>)</i></td></tr><tr><th>4</th><th>32</th><td colspan="16"></td><td colspan="16"></td></tr><tr><th>8</th><th>64</th><td colspan="32"><i>Source MAC (<i>00:05:3C:04:8D:59</i>)</i></td></tr><tr><th>12</th><th>96</th><td colspan="16"><i><abbr>EtherType</abbr> (0x0800)</i></td><td colspan="16"></td></tr><tr><th>16</th><th>128</th><td colspan="32" rowspan="3"><i>IPv4 packet, containing a UDP PDU with DHCP payload...</i></td></tr><tr><th>20</th><th>160</th></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>⋮</th><th>⋮</th><td colspan="32"><i>Frame Check Sequence</i></td></tr></tbody></table>

<table><caption>IPv4 Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32" rowspan="2"><i>IPv4 header start</i></td></tr><tr><th>4</th><th>32</th></tr><tr><th>8</th><th>64</th><td colspan="8"><i>TTL</i></td><td colspan="8"><i>Protocol (17 UDP)</i></td><td colspan="16"><i>Header Checksum</i></td></tr><tr><th>12</th><th>96</th><td colspan="32"><i>Source Address (<i>0.0.0.0</i>)</i></td></tr><tr><th>16</th><th>128</th><td colspan="32"><i>Destination Address</i></td></tr></tbody></table>

<table><caption>UDP Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>20</th><th>160</th><td colspan="16"><i>Source Port (68)</i></td><td colspan="16"><i>Destination Port (67)</i></td></tr><tr><th>24</th><th>192</th><td colspan="16"><i>Length</i></td><td colspan="16"><i>Checksum</i></td></tr></tbody></table>

<table><caption>DHCP Payload: DHCPDISCOVER</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>28</th><th>224</th><td colspan="8"><i><abbr>OP</abbr> (0x01)</i></td><td colspan="8"><i><abbr>HTYPE</abbr> (0x01)</i></td><td colspan="8"><i><abbr>HLEN</abbr> (0x06)</i></td><td colspan="8"><i>HOPS (0x00)</i></td></tr><tr><th>32</th><th>256</th><td colspan="32"><i>XID (0x3903F326)</i></td></tr><tr><th>36</th><th>288</th><td colspan="16"><i>SECS (0x0000)</i></td><td colspan="16"><i>FLAGS (0x0000)</i></td></tr><tr><th>40</th><th>320</th><td colspan="32"><i>CIADDR (Client IP address: 0x00000000)</i></td></tr><tr><th>44</th><th>352</th><td colspan="32"><i>YIADDR (Your IP address: 0x00000000)</i></td></tr><tr><th>48</th><th>384</th><td colspan="32"><i>SIADDR (Server IP address: 0x00000000)</i></td></tr><tr><th>52</th><th>416</th><td colspan="32"><i><abbr>GIADDR</abbr> (Gateway IP address: 0x00000000)</i></td></tr><tr><th>56</th><th>448</th><td colspan="32" rowspan="4"><i>CHADDR (Client Hardware address: 0x00053C04<br>0x8D590000<br>0x00000000<br>0x00000000)</i></td></tr><tr><th>60</th><th>480</th></tr><tr><th>64</th><th>512</th></tr><tr><th>68</th><th>544</th></tr><tr><th>72</th><th>576</th><td colspan="32" rowspan="3"><i>192 octets of 0s, or overflow space for additional options; BOOTP legacy.</i></td></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>260</th><th>2080</th></tr><tr><th>264</th><th>2112</th><td colspan="32"><i><a href="https://en.wikipedia.org/wiki/Magic_Cookie">Magic Cookie</a> (0x63825363)</i></td></tr></tbody></table>

<table><caption>DHCP Options (in <a href="https://en.wikipedia.org/wiki/Type-length-value">TLV</a> format)</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>268</th><th>2144</th><td colspan="24"><i>First option: 0x350101: Option 53 (DHCP Message Type) 1 octet (containing DHCPDISCOVER)</i></td><td colspan="8"><i>Second option:</i>↴</td></tr><tr><th>272</th><th>2176</th><td colspan="32"><i>↪0x3204c0a80164: Option 50 (Request IP address) 4 octets (containing <i>192.168.1.100</i>)</i></td></tr><tr><th>276</th><th>2208</th><td colspan="32"><i><abbr>Third option: 0x370401030f06: Option: 55 (Parameter Request List) 4 octets</abbr></i> ↴</td></tr><tr><th>280</th><th>2240</th><td colspan="8"><i>↪ <abbr>PRL cont...</abbr></i></td><td colspan="1"><i><abbr><small>ff</small></abbr></i></td></tr></tbody></table>

### Offer

When a DHCP server receives a DHCPDISCOVER message from a client, which is an IP address lease request, the DHCP server reserves an IP address for the client and makes a lease offer by sending a DHCPOFFER message to the client. This message may contain the client's *Client ID* (Option 61, containing a unique value, traditionally a MAC address), the IP address that the server is offering, the subnet mask, the lease duration, and the IP address of the DHCP server making the offer. The DHCP server may also take notice of the hardware-level MAC address (as specified in the CHADDR field). This field must be used to identify the client, if no Client ID is provided in the DHCP packet.[^4]<sup><span title="Location: §4.2">: §4.2</span></sup>

The DHCP server determines the configuration based on the client's hardware address as specified in the CHADDR (client hardware address) field. In the following example the server (*192.168.1.1*) specifies the client's IP address in the YIADDR (your IP address) field.

<table><caption>Example Ethernet frame with a DHCPOFFER message</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32"><i>Destination MAC (<i>00:05:3C:04:8D:59</i>)</i></td></tr><tr><th>4</th><th>32</th><td colspan="16"></td><td colspan="16"></td></tr><tr><th>8</th><th>64</th><td colspan="32"><i>Source MAC (<i>B4:0C:25:E3:7D:62</i>)</i></td></tr><tr><th>12</th><th>96</th><td colspan="16"><i><abbr>EtherType</abbr> (0x0800)</i></td><td colspan="16"></td></tr><tr><th>16</th><th>128</th><td colspan="32" rowspan="3"><i>IPv4 packet, containing a UDP PDU with DHCP payload...</i></td></tr><tr><th>20</th><th>160</th></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>⋮</th><th>⋮</th><td colspan="32"><i>Frame Check Sequence</i></td></tr></tbody></table>

<table><caption>IPv4 Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32" rowspan="2"><i>IPv4 header start</i></td></tr><tr><th>4</th><th>32</th></tr><tr><th>8</th><th>64</th><td colspan="8"><i>TTL</i></td><td colspan="8"><i>Protocol (17 UDP)</i></td><td colspan="16"><i>Header Checksum</i></td></tr><tr><th>12</th><th>96</th><td colspan="32"><i>Source Address (<i>192.168.1.1</i>)</i></td></tr><tr><th>16</th><th>128</th><td colspan="32"><i>Destination Address (<i>192.168.1.100</i>)</i></td></tr></tbody></table>

<table><caption>UDP Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>20</th><th>160</th><td colspan="16"><i>Source Port (67)</i></td><td colspan="16"><i>Destination Port (68)</i></td></tr><tr><th>24</th><th>192</th><td colspan="16"><i>Length</i></td><td colspan="16"><i>Checksum</i></td></tr></tbody></table>

<table><caption>DHCP Payload: DHCPOFFER</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>28</th><th>224</th><td colspan="8"><i><abbr>OP (0x02)</abbr></i></td><td colspan="8"><i>HTYPE (0x01)</i></td><td colspan="8"><i>HLEN (0x06)</i></td><td colspan="8"><i>HOPS (0x00)</i></td></tr><tr><th>32</th><th>256</th><td colspan="32"><i>XID (0x3903F326)</i></td></tr><tr><th>36</th><th>288</th><td colspan="16"><i>SECS (0x0000)</i></td><td colspan="16"><i>FLAGS (0x0000)</i></td></tr><tr><th>40</th><th>320</th><td colspan="32"><i>CIADDR (Client IP address: 0x00000000)</i></td></tr><tr><th>44</th><th>352</th><td colspan="32"><i>YIADDR (Your IP address: 0xC0A80164 or <i>192.168.1.100</i>)</i></td></tr><tr><th>48</th><th>384</th><td colspan="32"><i>SIADDR (Server IP address: 0xC0A80101 or <i>192.168.1.1</i>)</i></td></tr><tr><th>52</th><th>416</th><td colspan="32"><i>GIADDR (Gateway IP address: 0x00000000)</i></td></tr><tr><th>56</th><th>448</th><td colspan="32" rowspan="4"><i>CHADDR (Client Hardware address: 0x00053C04<br>0x8D590000<br>0x00000000<br>0x00000000)</i></td></tr><tr><th>60</th><th>480</th></tr><tr><th>64</th><th>512</th></tr><tr><th>68</th><th>544</th></tr><tr><th>72</th><th>576</th><td colspan="32" rowspan="3"><i>192 octets of 0s, or overflow space for additional options; BOOTP legacy.</i></td></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>260</th><th>2080</th></tr><tr><th>264</th><th>2112</th><td colspan="32"><i><a href="https://en.wikipedia.org/wiki/Magic_Cookie">Magic Cookie</a> (0x63825363)</i></td></tr></tbody></table>

<table><caption>DHCP Options (in <a href="https://en.wikipedia.org/wiki/Type-length-value">TLV</a> format)</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>268</th><th>2144</th><td colspan="24"><i>First option: 0x350102: Option 53 (DHCP Message Type) 1 octet (containing DHCPOFFER)</i></td><td colspan="8"><i>Second option:</i>↴</td></tr><tr><th>272</th><th>2176</th><td colspan="32"><i>↪0x0104ffffff00: Option 1 (Subnet mask) 4 octets (containing <i>255.255.255.0</i>)</i></td></tr><tr><th>276</th><th>2208</th><td colspan="32"><i>Third option: 0x0304c0A80101: Option: 3 (Router) 4 octets (containing <i>192.168.1.1</i>)</i> ↴</td></tr><tr><th>280</th><th>2240</th><td colspan="8"><i>↪Router cont...</i></td><td colspan="24"><i>Fourth option: 0x330400015080: Option 51 (Address time) 4 octets (a 86400 second lease time)</i> ↴</td></tr><tr><th>284</th><th>2272</th><td colspan="16"><i>↪Address time cont...</i></td><td colspan="16"><i>Fifth option:</i></td></tr><tr><th>288</th><th>2304</th><td colspan="32" rowspan="3"><i>0x060c09070a0f09070a1009070a13:<br>Option 6 (Domain Server) 14 octets (containing <i>9.7.10.15</i>,<i>9.7.10.16</i>,<i>9.7.10.18</i>)</i></td></tr><tr><th>292</th><th>2336</th></tr><tr><th>296</th><th>2368</th></tr><tr><th>300</th><th>2400</th><td colspan="12"></td><td><i><abbr><small>ff</small></abbr></i></td></tr></tbody></table>

### Request

In response to the DHCP offer, the client replies with a DHCPREQUEST message, broadcast to the server,[^1] requesting the offered address. A client can receive DHCP offers from multiple servers, but it will accept only one DHCP offer.

The client must send the *server identification* option in the DHCPREQUEST message, indicating the server whose offer the client has selected.[^4]<sup><span title="Page / location: Section 3.1, Item 3">: Section 3.1, Item 3</span> </sup> When other DHCP servers receive this message, they withdraw any offers that they have made to the client and return their offered IP address to the pool of available addresses.

<table><caption>Example Ethernet frame with a DHCPREQUEST message</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32"><i><abbr>Destination MAC</abbr> (<i>FF:FF:FF:FF:FF:FF</i>)</i></td></tr><tr><th>4</th><th>32</th><td colspan="16"></td><td colspan="16"></td></tr><tr><th>8</th><th>64</th><td colspan="32"><i>Source MAC (<i>00:05:3C:04:8D:59</i>)</i></td></tr><tr><th>12</th><th>96</th><td colspan="16"><i><abbr>EtherType</abbr> (0x0800)</i></td><td colspan="16"></td></tr><tr><th>16</th><th>128</th><td colspan="32" rowspan="3"><i>IPv4 packet, containing a UDP PDU with DHCP payload...</i></td></tr><tr><th>20</th><th>160</th></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>⋮</th><th>⋮</th><td colspan="32"><i>Frame Check Sequence</i></td></tr></tbody></table>

<table><caption>IPv4 Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32" rowspan="2"><i>IPv4 header start</i></td></tr><tr><th>4</th><th>32</th></tr><tr><th>8</th><th>64</th><td colspan="8"><i>TTL</i></td><td colspan="8"><i>Protocol (17 UDP)</i></td><td colspan="16"><i>Header Checksum</i></td></tr><tr><th>12</th><th>96</th><td colspan="32"><i>Source Address (<i>0.0.0.0</i>)</i></td></tr><tr><th>16</th><th>128</th><td colspan="32"><i>Destination Address (<i>255.255.255.255</i>)</i></td></tr></tbody></table>

<table><caption>UDP Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>20</th><th>160</th><td colspan="16"><i>Source Port (68)</i></td><td colspan="16"><i>Destination Port (67)</i></td></tr><tr><th>24</th><th>192</th><td colspan="16"><i>Length</i></td><td colspan="16"><i>Checksum</i></td></tr></tbody></table>

<table><caption>DHCP Payload: DHCPREQUEST</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>28</th><th>224</th><td colspan="8"><i><abbr>OP (0x01)</abbr></i></td><td colspan="8"><i>HTYPE (0x01)</i></td><td colspan="8"><i>HLEN (0x06)</i></td><td colspan="8"><i>HOPS (0x00)</i></td></tr><tr><th>32</th><th>256</th><td colspan="32"><i>XID (0x3903F326)</i></td></tr><tr><th>36</th><th>288</th><td colspan="16"><i>SECS (0x0000)</i></td><td colspan="16"><i>FLAGS (0x0000)</i></td></tr><tr><th>40</th><th>320</th><td colspan="32"><i>CIADDR (Client IP address: 0x00000000)</i></td></tr><tr><th>44</th><th>352</th><td colspan="32"><i>YIADDR (Your IP address: 0x00000000)</i></td></tr><tr><th>48</th><th>384</th><td colspan="32"><i>SIADDR (Server IP address: 0xc0a80101 or <i>192.168.1.1</i>)</i></td></tr><tr><th>52</th><th>416</th><td colspan="32"><i>GIADDR (Gateway IP address: 0x00000000)</i></td></tr><tr><th>56</th><th>448</th><td colspan="32" rowspan="4"><i>CHADDR (Client Hardware address: 0x00053C04<br>0x8D590000<br>0x00000000<br>0x00000000)</i></td></tr><tr><th>60</th><th>480</th></tr><tr><th>64</th><th>512</th></tr><tr><th>68</th><th>544</th></tr><tr><th>72</th><th>576</th><td colspan="32" rowspan="3"><i>192 octets of 0s, or overflow space for additional options; BOOTP legacy.</i></td></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>260</th><th>2080</th></tr><tr><th>264</th><th>2112</th><td colspan="32"><i><a href="https://en.wikipedia.org/wiki/Magic_Cookie">Magic Cookie</a> (0x63825363)</i></td></tr></tbody></table>

<table><caption>DHCP Options (in <a href="https://en.wikipedia.org/wiki/Type-length-value">TLV</a> format)</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>268</th><th>2144</th><td colspan="24"><i>First option: 0x350103: Option 53 (DHCP Message Type) 1 octet (containing DHCPREQUEST)</i></td><td colspan="8"><i>Second option:</i>↴</td></tr><tr><th>272</th><th>2176</th><td colspan="32"><i>↪ <abbr>0x3204c0a80164: Option 50 (Request IP address) 4 octets (containing <i>192.168.1.100</i>)</abbr></i></td></tr><tr><th>276</th><th>2208</th><td colspan="32"><i><abbr>Third option: 0x3604c0a801601: Option: 54 (DHCP Server) 4 octets (containing <i>192.168.1.1</i>)</abbr></i> ↴</td></tr><tr><th>280</th><th>2240</th><td colspan="8"><i>↪DHCP Server cont...</i></td><td colspan="1"><i><abbr><small>ff</small></abbr></i></td></tr></tbody></table>

### Acknowledgement

When the DHCP server receives the DHCPREQUEST message from the client, the configuration process enters its final phase. The acknowledgement phase involves sending a DHCPACK packet to the client. This packet includes the lease duration and any other configuration information that the client might have requested. At this point, the IP configuration process is completed.

The protocol expects the DHCP client to configure its network interface with the negotiated parameters.

<table><caption>Example Ethernet frame with a DHCPACK message</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32"><i><abbr>Destination MAC</abbr> (<i>00:05:3C:04:8D:59</i>)</i></td></tr><tr><th>4</th><th>32</th><td colspan="16"></td><td colspan="16"></td></tr><tr><th>8</th><th>64</th><td colspan="32"><i>Source MAC (<i>B4:0C:25:E3:7D:62</i>)</i></td></tr><tr><th>12</th><th>96</th><td colspan="16"><i><abbr>EtherType</abbr> (0x0800)</i></td><td colspan="16"></td></tr><tr><th>16</th><th>128</th><td colspan="32" rowspan="3"><i>IPv4 packet, containing a UDP PDU with DHCP payload...</i></td></tr><tr><th>20</th><th>160</th></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>⋮</th><th>⋮</th><td colspan="32"><i>Frame Check Sequence</i></td></tr></tbody></table>

<table><caption>IPv4 Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>0</th><th>0</th><td colspan="32" rowspan="2"><i>IPv4 header start</i></td></tr><tr><th>4</th><th>32</th></tr><tr><th>8</th><th>64</th><td colspan="8"><i>TTL</i></td><td colspan="8"><i>Protocol (17 UDP)</i></td><td colspan="16"><i>Header Checksum</i></td></tr><tr><th>12</th><th>96</th><td colspan="32"><i>Source Address (<i>192.168.1.1</i>)</i></td></tr><tr><th>16</th><th>128</th><td colspan="32"><i>Destination Address (<i>192.168.1.100</i>)</i></td></tr></tbody></table>

<table><caption>UDP Header</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>20</th><th>160</th><td colspan="16"><i>Source Port (67)</i></td><td colspan="16"><i>Destination Port (68)</i></td></tr><tr><th>24</th><th>192</th><td colspan="16"><i>Length</i></td><td colspan="16"><i>Checksum</i></td></tr></tbody></table>

<table><caption>DHCP Payload: DHCPACK</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>28</th><th>224</th><td colspan="8"><i><abbr>OP (0x02)</abbr></i></td><td colspan="8"><i>HTYPE (0x01)</i></td><td colspan="8"><i>HLEN (0x06)</i></td><td colspan="8"><i>HOPS (0x00)</i></td></tr><tr><th>32</th><th>256</th><td colspan="32"><i>XID (0x3903F326)</i></td></tr><tr><th>36</th><th>288</th><td colspan="16"><i>SECS (0x0000)</i></td><td colspan="16"><i>FLAGS (0x0000)</i></td></tr><tr><th>40</th><th>320</th><td colspan="32"><i>CIADDR (Client IP address: 0x00000000)</i></td></tr><tr><th>44</th><th>352</th><td colspan="32"><i>YIADDR (Your IP address: 0xC0A80164 or <i>192.168.1.100</i>)</i></td></tr><tr><th>48</th><th>384</th><td colspan="32"><i>SIADDR (Server IP address: 0xC0A80101 or <i>192.168.1.1</i>)</i></td></tr><tr><th>52</th><th>416</th><td colspan="32"><i>GIADDR (Gateway IP address: 0x00000000)</i></td></tr><tr><th>56</th><th>448</th><td colspan="32" rowspan="4"><i>CHADDR (Client Hardware address: 0x00053C04<br>0x8D590000<br>0x00000000<br>0x00000000)</i></td></tr><tr><th>60</th><th>480</th></tr><tr><th>64</th><th>512</th></tr><tr><th>68</th><th>544</th></tr><tr><th>72</th><th>576</th><td colspan="32" rowspan="3"><i>192 octets of 0s, or overflow space for additional options; BOOTP legacy.</i></td></tr><tr><th>⋮</th><th>⋮</th></tr><tr><th>260</th><th>2080</th></tr><tr><th>264</th><th>2112</th><td colspan="32"><i><a href="https://en.wikipedia.org/wiki/Magic_Cookie">Magic Cookie</a> (0x63825363)</i></td></tr></tbody></table>

<table><caption>DHCP Options (in <a href="https://en.wikipedia.org/wiki/Type-length-value">TLV</a> format)</caption><tbody><tr><th><i>Offset</i></th><th><a href="https://en.wikipedia.org/wiki/Octet_(computing)">Octet</a></th><th colspan="8">0</th><th colspan="8">1</th><th colspan="8">2</th><th colspan="8">3</th></tr><tr><th>Octet</th><th><a href="https://en.wikipedia.org/wiki/Bit">Bit</a></th><th>0</th><th>1</th><th>2</th><th>3</th><th>4</th><th>5</th><th>6</th><th>7</th><th>8</th><th>9</th><th>10</th><th>11</th><th>12</th><th>13</th><th>14</th><th>15</th><th>16</th><th>17</th><th>18</th><th>19</th><th>20</th><th>21</th><th>22</th><th>23</th><th>24</th><th>25</th><th>26</th><th>27</th><th>28</th><th>29</th><th>30</th><th>31</th></tr><tr><th>268</th><th>2144</th><td colspan="24"><i>First option: 0x350105: Option 53 (DHCP Message Type) 1 octet (containing DHCPACK)</i></td><td colspan="8"><i>Second option:</i>↴</td></tr><tr><th>272</th><th>2176</th><td colspan="32"><i>↪0x0104ffffff00: Option 1 (Subnet mask) 4 octets (containing <i>255.255.255.0</i>)</i></td></tr><tr><th>276</th><th>2208</th><td colspan="32"><i>Third option: 0x0304c0A80101: Option: 3 (Router) 4 octets (containing <i>192.168.1.1</i>)</i> ↴</td></tr><tr><th>280</th><th>2240</th><td colspan="8"><i>↪Router cont...</i></td><td colspan="24"><i>Fourth option: 0x330400015080: Option 51 (Address time) 4 octets (a 86400 second lease time)</i> ↴</td></tr><tr><th>284</th><th>2272</th><td colspan="16"><i>↪Address time cont...</i></td><td colspan="16"><i>Fifth option:</i></td></tr><tr><th>288</th><th>2304</th><td colspan="32" rowspan="3"><i>0x060c09070a0f09070a1009070a13:<br>Option 6 (Domain Server) 14 octets (containing <i>9.7.10.15</i>,<i>9.7.10.16</i>,<i>9.7.10.18</i>)</i></td></tr><tr><th>292</th><th>2336</th></tr><tr><th>296</th><th>2368</th></tr><tr><th>300</th><th>2400</th><td colspan="12"></td><td><i><abbr><small>ff</small></abbr></i></td></tr></tbody></table>

### Selecting and configuring IP addresses

When the server is reusing an IP address from its pool, it may first check (using [ping](https://en.wikipedia.org/wiki/Ping_\(networking_utility\) "Ping (networking utility)")) to see if it is not taken already.[^4]<sup><span title="Page / location: sec. 2.2">: sec. 2.2</span> </sup> This may happen if a host is configured manually with an IP address that lies within the DHCP scope.

Before claiming an IP address, the client should probe the newly received address (e.g. with [ARP](https://en.wikipedia.org/wiki/Address_Resolution_Protocol "Address Resolution Protocol")), in order to find if there is another host present in the network with the proposed IP address.[^4]<sup><span title="Page / location: sec. 2.2">: sec. 2.2</span> </sup> If there is no reply, this address does not conflict with that of another host, so it is free to be used. If this probe finds another computer using that address, the client should broadcast a DHCPDECLINE to the DHCP server(s).

### Information

A DHCP client may request more information than the server sent with the original DHCPOFFER. The client may also request repeat data for a particular application. For example, browsers use *DHCP Inform* to obtain web proxy settings via [WPAD](https://en.wikipedia.org/wiki/Web_Proxy_Auto-Discovery_Protocol "Web Proxy Auto-Discovery Protocol").

### Releasing

The client sends a request to the DHCP server to release the DHCP information and the client deactivates its IP address. As client devices usually do not know when users may unplug them from the network, the protocol does not mandate the sending of *DHCP Release*.

## Client configuration parameters

A DHCP server can provide optional configuration parameters to the client. RFC 2132 describes the available DHCP options defined by [Internet Assigned Numbers Authority](https://en.wikipedia.org/wiki/Internet_Assigned_Numbers_Authority "Internet Assigned Numbers Authority") (IANA) - DHCP and BOOTP PARAMETERS.[^15]

A DHCP client can select, manipulate and overwrite parameters provided by a DHCP server. In Unix-like systems this client-level refinement typically takes place according to the values in the configuration file */etc/dhclient.conf*.

## Options

Options are octet strings of varying length. This is called [Type–length–value](https://en.wikipedia.org/wiki/Type%E2%80%93length%E2%80%93value "Type–length–value") encoding. The first octet is the option code, the second octet is the number of following octets and the remaining octets are code dependent. For example, the DHCP message-type option for an offer would appear as 0x35, 0x01, 0x02, where 0x35 is code 53 for "DHCP message type", 0x01 means one octet follows and 0x02 is the value of "offer".

The following tables list the available DHCP options.[^16] [^15]

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 0 | Pad | 0 [octets](https://en.wikipedia.org/wiki/Octet_\(computing\) "Octet (computing)") | Can be used to pad other options so that they are aligned to the word boundary; is not followed by length byte |
| 1 | Subnet mask | 4 octets | Client's subnet mask as per [RFC 950](https://datatracker.ietf.org/doc/html/rfc950). If both the subnet mask and the router option (option 3) are included, the subnet mask option must be first. |
| 2 | Time offset | 4 octets | Time offset of the client's subnet in seconds from Coordinated Universal Time (UTC). The offset is expressed as a two's complement 32-bit integer. A positive offset indicates a location east of the zero meridian and a negative offset indicates a location west of the zero meridian. |
| 3 | Router | Multiples of 4 octets | Available routers, should be listed in order of preference |
| 4 | Time server | Multiples of 4 octets | Available [Time Protocol](https://en.wikipedia.org/wiki/Time_Protocol "Time Protocol") servers to synchronise with, should be listed in order of preference |
| 5 | Name server | Multiples of 4 octets | Available [IEN 116](https://en.wikipedia.org/wiki/IEN_116 "IEN 116") name servers, should be listed in order of preference |
| 6 | Domain name server | Multiples of 4 octets | Available [DNS](https://en.wikipedia.org/wiki/DNS "DNS") servers, should be listed in order of preference |
| 7 | Log server | Multiples of 4 octets | Available log servers, should be listed in order of preference |
| 8 | Cookie server | Multiples of 4 octets | *Cookie* in this case means "fortune cookie" or "quote of the day", a pithy or humorous anecdote often sent as part of a logon process on large computers; it has nothing to do with [cookies sent by websites](https://en.wikipedia.org/wiki/HTTP_cookie "HTTP cookie"). |
| 9 | LPR Server | Multiples of 4 octets | A list of [Line Printer Daemon protocol](https://en.wikipedia.org/wiki/Line_Printer_Daemon_protocol "Line Printer Daemon protocol") servers available to the client, should be listed in order of preference |
| 10 | Impress server | Multiples of 4 octets | A list of Imagen Impress servers available to the client, should be listed in order of preference |
| 11 | Resource location server | Multiples of 4 octets | A list of [Resource Location Protocol](https://en.wikipedia.org/wiki/Resource_Location_Protocol?action=edit&redlink=1 "Resource Location Protocol (page does not exist)") servers available to the client, should be listed in order of preference |
| 12 | Host name | Minimum of 1 octet | Name of the client. The name may be qualified with the local domain name. |
| 13 | Boot file size | 2 octets | Length of the boot image in 512B blocks |
| 14 | [Merit](https://en.wikipedia.org/wiki/Merit_Network "Merit Network") dump file | Minimum of 1 octet | Path where crash dumps should be stored |
| 15 | Domain name | Minimum of 1 octet |  |
| 16 | Swap server | 4 octets | The IP address of a server where a swap service (e.g., swap over NFS) is provided for diskless workstations [^17] |
| 17 | Root path | Minimum of 1 octet | The path in the remote filesystem specified by siaddr or sname that the client should mount as its root filesystem (e.g, over NFS) |
| 18 | Extensions path | Minimum of 1 octet |  |
| 255 | End | 0 octets | Used to mark the end of the vendor option field |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 19 | IP forwarding enable/disable | 1 octet |  |
| 20 | Non-local source routing enable/disable | 1 octet |  |
| 21 | Policy filter | Multiples of 8 octets |  |
| 22 | Maximum datagram reassembly size | 2 octets |  |
| 23 | Default IP time-to-live | 1 octet |  |
| 24 | Path MTU aging timeout | 4 octets |  |
| 25 | Path MTU plateau table | Multiples of 2 octets |  |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 26 | Interface MTU | 2 octets |  |
| 27 | All subnets are local | 1 octet |  |
| 28 | Broadcast address | 4 octets |  |
| 29 | Perform mask discovery | 1 octet |  |
| 30 | Mask supplier | 1 octet |  |
| 31 | Perform router discovery | 1 octet |  |
| 32 | Router solicitation address | 4 octets |  |
| 33 | Static route | Multiples of 8 octets | A list of destination/router pairs |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 34 | Trailer encapsulation option | 1 octet |  |
| 35 | ARP cache timeout | 4 octets |  |
| 36 | Ethernet encapsulation | 1 octet |  |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 37 | TCP default TTL | 1 octet |  |
| 38 | TCP keepalive interval | 4 octets |  |
| 39 | TCP keepalive garbage | 1 octet |  |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 40 | Network information service domain | Minimum of 1 octet |  |
| 41 | Network information servers | Multiples of 4 octets |  |
| 42 | [Network Time Protocol](https://en.wikipedia.org/wiki/Network_Time_Protocol "Network Time Protocol") (NTP) servers | Multiples of 4 octets |  |
| 43 | Vendor-specific information | Minimum of 1 octets |  |
| 44 | NetBIOS over TCP/IP name server | Multiples of 4 octets |  |
| 45 | NetBIOS over TCP/IP datagram Distribution Server | Multiples of 4 octets |  |
| 46 | NetBIOS over TCP/IP node type | 1 octet |  |
| 47 | NetBIOS over TCP/IP scope | Minimum of 1 octet |  |
| 48 | [X Window System](https://en.wikipedia.org/wiki/X_Window_System "X Window System") font server | Multiples of 4 octets |  |
| 49 | X Window System display manager | Multiples of 4 octets |  |
| 64 | [Network Information Service](https://en.wikipedia.org/wiki/Network_Information_Service "Network Information Service") + domain | Minimum of 1 octet |  |
| 65 | Network Information Service+ servers | Multiples of 4 octets |  |
| 68 | Mobile IP home agent | Multiples of 4 octets |  |
| 69 | [Simple Mail Transfer Protocol](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol "Simple Mail Transfer Protocol") (SMTP) server | Multiples of 4 octets |  |
| 70 | [Post Office Protocol](https://en.wikipedia.org/wiki/Post_Office_Protocol "Post Office Protocol") (POP3) server | Multiples of 4 octets |  |
| 71 | [Network News Transfer Protocol](https://en.wikipedia.org/wiki/Network_News_Transfer_Protocol "Network News Transfer Protocol") (NNTP) server | Multiples of 4 octets |  |
| 72 | Default [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web") (WWW) server | Multiples of 4 octets |  |
| 73 | Default [Finger protocol](https://en.wikipedia.org/wiki/Finger_protocol "Finger protocol") server | Multiples of 4 octets |  |
| 74 | Default [Internet Relay Chat](https://en.wikipedia.org/wiki/Internet_Relay_Chat "Internet Relay Chat") (IRC) server | Multiples of 4 octets |  |
| 75 | [StreetTalk](https://en.wikipedia.org/wiki/StreetTalk "StreetTalk") server | Multiples of 4 octets |  |
| 76 | StreetTalk Directory Assistance (STDA) server | Multiples of 4 octets |  |

| Code | Name | Length | Notes |
| --- | --- | --- | --- |
| 50 | Requested IP address | 4 octets |  |
| 51 | IP address lease time | 4 octets |  |
| 52 | Option overload | 1 octet |  |
| 53 | DHCP message type | 1 octet |  |
| 54 | Server identifier | 4 octets |  |
| 55 | Parameter request list | Minimum of 1 octet |  |
| 56 | Message | Minimum of 1 octet |  |
| 57 | Maximum DHCP message size | 2 octets |  |
| 58 | Renewal (T1) time value | 4 octets |  |
| 59 | Rebinding (T2) time value | 4 octets |  |
| 60 | Vendor class identifier | Minimum of 1 octet |  |
| 61 | Client identifier | Minimum of 2 octets |  |
| 66 | TFTP server name | Minimum of 1 octet |  |
| 67 | Bootfile name | Minimum of 1 octet |  |

### DHCP message types

This table lists the DHCP message types. These codes are the value in the DHCP extension 53, shown in the table above.

| Code | Name | Length | RFC |
| --- | --- | --- | --- |
| 1 | DHCPDISCOVER | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) [^16]<sup><span title="Location: §9.6">: §9.6</span></sup> |
| 2 | DHCPOFFER | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 3 | DHCPREQUEST | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 4 | DHCPDECLINE | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 5 | DHCPACK | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 6 | DHCPNAK | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 7 | DHCPRELEASE | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 8 | DHCPINFORM | 1 octet | [2132](https://www.rfc-editor.org/rfc/rfc2132) |
| 9 | DHCPFORCERENEW | 1 octet | [3203](https://www.rfc-editor.org/rfc/rfc3203) [^18]<sup><span title="Location: §4">: §4</span></sup> |
| 10 | DHCPLEASEQUERY | 1 octet | [4388](https://www.rfc-editor.org/rfc/rfc4388) [^19]<sup><span title="Location: §6.1">: §6.1</span></sup> |
| 11 | DHCPLEASEUNASSIGNED | 1 octet | [4388](https://www.rfc-editor.org/rfc/rfc4388) |
| 12 | DHCPLEASEUNKNOWN | 1 octet | [4388](https://www.rfc-editor.org/rfc/rfc4388) |
| 13 | DHCPLEASEACTIVE | 1 octet | [4388](https://www.rfc-editor.org/rfc/rfc4388) |
| 14 | DHCPBULKLEASEQUERY | 1 octet | [6926](https://www.rfc-editor.org/rfc/rfc6926) [^20]<sup><span title="Location: §6.2.1">: §6.2.1</span></sup> |
| 15 | DHCPLEASEQUERYDONE | 1 octet | [6926](https://www.rfc-editor.org/rfc/rfc6926) |
| 16 | DHCPACTIVELEASEQUERY | 1 octet | [7724](https://www.rfc-editor.org/rfc/rfc7724) [^21]<sup><span title="Location: §5.2.1">: §5.2.1</span></sup> |
| 17 | DHCPLEASEQUERYSTATUS | 1 octet | [7724](https://www.rfc-editor.org/rfc/rfc7724) |
| 18 | DHCPTLS | 1 octet | [7724](https://www.rfc-editor.org/rfc/rfc7724) |

#### Client vendor identification

An option exists to identify the vendor and functionality of a DHCP client. The information is a [variable-length string](https://en.wikipedia.org/wiki/Variable-length_code "Variable-length code") of characters or octets which has a meaning specified by the vendor of the DHCP client. One method by which a DHCP client can communicate to the server that it is using a certain type of hardware or [firmware](https://en.wikipedia.org/wiki/Firmware "Firmware") is to set a value in its DHCP requests called the Vendor Class Identifier (VCI) (Option 60).

The value to which this option is set gives the DHCP server a hint about any required extra information that this client needs in a DHCP response. Some types of [set-top boxes](https://en.wikipedia.org/wiki/Set-top_boxes "Set-top boxes") set the VCI to inform the DHCP server about the hardware type and functionality of the device. An [Aruba](https://en.wikipedia.org/wiki/Aruba_Networks "Aruba Networks") campus [wireless access point](https://en.wikipedia.org/wiki/Wireless_access_point "Wireless access point"), for example, supplies value 'ArubaAP' as option 60 in its DHCPDISCOVER message.[^22] The DHCP server can then augment its DHCPOFFER with an IP address of an Aruba [wireless controller](https://en.wikipedia.org/wiki/Wireless_controller "Wireless controller") in option 43, so the access point knows where to register itself.

Setting a VCI by the client allows a DHCP server to differentiate between client machines and process the requests from them appropriately.

### Other extensions

| Code | Name | Length | RFC |
| --- | --- | --- | --- |
| 77 | User Class | Minimum of 2 octets | [3004](https://www.rfc-editor.org/rfc/rfc3004) [^23] |
| 82 | [Relay agent information](#Relay_agent_information_sub-options) | Minimum of 2 octets | [3046](https://www.rfc-editor.org/rfc/rfc3046) [^24] |
| 85 | [Novell Directory Service](https://en.wikipedia.org/wiki/Novell_Directory_Service "Novell Directory Service") (NDS) servers | Minimum of 4 octets, multiple of 4 octets | [2241](https://www.rfc-editor.org/rfc/rfc2241) [^25]<sup><span title="Location: §2">: §2</span></sup> |
| 86 | NDS tree name | Variable | [2241](https://www.rfc-editor.org/rfc/rfc2241) [^25]<sup><span title="Location: §3">: §3</span></sup> |
| 87 | NDS context | Variable | [2241](https://www.rfc-editor.org/rfc/rfc2241) [^25]<sup><span title="Location: §4">: §4</span></sup> |
| 100 | [Time zone](https://en.wikipedia.org/wiki/Time_zone "Time zone"), POSIX style | Variable | [4833](https://www.rfc-editor.org/rfc/rfc4833) [^26] |
| 101 | [Time zone](https://en.wikipedia.org/wiki/Time_zone "Time zone"), [tz database](https://en.wikipedia.org/wiki/Tz_database "Tz database") style | Variable | [4833](https://www.rfc-editor.org/rfc/rfc4833) |
| 114 | DHCP [Captive Portal](https://en.wikipedia.org/wiki/Captive_Portal "Captive Portal") | Variable | [8910](https://www.rfc-editor.org/rfc/rfc8910) [^27] |
| 119 | [Domain search](https://en.wikipedia.org/wiki/Search_domain "Search domain") | Variable | [3397](https://www.rfc-editor.org/rfc/rfc3397) [^28] |
| 121 | Classless static route | Variable | [3442](https://www.rfc-editor.org/rfc/rfc3442) [^29] |
| 209 | Configuration File | Variable | [5071](https://www.rfc-editor.org/rfc/rfc5071) [^30] |
| 210 | Path Prefix | Variable | [5071](https://www.rfc-editor.org/rfc/rfc5071) |
| 211 | Reboot Time | Variable | [5071](https://www.rfc-editor.org/rfc/rfc5071) |
| 224–254 | site-specific options | Variable | [3942](https://www.rfc-editor.org/rfc/rfc3942) |

#### Relay agent information sub-options

The relay agent information option (option 82) specifies container for attaching sub-options to DHCP requests transmitted between a DHCP relay and a DHCP server.[^31]

| Code | Name | Length | RFC |
| --- | --- | --- | --- |
| 1 | Agent Circuit ID | Minimum of 1 octet | [3046](https://www.rfc-editor.org/rfc/rfc3046) [^24] |
| 2 | Agent Remote ID | Minimum of 1 octet | [3046](https://www.rfc-editor.org/rfc/rfc3046) |
| 4 | Data-Over-Cable Service Interface Specifications (DOCSIS) device class | 4 octets | [3256](https://www.rfc-editor.org/rfc/rfc3256) [^32] |
| 5 | Link Selection | 4 octets | [3527](https://www.rfc-editor.org/rfc/rfc3527) [^33] |

## Relaying

In small networks, where only one IP subnet is being managed, DHCP clients communicate directly with DHCP servers. However, DHCP servers can also provide IP addresses for multiple subnets. In this case, a DHCP client that has not yet acquired an IP address cannot communicate directly with a DHCP server not on the same subnet, as the client's broadcast can only be received on its own subnet.

In order to allow DHCP clients on subnets not directly served by DHCP servers to communicate with DHCP servers, DHCP relay agents can be installed on these subnets. A DHCP relay agent runs on a network device, capable of [routing](https://en.wikipedia.org/wiki/Routing "Routing") between the client's subnet and the subnet of the DHCP server. The DHCP client broadcasts on the local link; the relay agent receives the broadcast and transmits it to one or more DHCP servers using [unicast](https://en.wikipedia.org/wiki/Unicast "Unicast"). The IP addresses of the DHCP servers are manually configured in the relay agent. The relay agent stores its own IP address, from the interface on which it has received the client's broadcast, in the *GIADDR* field of the DHCP packet. The DHCP server uses the GIADDR-value to determine the subnet, and subsequently the corresponding address pool, from which to allocate an IP address. When the DHCP server replies to the client, it sends the reply to the GIADDR-address, again using unicast. The relay agent then retransmits the response on the local network, using unicast (in most cases) to the newly reserved IP address, in an [Ethernet frame](https://en.wikipedia.org/wiki/Ethernet_frame "Ethernet frame") directed to the client's MAC address. The client should accept the packet as its own, even when that IP address is not yet set on the interface.[^4]<sup><span title="Page: 25">: 25</span> </sup> Directly after processing the packet, the client sets the IP address on its interface and is ready for regular IP communication, directly thereafter.

If the client's implementation of the IP stack does not accept unicast packets when it has no IP address yet, the client may set the *broadcast* bit in the FLAGS field when sending a DHCPDISCOVER packet. The relay agent will use the *255.255.255.255* broadcast IP address (and the clients MAC address) to inform the client of the server's DHCPOFFER.

The communication between the relay agent and the DHCP server typically uses both a source and destination UDP port of 67.

## Client states

![[250px-Dhcp-client-state-diagram.svg.png]]

A simplified DHCP client state-transition diagram based on figure 5 of RFC 2131

A DHCP client can receive these messages from a server:[^4]<sup><span title="Location: §4.4">: §4.4</span></sup>

- DHCPOFFER
- DHCPACK
- DHCPNAK

The client moves through DHCP states depending on how the server responds to the messages that the client sends.

## Reliability

The DHCP ensures reliability in several ways: periodic renewal, rebinding,[^4]<sup><span title="Location: §4.4.5">: §4.4.5</span> </sup> and failover. DHCP clients are allocated leases that last for some period of time. Clients begin to attempt to renew their leases once half the lease interval has expired.[^4]<sup><span title="Location: §4.4.5 Paragraph 3">: §4.4.5 Paragraph 3</span> </sup> They do this by sending a unicast *DHCPREQUEST* message to the DHCP server that granted the original lease. If that server is down or unreachable, it will fail to respond to the *DHCPREQUEST*. However, in that case the client repeats the *DHCPREQUEST* from time to time,[^4]<sup><span title="Location: §4.4.5 Paragraph 8">: §4.4.5 Paragraph 8</span> </sup> [^2] so if the DHCP server comes back up or becomes reachable again, the DHCP client will succeed in contacting it and renew the lease.

If the DHCP server is unreachable for an extended period of time,[^4]<sup><span title="Location: §4.4.5 Paragraph 5">: §4.4.5 Paragraph 5</span> </sup> the DHCP client will attempt to rebind, by broadcasting its *DHCPREQUEST* rather than unicasting it. Because it is [broadcast](https://en.wikipedia.org/wiki/Broadcasting_\(networking\) "Broadcasting (networking)"), the *DHCPREQUEST* message will reach all available DHCP servers. If some other DHCP server is able to renew the lease, it will do so at this time.

In order for rebinding to work, when the client successfully contacts a backup DHCP server, that server must have accurate information about the client's binding. Maintaining accurate binding information between two servers is a complicated problem; if both servers are able to update the same lease database, there must be a mechanism to avoid conflicts between updates on the independent servers. A proposal for implementing [fault-tolerant](https://en.wikipedia.org/wiki/Fault-tolerant "Fault-tolerant") DHCP servers was submitted to the Internet Engineering Task Force, but never formalized.[^34] [^3]

If rebinding fails, the lease will eventually expire. When the lease expires, the client must stop using the IP address granted to it in its lease.[^4]<sup><span title="Location: §4.4.5 Paragraph 9">: §4.4.5 Paragraph 9</span> </sup> At that time it will restart the DHCP process from the beginning by broadcasting a `DHCPDISCOVER` message. Since its lease has expired, it will accept any IP address offered to it. Once it has a new IP address (presumably from a different DHCP server) it will once again be able to use the network. However, since its IP address has changed, any ongoing connections will be broken.

## IPv6 networks

The basic methodology of DHCP was developed for networks based on [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") (IPv4). Since the development and deployment of [IPv6](https://en.wikipedia.org/wiki/IPv6 "IPv6") networks, DHCP has also been used for assigning parameters in such networks, despite the inherent features of IPv6 for [stateless address autoconfiguration](https://en.wikipedia.org/wiki/Stateless_address_autoconfiguration "Stateless address autoconfiguration"). The IPv6 version of the protocol is designated as [DHCPv6](https://en.wikipedia.org/wiki/DHCPv6 "DHCPv6").[^35]

## Security

The base DHCP does not include any mechanism for authentication.[^24]<sup><span title="Location: §7">: §7</span> </sup> Because of this, it is vulnerable to a variety of attacks. These attacks fall into three main categories:[^4]<sup><span title="Page / location: sec. 7">: sec. 7</span></sup>

- Unauthorized DHCP servers providing false information to clients.
- Unauthorized clients gaining access to resources.
- Resource exhaustion attacks from malicious DHCP clients.

Because the client has no way to validate the identity of a DHCP server, unauthorized DHCP servers (commonly called " [rogue DHCP](https://en.wikipedia.org/wiki/Rogue_DHCP "Rogue DHCP") ") can be operated on networks, providing incorrect information to DHCP clients.[^36] This can serve either as a [denial-of-service attack](https://en.wikipedia.org/wiki/Denial-of-service_attack "Denial-of-service attack"), preventing the client from gaining access to network connectivity,[^37] or as a [man-in-the-middle attack](https://en.wikipedia.org/wiki/Man-in-the-middle_attack "Man-in-the-middle attack").[^38] Because the DHCP server provides the DHCP client with server IP addresses, such as the IP address of one or more DNS servers,[^4]<sup><span title="Page / location: sec. 7">: sec. 7</span> </sup> an attacker can convince a DHCP client to do its DNS lookups through its own DNS server, and can therefore provide its own answers to DNS queries from the client.[^39] This in turn allows the attacker to redirect network traffic through itself, allowing it to eavesdrop on connections between the client and network servers it contacts, or to simply replace those network servers with its own.[^39]

Because the DHCP server has no secure mechanism for authenticating the client, clients can gain unauthorized access to IP addresses by presenting credentials, such as client identifiers, that belong to other DHCP clients.[^36] This also allows DHCP clients to exhaust the DHCP server's store of IP addresses—by presenting new credentials each time it asks for an address, the client can consume all the available IP addresses on a particular network link, preventing other DHCP clients from getting service.[^36]

DHCP does provide some mechanisms for mitigating these problems. The [Relay Agent Information Option](#Relay_agent_information_sub-options) protocol extension [^24] (usually referred to in the industry by its actual number as *Option 82* [^40] [^41]) allows network operators to attach tags to DHCP messages as these messages arrive on the network operator's trusted network. This tag is then used as an authorization token to control the client's access to network resources. Because the client has no access to the network upstream of the relay agent, the lack of authentication does not prevent the DHCP server operator from relying on the authorization token.[^24]<sup><span title="Page / location: sec. 7">: sec. 7</span></sup>

Another extension, Authentication for DHCP Messages [^42] (RFC 3118), provides a mechanism for authenticating DHCP messages. As of 2002, this extension had not seen widespread adoption because of the problems of managing keys for large numbers of DHCP clients.[^43] A 2007 book about DSL technologies remarked that:

> \[T\]here were numerous security vulnerabilities identified against the security measures proposed by RFC 3118. This fact, combined with the introduction of [802.1X](https://en.wikipedia.org/wiki/802.1X "802.1X"), slowed the deployment and take-rate of authenticated DHCP, and it has never been widely deployed.[^44]

A 2010 book notes that:

> \[T\]here have been very few implementations of DHCP Authentication. The challenges of key management and processing delays due to hash computation have been deemed too heavy a price to pay for the perceived benefits.[^45]

Architectural proposals from 2008 involve authenticating DHCP requests using [802.1X](https://en.wikipedia.org/wiki/802.1X "802.1X") or [PANA](https://en.wikipedia.org/wiki/Protocol_for_Carrying_Authentication_for_Network_Access "Protocol for Carrying Authentication for Network Access") (both of which transport [EAP](https://en.wikipedia.org/wiki/Extensible_Authentication_Protocol "Extensible Authentication Protocol")).[^46] An IETF proposal was made for including EAP in DHCP itself, the so-called EAPoDHCP;[^47] this does not appear to have progressed beyond IETF draft level, the last of which dates to 2010.[^48]

## IETF standards documents

- RFC [2131](https://www.rfc-editor.org/rfc/rfc2131)  – " Dynamic Host Configuration Protocol," [^4] *Draft Standard.*
- RFC [2132](https://www.rfc-editor.org/rfc/rfc2132)  – " DHCP Options and BOOTP Vendor Extensions," [^16] *Draft Standard.*
- RFC [3046](https://www.rfc-editor.org/rfc/rfc3046)  – " DHCP Relay Agent Information Option," [^24] *Proposed Standard.*
- RFC [3203](https://www.rfc-editor.org/rfc/rfc3203)  – " DHCP reconfigure extension," [^18] *Proposed Standard.*
- RFC [3397](https://www.rfc-editor.org/rfc/rfc3397)  – " Dynamic Host Configuration Protocol (DHCP) Domain Search Option," [^28] *Proposed Standard.*
- RFC [3442](https://www.rfc-editor.org/rfc/rfc3442)  – " The Classless Static Route Option for Dynamic Host Configuration Protocol (DHCP) version 4," [^29] *Proposed Standard.*
- RFC [3942](https://www.rfc-editor.org/rfc/rfc3942)  – " Reclassifying Dynamic Host Configuration Protocol version 4 (DHCPv4) Options," [^49] *Proposed Standard.*
- RFC [4361](https://www.rfc-editor.org/rfc/rfc4361)  – " Node-specific Client Identifiers for Dynamic Host Configuration Protocol Version Four (DHCPv4)," [^50] *Proposed Standard.*
- RFC [4388](https://www.rfc-editor.org/rfc/rfc4388)  – " Dynamic Host Configuration Protocol (DHCP) Leasequery," [^19] *Proposed Standard.*
- RFC [4436](https://www.rfc-editor.org/rfc/rfc4436)  – " Detecting Network Attachment in IPv4 (DNAv4)," [^51] *Proposed Standard.*
- RFC [6926](https://www.rfc-editor.org/rfc/rfc6926)  – " DHCPv4 Bulk Leasequery," [^20] *Proposed Standard.*
- RFC [7724](https://www.rfc-editor.org/rfc/rfc7724)  – " Active DHCPv4 Lease Query," [^21] *Proposed Standard.*
- RFC [8415](https://www.rfc-editor.org/rfc/rfc8415)  – " Dynamic Host Configuration Protocol for IPv6 (DHCPv6)," [^12] *Proposed Standard.*

[^1]: As an optional client behavior, some broadcasts, such as those carrying DHCP discovery and request messages, may be replaced with unicasts in case the DHCP client already knows the DHCP server's IP address.[^4]

[^2]: The RFC calls for the client to wait one half of the remaining time until T2 before it retransmits the *DHCPREQUEST* packet

[^3]: The proposal provided a mechanism whereby two servers could remain loosely in sync with each other in such a way that even in the event of a total failure of one server, the other server could recover the lease database and continue operating. Due to the length and complexity of the specification, it was never published as a standard; however, the techniques described in the proposal are in wide use, with open-source and several commercial implementations.

[^4]: R. Droms (March 1997). [*Dynamic Host Configuration Protocol*](https://www.rfc-editor.org/rfc/rfc2131). [IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force") Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC2131](https://doi.org/10.17487%2FRFC2131). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [2131](https://datatracker.ietf.org/doc/html/rfc2131). *Draft Standard.* Obsoletes RFC [1541](https://www.rfc-editor.org/rfc/rfc1541). Updated by RFC [3396](https://www.rfc-editor.org/rfc/rfc3396), [4361](https://www.rfc-editor.org/rfc/rfc4361), [5494](https://www.rfc-editor.org/rfc/rfc5494) and [6842](https://www.rfc-editor.org/rfc/rfc6842)

[^5]: Peterson, Larry L.; Davie, Bruce S. (2011). [*Computer Networks: A Systems Approach*](https://books.google.com/books?id=BvaFreun1W8C&pg=PA372) (5th ed.). Elsevier. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-12-385060-7](https://en.wikipedia.org/wiki/Special:BookSources/978-0-12-385060-7 "Special:BookSources/978-0-12-385060-7"). Retrieved March 21, 2019.

[^6]: R. Finlayson; T. Mann; J. Mogul; M. Theimer (June 1984). [*A Reverse Address Resolution Protocol*](https://www.rfc-editor.org/rfc/rfc903). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC0903](https://doi.org/10.17487%2FRFC0903). STD 38. [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [903](https://datatracker.ietf.org/doc/html/rfc903). *Internet Standard 38.*

[^7]: Bill Croft; John Gilmore (September 1985). [*BOOTSTRAP PROTOCOL (BOOTP)*](https://www.rfc-editor.org/rfc/rfc951). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC0951](https://doi.org/10.17487%2FRFC0951). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [951](https://datatracker.ietf.org/doc/html/rfc951). *Draft Standard.* Updated by RFC [1395](https://www.rfc-editor.org/rfc/rfc1395), [1497](https://www.rfc-editor.org/rfc/rfc1497), [1532](https://www.rfc-editor.org/rfc/rfc1532), [1542](https://www.rfc-editor.org/rfc/rfc1542) and [5494](https://www.rfc-editor.org/rfc/rfc5494)

[^8]: R. Droms (October 1993). [*Dynamic Host Configuration Protocol*](https://www.rfc-editor.org/rfc/rfc1531). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC1531](https://doi.org/10.17487%2FRFC1531). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [1531](https://datatracker.ietf.org/doc/html/rfc1531). *Obsolete.* Obsoleted by RFC [1541](https://www.rfc-editor.org/rfc/rfc1541), due to errors in the editorial process.

[^9]: R. Droms (October 1993). [*Dynamic Host Configuration Protocol*](https://www.rfc-editor.org/rfc/rfc1541). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC1541](https://doi.org/10.17487%2FRFC1541). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [1541](https://datatracker.ietf.org/doc/html/rfc1541). *Obsolete.* Obsoleted by RFC [2131](https://www.rfc-editor.org/rfc/rfc2131). Obsoletes RFC [1531](https://www.rfc-editor.org/rfc/rfc1531)

[^10]: Network+ Certification 2006 Published By Microsoft Press.

[^11]: J. Bound; B. Volz; T. Lemon; C. Perkins; M. Carney (July 2002). R. Droms (ed.). [*Dynamic Host Configuration Protocol for IPv6 (DHCPv6)*](https://www.rfc-editor.org/rfc/rfc3315). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3315](https://doi.org/10.17487%2FRFC3315). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3315](https://datatracker.ietf.org/doc/html/rfc3315). *Obsolete.* Obsoleted by [RFC](https://en.wikipedia.org/wiki/RFC_\(identifier\) "RFC (identifier)") [8415](https://www.rfc-editor.org/rfc/rfc8415). Updated by RFC [4361](https://www.rfc-editor.org/rfc/rfc4361), [5494](https://www.rfc-editor.org/rfc/rfc5494), [6221](https://www.rfc-editor.org/rfc/rfc6221), [6422](https://www.rfc-editor.org/rfc/rfc6422), [6644](https://www.rfc-editor.org/rfc/rfc6644), [7083](https://www.rfc-editor.org/rfc/rfc7083), [7283](https://www.rfc-editor.org/rfc/rfc7283), [7227](https://www.rfc-editor.org/rfc/rfc7227) and [7550](https://www.rfc-editor.org/rfc/rfc7550)

[^12]: T. Mrugalski; M. Siodelski; B. Volz; A. Yourtchenko; M. Richardson; S. Jiang; T. Lemon; T. Winters (November 2018). [*Dynamic Host Configuration Protocol for IPv6 (DHCPv6)*](https://www.rfc-editor.org/rfc/rfc8415). [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force"). [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC8415](https://doi.org/10.17487%2FRFC8415). [ISSN](https://en.wikipedia.org/wiki/ISSN_\(identifier\) "ISSN (identifier)") [2070-1721](https://search.worldcat.org/issn/2070-1721). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [8415](https://datatracker.ietf.org/doc/html/rfc8415). *Proposed Standard.* Obsoletes RFC [3315](https://www.rfc-editor.org/rfc/rfc3315), [3633](https://www.rfc-editor.org/rfc/rfc3633), [3736](https://www.rfc-editor.org/rfc/rfc3736), [4242](https://www.rfc-editor.org/rfc/rfc4242), [7083](https://www.rfc-editor.org/rfc/rfc7083), [7283](https://www.rfc-editor.org/rfc/rfc7283) and [7550](https://www.rfc-editor.org/rfc/rfc7550)

[^13]: ["DHCP - Dynamic Host Configuration Protocol"](https://routeripnet.com/dhcp/).

[^14]: Droms, Ralph; Lemon, Ted (2003). *The DHCP Handbook*. [SAMS Publishing](https://en.wikipedia.org/wiki/SAMS_Publishing "SAMS Publishing"). p. 436. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-672-32327-0](https://en.wikipedia.org/wiki/Special:BookSources/978-0-672-32327-0 "Special:BookSources/978-0-672-32327-0").

[^15]: ["Dynamic Host Configuration Protocol (DHCP) and Bootstrap Protocol (BOOTP) Parameters"](https://www.iana.org/assignments/bootp-dhcp-parameters/bootp-dhcp-parameters.xhtml). iana.org. Retrieved 2018-10-16.

[^16]: S. Alexander; R. Droms (March 1997). [*DHCP Options and BOOTP Vendor Extensions*](https://www.rfc-editor.org/rfc/rfc2132). [IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force") Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC2132](https://doi.org/10.17487%2FRFC2132). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [2132](https://datatracker.ietf.org/doc/html/rfc2132). *Draft Standard.* Obsoletes RFC [1533](https://www.rfc-editor.org/rfc/rfc1533). Updated by RFC [3442](https://www.rfc-editor.org/rfc/rfc3442), [3942](https://www.rfc-editor.org/rfc/rfc3942), [4361](https://www.rfc-editor.org/rfc/rfc4361), [4833](https://www.rfc-editor.org/rfc/rfc4833) and [5494](https://www.rfc-editor.org/rfc/rfc5494)

[^17]: Droms, Ralph; Lemon, Ted (2003). *The DHCP handbook* (2nd ed.). Indianapolis, Indiana: Sams (published October 2002). p. 134. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-672-32327-0](https://en.wikipedia.org/wiki/Special:BookSources/978-0-672-32327-0 "Special:BookSources/978-0-672-32327-0").

[^18]: Y. T'Joens; C. Hublet; P. De Schrijver (December 2001). [*DHCP reconfigure extension*](https://www.rfc-editor.org/rfc/rfc3203). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3203](https://doi.org/10.17487%2FRFC3203). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3203](https://datatracker.ietf.org/doc/html/rfc3203). *Proposed Standard.* Updated by RFC [6704](https://www.rfc-editor.org/rfc/rfc6704)

[^19]: R. Woundy; K. Kinnear (February 2006). [*Dynamic Host Configuration Protocol (DHCP) Leasequery*](https://www.rfc-editor.org/rfc/rfc4388). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC4388](https://doi.org/10.17487%2FRFC4388). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [4388](https://datatracker.ietf.org/doc/html/rfc4388). *Proposed Standard.* Updated by RFC [6148](https://www.rfc-editor.org/rfc/rfc6148)

[^20]: K. Kinnear; M. Stapp; R. Desetti; B. Joshi; N. Russell; P. Kurapati; B. Volz (April 2013). [*DHCPv4 Bulk Leasequery*](https://www.rfc-editor.org/rfc/rfc6926). [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force"). [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC6926](https://doi.org/10.17487%2FRFC6926). [ISSN](https://en.wikipedia.org/wiki/ISSN_\(identifier\) "ISSN (identifier)") [2070-1721](https://search.worldcat.org/issn/2070-1721). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [6926](https://datatracker.ietf.org/doc/html/rfc6926). *Proposed Standard.* Updated by RFC [7724](https://www.rfc-editor.org/rfc/rfc7724)

[^21]: K. Kinnear; M. Stapp; B. Volz; N. Russell (December 2015). [*Active DHCPv4 Lease Query*](https://www.rfc-editor.org/rfc/rfc7724). [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force"). [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC7724](https://doi.org/10.17487%2FRFC7724). [ISSN](https://en.wikipedia.org/wiki/ISSN_\(identifier\) "ISSN (identifier)") [2070-1721](https://search.worldcat.org/issn/2070-1721). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [7724](https://datatracker.ietf.org/doc/html/rfc7724). *Proposed Standard.* Updates RFC [6926](https://www.rfc-editor.org/rfc/rfc6926)

[^22]: ["Aruba DHCP Option 60"](https://web.archive.org/web/20220417150426/http://the-ethernets.com/2020/10/aruba-dhcp-option-60/). 7 October 2020. Archived from the original on April 17, 2022.

[^23]: G. Stump; R. Droms; Y. Gu; R. Vyaghrapuri; A. Demirtjis; B. Beser; J. Privat (November 2000). [*The User Class Option for DHCP*](https://www.rfc-editor.org/rfc/rfc3004). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3004](https://doi.org/10.17487%2FRFC3004). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3004](https://datatracker.ietf.org/doc/html/rfc3004). *Proposed Standard.*

[^24]: M. Patrick (January 2001). [*DHCP Relay Agent Information Option*](https://www.rfc-editor.org/rfc/rfc3046). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3046](https://doi.org/10.17487%2FRFC3046). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3046](https://datatracker.ietf.org/doc/html/rfc3046). *Proposed Standard.* Updated by RFC [6607](https://www.rfc-editor.org/rfc/rfc6607)

[^25]: D. Provan (November 1997). [*DHCP Options for Novell Directory Services*](https://www.rfc-editor.org/rfc/rfc2241). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC2241](https://doi.org/10.17487%2FRFC2241). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [2241](https://datatracker.ietf.org/doc/html/rfc2241). *Proposed Standard.*

[^26]: E. Lear; P. Eggert (April 2007). [*Timezone Options for DHCP*](https://www.rfc-editor.org/rfc/rfc4833). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC4833](https://doi.org/10.17487%2FRFC4833). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [4833](https://datatracker.ietf.org/doc/html/rfc4833). *Proposed Standard.* Updates RFC [2132](https://www.rfc-editor.org/rfc/rfc2132)

[^27]: W. Kumari; E. Kline (September 2020). [*Captive-Portal Identification in DHCP and Router Advertisements (RAs)*](https://www.rfc-editor.org/rfc/rfc8910). [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force"). [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC8910](https://doi.org/10.17487%2FRFC8910). [ISSN](https://en.wikipedia.org/wiki/ISSN_\(identifier\) "ISSN (identifier)") [2070-1721](https://search.worldcat.org/issn/2070-1721). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [8910](https://datatracker.ietf.org/doc/html/rfc8910). *Proposed Standard.* Obsoletes RFC [7710](https://www.rfc-editor.org/rfc/rfc7710). Updates RFC [3679](https://www.rfc-editor.org/rfc/rfc3679)

[^28]: B. Aboba; [S. Cheshire](https://en.wikipedia.org/wiki/Stuart_Cheshire "Stuart Cheshire") (November 2002). [*Dynamic Host Configuration Protocol (DHCP) Domain Search Option*](https://www.rfc-editor.org/rfc/rfc3397). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3397](https://doi.org/10.17487%2FRFC3397). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3397](https://datatracker.ietf.org/doc/html/rfc3397). *Proposed Standard.*

[^29]: T. Lemon; [S. Cheshire](https://en.wikipedia.org/wiki/Stuart_Cheshire "Stuart Cheshire"); B. Volz (December 2002). [*The Classless Static Route Option for Dynamic Host Configuration Protocol (DHCP) version 4*](https://www.rfc-editor.org/rfc/rfc3442). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3442](https://doi.org/10.17487%2FRFC3442). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3442](https://datatracker.ietf.org/doc/html/rfc3442). *Proposed Standard.* Updates RFC [2132](https://www.rfc-editor.org/rfc/rfc2132)

[^30]: D. Hankins (December 2007). [*Dynamic Host Configuration Protocol Options Used by PXELINUX*](https://www.rfc-editor.org/rfc/rfc5071). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC5071](https://doi.org/10.17487%2FRFC5071). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [5071](https://datatracker.ietf.org/doc/html/rfc5071). *Informational.*

[^31]: Patrick, Michael (January 2001). ["DHCP Relay Agent Information Option"](https://tools.ietf.org/html/rfc3046). *IETF Documents*. [IETF](https://en.wikipedia.org/wiki/IETF "IETF"). [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3046](https://doi.org/10.17487%2FRFC3046). Retrieved 22 July 2017.

[^32]: D. Jones; R. Woundy (April 2002). [*The DOCSIS (Data-Over-Cable Service Interface Specifications) Device Class DHCP (Dynamic Host Configuration Protocol) Relay Agent Information Sub-option*](https://www.rfc-editor.org/rfc/rfc3256). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3256](https://doi.org/10.17487%2FRFC3256). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3256](https://datatracker.ietf.org/doc/html/rfc3256). *Proposed Standard.*

[^33]: K. Kinnear; M. Stapp; R. Johnson; J. Kumarasamy (April 2003). [*Link Selection sub-option for the Relay Agent Information Option for DHCPv4*](https://www.rfc-editor.org/rfc/rfc3527). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3527](https://doi.org/10.17487%2FRFC3527). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3527](https://datatracker.ietf.org/doc/html/rfc3527). *Proposed Standard.*

[^34]: Droms, Ralph; Kinnear, Kim; Stapp, Mark; Volz, Bernie; Gonczi, Steve; Rabil, Greg; Dooley, Michael; Kapur, Arun (March 2003). [*DHCP Failover Protocol*](https://datatracker.ietf.org/doc/html/draft-ietf-dhc-failover-12). [IETF](https://en.wikipedia.org/wiki/IETF "IETF"). I-D draft-ietf-dhc-failover-12. Retrieved May 9, 2010.

[^35]: Weinberg, Neal (2018-08-14). ["Why DHCP's days might be numbered"](https://www.networkworld.com/article/3297800/why-dhcps-days-might-be-numbered.html). *Network World*. Retrieved 2019-08-07.

[^36]: Stapko, Timothy (2011). [*Practical Embedded Security: Building Secure Resource-Constrained Systems*](https://books.google.com/books?id=Mly55VntuYMC&pg=PA39). Newnes. p. 39. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-08-055131-9](https://en.wikipedia.org/wiki/Special:BookSources/978-0-08-055131-9 "Special:BookSources/978-0-08-055131-9").

[^37]: Rountree, Derrick (2013). [*Windows 2012 Server Network Security: Securing Your Windows Network Systems and Infrastructure*](https://books.google.com/books?id=NFzou_d4MGUC&pg=SA2-PA13). Newnes. p. 22. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-59749-965-1](https://en.wikipedia.org/wiki/Special:BookSources/978-1-59749-965-1 "Special:BookSources/978-1-59749-965-1").

[^38]: Rooney, Timothy (2010). [*Introduction to IP Address Management*](https://books.google.com/books?id=QgRDxkuI1MkC&pg=PA180). John Wiley & Sons. p. 180. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-118-07380-3](https://en.wikipedia.org/wiki/Special:BookSources/978-1-118-07380-3 "Special:BookSources/978-1-118-07380-3").

[^39]: Golovanov (Kaspersky Labs), Sergey (June 2011). ["TDSS loader now got "legs""](https://web.archive.org/web/20210125194521/https://securelist.com/tdss-loader-now-got-legs/30844/). Archived from [the original](http://www.securelist.com/en/blog/208188095/TDSS_loader_now_got_legs) on 25 January 2021.

[^40]: Hens, Francisco J.; Caballero, José M. (2008). [*Triple Play: Building the converged network for IP, VoIP and IPTV*](https://books.google.com/books?id=aS1ZngveBIkC&pg=PA239). John Wiley & Sons. p. 239. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-470-75439-9](https://en.wikipedia.org/wiki/Special:BookSources/978-0-470-75439-9 "Special:BookSources/978-0-470-75439-9").

[^41]: Ramirez, David H. (2008). [*IPTV Security: Protecting High-Value Digital Contents*](https://books.google.com/books?id=70tr_hSDULwC&pg=PA55). John Wiley & Sons. p. 55. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-0-470-72719-5](https://en.wikipedia.org/wiki/Special:BookSources/978-0-470-72719-5 "Special:BookSources/978-0-470-72719-5").

[^42]: R. Droms; W. Arbaugh, eds. (June 2001). [*Authentication for DHCP Messages*](https://www.rfc-editor.org/rfc/rfc3118). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3118](https://doi.org/10.17487%2FRFC3118). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3118](https://datatracker.ietf.org/doc/html/rfc3118). *Proposed Standard.*

[^43]: Lemon, Ted (April 2002). ["Implementation of RFC 3118"](https://www.ietf.org/mail-archive/web/dhcwg/current/msg00876.html).

[^44]: Golden, Philip; Dedieu, Hervé; Jacobsen, Krista S. (2007). [*Implementation and Applications of DSL Technology*](https://books.google.com/books?id=Jjkd74jY47oC&pg=PA484). Taylor & Francis. p. 484. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-4200-1307-8](https://en.wikipedia.org/wiki/Special:BookSources/978-1-4200-1307-8 "Special:BookSources/978-1-4200-1307-8").

[^45]: Rooney, Timothy (2010). [*Introduction to IP Address Management*](https://books.google.com/books?id=QgRDxkuI1MkC&pg=PA181). John Wiley & Sons. pp. 181–182. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-118-07380-3](https://en.wikipedia.org/wiki/Special:BookSources/978-1-118-07380-3 "Special:BookSources/978-1-118-07380-3").

[^46]: Copeland, Rebecca (2008). [*Converging NGN Wireline and Mobile 3G Networks with IMS*](https://books.google.com/books?id=ruWv8RGkBGgC&pg=PA142). Taylor & Francis. pp. 142–143. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-4200-1378-8](https://en.wikipedia.org/wiki/Special:BookSources/978-1-4200-1378-8 "Special:BookSources/978-1-4200-1378-8").

[^47]: Prasad, Ramjee; Mihovska, Albena (2009). [*New Horizons in Mobile and Wireless Communications: Networks, services, and applications*](https://books.google.com/books?id=w9bEwBwd33MC&pg=PA339). Vol. 2. Artech House. p. 339. [ISBN](https://en.wikipedia.org/wiki/ISBN_\(identifier\) "ISBN (identifier)") [978-1-60783-970-5](https://en.wikipedia.org/wiki/Special:BookSources/978-1-60783-970-5 "Special:BookSources/978-1-60783-970-5").

[^48]: ["Draft-pruss-DHCP-auth-DSL-07 - EAP Authentication Extensions for the Dynamic Host Configuration Protocol for Broadband"](https://web.archive.org/web/20150403091552/http://tools.ietf.org/search/draft-pruss-dhcp-auth-dsl-07). Archived from [the original](http://tools.ietf.org/search/draft-pruss-dhcp-auth-dsl-07) on 2015-04-03. Retrieved 2013-12-12.

[^49]: B. Volz (November 2004). [*Reclassifying Dynamic Host Configuration Protocol version 4 (DHCPv4) Options*](https://www.rfc-editor.org/rfc/rfc3942). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC3942](https://doi.org/10.17487%2FRFC3942). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [3942](https://datatracker.ietf.org/doc/html/rfc3942). *Proposed Standard.* Updates RFC [2132](https://www.rfc-editor.org/rfc/rfc2132)

[^50]: T. Lemon; B. Sommerfield (February 2006). [*Node-specific Client Identifiers for Dynamic Host Configuration Protocol Version Four (DHCPv4)*](https://www.rfc-editor.org/rfc/rfc4361). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC4361](https://doi.org/10.17487%2FRFC4361). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [4361](https://datatracker.ietf.org/doc/html/rfc4361). *Proposed Standard.* Updated by RFC [5494](https://www.rfc-editor.org/rfc/rfc5494). Updates RFC [2131](https://www.rfc-editor.org/rfc/rfc2131), [3315](https://www.rfc-editor.org/rfc/rfc3315) and [2132](https://www.rfc-editor.org/rfc/rfc2132)

[^51]: B. Aboba; J. Carlson; [S. Cheshire](https://en.wikipedia.org/wiki/Stuart_Cheshire "Stuart Cheshire") (March 2006). [*Detecting Network Attachment in IPv4 (DNAv4)*](https://www.rfc-editor.org/rfc/rfc4436). Network Working Group. [doi](https://en.wikipedia.org/wiki/Doi_\(identifier\) "Doi (identifier)"):[10.17487/RFC4436](https://doi.org/10.17487%2FRFC4436). [RFC](https://en.wikipedia.org/wiki/Request_for_Comments "Request for Comments") [4436](https://datatracker.ietf.org/doc/html/rfc4436). *Proposed Standard.*