List all the devices that appear in your network, along with a model of the device (if applicable; namely for routers and switches).

Router0 2811,Switch0 2960-24TT, Switch1 2960-24TT,PC0-PC-PT, PC1 PC-PT, PC2 PC-PT,Laptop0 Laptop-PT, Server0 Server-PT, Server1 Server-PT,Server2 Server-PT 

Next to each host, note down what IP address was assigned to it.
PC0= 168.90.0.2
PC1=168.90.0.3 
Laptop0= 168.90.0.4
Server0=168.90.0.5 

Server1=210.3.14.2 
Server2=210.3.14.3
PC2=210.3.14.4


DHCP Commands used inside of Router's CLI:

Enter a configuration mode:
en 
configure terminal
Assign a IP to Router (First Switch):
interface  Fa0/0
ip add 168.90.0.1 255.255.0.0
no shutdown
exit
Assign a IP to Router (Second Switch):
interface  Fa0/1
ip add 210.3.14.1 255.255.255.0
no shutdown
exit
Configure DHCP for First Switch:
ip dhcp pool SWITCH1_POOL
network 168.90.0.0 255.255.0.0
default-router 168.90.0.1
Configure DHCP for Second Switch:
ip dhcp pool SWITCH2_POOL
network 210.3.14.0 255.255.255.0
default-router 210.3.14.1
Exclude Router IP Addressess from DHCP
ip dhcp excluded-address 168.90.0.1
ip dhcp excluded-address 210.3.14.1
