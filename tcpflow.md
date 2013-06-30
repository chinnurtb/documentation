Dump general traffic
--------------------
sudo tcpdump -i en1 -w dump.pcap

Dump traffic localhost
----------------------
sudo tcpdump -i lo -w dump.pcap

Print TCP traffic to terminal
-----------------------------
sudo tcpflow -i lo0 -c
-i interface
-c console

### debug one host

sudo tcpflow -i en0 -c host www.host.com

Wireshark
======

Show http traffic
-----------------
http

Show only 404er
---------------
http.response.code == 404

Show only file data received over HTTP (the content of the responses)
---------------------------------------------------------------------
http.content_type


ip.dst_host == 83.169.37.123 && http
