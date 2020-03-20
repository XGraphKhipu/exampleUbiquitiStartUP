# exampleUbiquitiStartUP
example how to run script at startup to Ubiquiti 

connecto to Ubiquiti thought ssh

vi /etc/system.cfg

write:

iptables.status=enabled\
iptables.1.cmd=-t mangle -A PREROUTING -d 192.168.1.0/24 -j DROP\
iptables.2.cmd=-t mangle -A PREROUTING -s 192.168.1.0/24 -j DROP\
iptables.3.cmd=-A FORWARD -s 192.168.1.0/24 -j DROP\
iptables.4.cmd=-A FORWARD -d 192.168.1.0/24 -j DROP\
iptables.5.cmd=-A INPUT -s 192.168.1.0/24 -j DROP\
iptables.6.cmd=-A INPUT -d 192.168.1.0/24 -j DROP\


cfgmtd -f /tmp/system.cfg -w

reboot
