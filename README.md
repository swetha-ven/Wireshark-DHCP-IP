# Wireshark-DHCP-IP
CMPE 148: Assignment #2

Wireshark-DHCP Lab:

In this lab, we’ll take a quick look at DHCP. Recall that DHCP is used extensively in corporate,
university and home-network wired and wireless LANs to dynamically assign IP addresses to
hosts (as well as to configure other network configuration information).
This lab is brief, as we’ll only examine the DHCP packets captured by a host. If you also have
administrative access to your DHCP server, you may want to repeat this lab after making some
configuration changes (such as the lease time). If you have a router at home, you most likely can
configure your DHCP server.
DHCP Experiment
In order to observe DHCP in action, we’ll perform several DHCP-related commands and capture
the DHCP messages exchanged as a result of executing these commands. Do the following:
1. Begin by opening the Windows Command Prompt application (or Terminal for Mac /
Linux). As shown in Figure 1, enter “ipconfig /release” for Windows (“sudo ipconfig set
<interface> BOOTP” for Mac). This command releases your current IP address, so that
your host’s IP address becomes 0.0.0.0. (Use “ifconfig” to check what is the <interface>
name)
2. Start up the Wireshark packet sniffer, as described in the introductory Wireshark lab and
begin Wireshark packet capture. Apply the filter ‘(udp.port == 67 or udp.port == 68) or
(eth.type == 0x806)’ to capture only the DHCP-related packets.
3. Now go back to the Windows Command Prompt and enter “ipconfig /renew” (“sudo
ipconfig set <interface> DHCP” for Mac). This instructs your host to obtain a network
configuration, including a new IP address. In Figure 1, the host obtains the IP address
192.168.1.108.
4. Wait until the “ipconfig /renew” (“sudo ipconfig set <interface> DHCP” for Mac) has
terminated. Then enter the same command “ipconfig /renew” again.
5. When the second “ipconfig /renew” terminates, enter the command “ipconfig/release”
(“sudo ipconfig set <interface> BOOTP” for Mac) to release the previously-allocated IP
address to your computer.
6. Finally, enter “ipconfig /renew” to again be allocated an IP address for your computer.
7. Stop Wireshark packet capture.

You should attach a screen shot of the Command Prompt window. Whenever possible, when answering a question below, 
attach the packet(s) within the trace that you used to answer the question asked. Annotate the printout to explain 
your answer. To print a CMPE 148 Wireshark Lab: DHCP packet, use File->Print, choose Selected packet only, 
choose Packet summary line, and select the minimum amount of packet detail that you need to answer the question.

Answer the following questions:
1. How do you know that a message belongs to DHCP? Is it the protocol field in IP header?
2. Draw a timing datagram illustrating the sequence of the first four-packet
Discover/Offer/Request/ACK DHCP exchange between the client and server.
3. What is the link-layer (e.g., Ethernet) address of your DHCP server?
4. What values in the DHCP discover message differentiate this message from the DHCP
request message?
5. What is the value of the Transaction-ID in each of the first four
(Discover/Offer/Request/ACK) DHCP messages? What are the values of the
Transaction-ID in the second set (Request/ACK) set of DHCP messages? What is the
purpose of the Transaction-ID field?
6. A host uses DHCP to obtain an IP address, among other things. But a host’s IP address is
not confirmed until the end of the four-message exchange! If the IP address is not set
until the end of the four-message exchange, then what values are used in the IP datagrams
in the four-message exchange? For each of the four DHCP messages
(Discover/Offer/Request/ACK DHCP), indicate the source and destination IP addresses
that are carried in the encapsulating IP datagram.
7. What is the IP address of your DHCP server? Which type of DHCP messages does it
send?
8. What IP address is the DHCP server offering to your host in the DHCP Offer message?
Indicate which DHCP message contains the offered DHCP address.
9. In the example screenshot in this assignment, there is no relay agent between the host and
the DHCP server. What values in the trace indicate the absence of a relay agent? Is there
a relay agent in your experiment? If so what is the IP address of the agent?
10. In this experiment the DHCP server is offering a specific IP address to the client (see also
question 8. above). In the client’s response to the first server OFFER message, does the
client accept this IP address? Where in the client’s RESPONSE is the client’s requested
address?
11. What other information is required apart from the client IP address for the client to start
communicating? Does the offer message include this information?
12. Where is the lease time mentioned in the communication? How long is the lease time in your
experiment?
13. What is the purpose of the DHCP release message? Does the DHCP server issue an
acknowledgment of receipt of the client’s DHCP request? What would happen if the client’s
DHCP release message is lost?
14. Were any ARP packets sent or received during the DHCP packet-exchange period? If so,
explain the purpose of those ARP packets.

Wireshark-IP Lab:


