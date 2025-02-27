# Wireshark-Filters 🔎
Master Network Analysis with Wireshark

Wireshark is one of the most powerful tools in the cybersecurity arsenal for network traffic analysis. Using filters effectively is the key to pinpointing specific data from the sea of network packets.

Here's a handy list of Wireshark filters that can help you:

✅ Track traffic to specific IPs or ranges 

✅ Capture TCP or UDP traffic with specific flags 

✅ Analyze DNS responses and HTTP requests

✅ Focus on ICMP, DHCP and TLS handshake packets

✅ Filter out background noise like ARP and ICMP

Master these filters, and you'll be on your way to network traffic analysis proficiency, aiding in faster troubleshooting and better cybersecurity defense!

# Top Wireshark Filters

The filtering capabilities of Wireshark are very comprehensive. You can filter on just about any field of any protocol, even down to the HEX values in a data stream. Sometimes though, the hardest part about setting a filter in Wireshark is remembering the syntax.

So below are the most common filters that I use in Wireshark. Please comment below and add any common ones that you use as well. 

1. ip.addr == 10.0.0.1 [Sets a filter for any packet with 10.0.0.1, as either the source or dest]
2. ip.addr==10.0.0.1  && ip.addr==10.0.0.2 [sets a conversation filter between the two defined IP addresses]
3. tcp.time_delta > .250 [sets a filter to display all tcp packets that have a delta time of greater than 250mSec in the context of their stream. Note, this filter requires TCP Conversation Timestamps to be calculated. To learn to do that, click here.]
4. tcp.port==4000 [sets a filter for any TCP packet with 4000 as a source or dest port]
5. tcp.flags == 0x012 [displays all TCP SYN/ACK packets - shows the connections that had a positive response. Related to this is tcp.flags.syn==1]
6. ip.addr == 10.0.0.0/24 [Shows packets to and from any address in the 10.0.0.0/24 space]
7. frame contains traffic [displays all packets that contain the word ‘traffic’. Excellent when searching on a specific string or user ID]
8. !(arp or icmp or stp) [masks out arp, icmp, stp, or whatever other protocols may be background noise. Allowing you to focus on the traffic of interest]
9. eth[0x47:2] == 01:80 [This is an example of an offset filter. It sets a filter for the HEX values of 0x01 and 0x80 specifically at the offset location of 0x47]
10. tcp.analysis.flags && !tcp.analysis.window_update [displays all retransmissions, duplicate acks, zero windows, and more in the trace. Helps when tracking down slow application performance and packet loss. It will not include the window updates, since these aren't really important for me to see in most cases.]
11. ip.src == 10.0.0.1 && ip.dst == 10.0.0.2 [Show all traffic from 10.0.0.1 to 10.0.0.2]
12. !(ip.addr == 10.0.0.1) [Exclude all traffic to or from 10.0.0.1]
13. icmp.type == 3 [Show ICMP "destination unreachable" packets]
14. tcp or udp [Show TCP or UDP traffic]
15. tcp.port == 80 [Show TCP with port 80]
16. tcp.srcport < 1000 [Show TCP traffic with src port range]
17. http or dns [Show all HTTP or DNS traffic]
18. tcp.flags.syn == 1 [Show TCP packets with SYN flag set]
19. tcp.analysis.retransmission [Show all retransmitted TCP packets]
20. http.request.method == "GET" [Show TCP packets associated with HTTP GET]
21. http.response.code == 404 [Show packets associated with HTTP 404 response]
22. http.host == "www.test.com" [Show HTTP traffic matching the Host header field]
23. tls.handshake [Show only TLS handshake packets]
24. tls.handshake.type == 1 [Show client Hello pakcet during TLS handshake]
25. dhcp and ip.addr == 10.0.0.0/24 [Show DHCP traffic for  10.0.0.0/24 subnet]
26. dhcp.hw.mac_addr==00:11:22:33:44:55 [Show DHCP packets for client MAC address]
27. dns.resp.name == cnn.com [Show DNS responses with name field of cnn.com]
28. frame contains keyword [Show all packets that contain the word "keyword"]
29. frame.len > 1000 [Show all packets with total length larger than 1000 bytes]
30. eth.addr == 00:11:22:33:44:55 [Show all traffic to or from the specific MAC address]
31. vlan.id == 100 [Show packets with VLAN ID 100]
32. frame matches traffic [matches and filters in all the packets containing the keyword "traffic"]
