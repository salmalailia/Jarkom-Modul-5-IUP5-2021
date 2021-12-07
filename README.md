# Jarkom-Modul-5-IUP5-2021


Group IUP 5 :

Hilmy Hanif Ibrahim (05111942000005)

Salma Rahma Lailia  (05111942000016)

Khairi Wiryawan     (05111942000023)


# Module 5

(A) Your first task is to create a network topology according to the design given by Luffy below:

Description : 	

Doriki is a DNS Server

Jipangu is a DHCP Server

Maingate and Jorge are Web Servers

Number of Hosts on Blueno is 100 hosts

Number of Hosts in Cipher is 700 hosts

Total Hosts on Elena is 300 hosts

The number of hosts on Fukurou is 200 hosts

![1638796866144](https://user-images.githubusercontent.com/73702347/145006303-9df4680b-7e1e-4ddf-8420-bdab5afd5e99.jpg)

(B) Since you have learned subnetting and routing, Luffy would like to ask you to create the topology using CIDR or VLSM techniques. After doing subnetting.

(C) You are also required to do routing so that every device on the network can connect.

(D) The next task is to assign ips to the Blueno, Cipher, Fukurou, and Elena subnets dynamically using the help of a DHCP server. Then you remember that you have to set DHCP Relay on the router that connects it.

![1638868914600](https://user-images.githubusercontent.com/73702347/145006315-3f3aca41-9add-469f-b4a8-9c85b82b081a.jpg)

![Modul5](https://user-images.githubusercontent.com/73702347/145011901-fa62bfbd-59c0-48e5-b085-bd92cbad38e8.jpeg)

SUBNETTING 

Water7

	auto eth0
	iface eth0 inet static
 	address 10.40.7.145
 	netmask 255.255.255.252
 	gateway 10.40.7.146

	auto eth1
	iface eth1 inet static
 	address 10.40.7.1
 	netmask 255.255.255.128

	auto eth2
	iface eth2 inet static
 	address 10.40.7.129
 	netmask 255.255.255.248

	auto eth3
	iface eth3 inet static
	address 10.40.0.1
 	netmask 255.255.252.0

Foosha

	auto eth0
	iface eth0 inet dhcp
	hwaddress ether ca:7a:3f:7a:9e:43

	auto eth1
	iface eth1 inet static
	address 10.40.7.146
 	netmask 255.255.255.252

	auto eth2
	iface eth2 inet static
	address 10.40.7.149
	netmask 255.255.255.252

Guanhao

	auto eth0
	iface eth0 inet static
 	address 10.40.7.150
 	netmask 255.255.255.252
 	gateway 10.40.7.149

	auto eth1
	iface eth1 inet static
 	address 10.40.6.1
 	netmask 255.255.255.0

	auto eth2
	iface eth2 inet static
 	address 10.40.7.137
 	netmask 255.255.255.248

	auto eth3
	iface eth3 inet static
 	address 10.40.4.1
 	netmask 255.255.254.0

Doriki
	
	auto eth0
	iface eth0 inet static
 	address 10.40.7.130
 	netmask 255.255.255.248
 	gateway 10.40.7.129

Jipangu
	
	auto eth0
	iface eth0 inet static
 	address 10.40.7.131
 	netmask 255.255.255.248
 	gateway 10.40.7.129

Jorge

	auto eth0
	iface eth0 inet static
 	address 10.40.7.138
 	netmask 255.255.255.248
 	gateway 10.40.7.137

Maingate

	auto eth0
	iface eth0 inet static
 	address 10.40.7.139
 	netmask 255.255.255.248
 	gateway 10.40.7.137

Blueno

	auto eth0
	iface eth0 inet dhcp
	hwaddress ether 5a:c1:3a:85:39:90

Cipher
	
	auto eth0
	iface eth0 inet dhcp
	hwaddress ether 6e:25:8a:e4:b5:8e

Elena
	
	auto eth0
	iface eth0 inet dhcp
	hwaddress ether 96:4a:a5:96:55:23

Fukurou
	
	auto eth0
	iface eth0 inet dhcp
	hwaddress ether 12:90:09:c6:0c:be

SUBNETTING "DHCP"

In /etc/default/isc-dhcp-server Jipangu
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/server%20jipangu.jpeg)

In /etc/dhcp/dhcpd.conf Jipangu

	subnet 10.40.7.0 netmask 255.255.255.128 {
    	range 10.40.7.2 10.40.7.126;
    	option routers 10.40.7.1;
    	option broadcast-address 10.40.7.127;
    	option domain-name-servers 10.40.7.130;
    	default-lease-time 720;
    	max-lease-time 7200;
	}

	subnet 10.40.0.0 netmask 255.255.252.0 {
    	range 10.40.0.2 10.40.3.254;
    	option routers 10.40.0.1;
    	option broadcast-address 10.40.3.255;
    	option domain-name-servers 10.40.7.130;
    	default-lease-time 720;
    	max-lease-time 7200;
	}

	host Blueno{
    	hardware ethernet 5a:c1:3a:85:39:90;
    	fixed-address 10.40.7.3;
	}

	host Cipher{
    	hardware ethernet 6e:25:8a:e4:b5:8e;
    	fixed-address 10.40.0.3;
	}

	subnet 10.40.4.0 netmask 255.255.254.0 {
    	range 10.40.4.1 10.40.5.254;
    	option routers 10.40.4.1;
    	option broadcast-address 10.40.5.255;
    	option domain-name-servers 10.40.7.130;
    	default-lease-time 720;
    	max-lease-time 7200;
	}

	subnet 10.40.6.0 netmask 255.255.255.0 {
    	range 10.40.6.1 10.40.6.254;
    	option routers 10.40.6.1;
    	option broadcast-address 10.40.6.255;
    	option domain-name-servers 10.40.7.130;
    	default-lease-time 720;
    	max-lease-time 7200;
	}

	host Elena{
    	hardware ethernet 96:4a:a5:96:55:23;
    	fixed-address 10.40.4.2;
	}

	host Fukurou{
    	hardware ethernet 12:90:09:c6:0c:be;
    	fixed-address 10.40.6.2;
	}

Routing from Jipangu to router Water7

	subnet 10.40.7.128 netmask 255.255.255.248 {
        	option routers 10.40.7.129;
	}

Routing from Jipangu to router Guanhao
	
	subnet 10.40.7.136 netmask 255.255.255.248 {
        	option routers 10.40.7.137;
	}

Routing from Jipangu to router Foosha

	subnet 10.40.7.144 netmask 255.255.255.252 {
        	option routers 10.40.7.146;
	}

Routing from Foosha to Guanhao

	subnet 10.40.7.148 netmask 255.255.255.252 {
        	option routers 10.40.7.149;
	}
	
	host FOOSHA {
    	hardware ethernet ca:7a:3f:7a:9e:43;
    	fixed-address 192.168.122.98;
	}

/etc/default/isc-dhcp-server
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/dhcp1.jpeg)
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/dhcp2.jpeg)
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/dhcp3.jpeg)
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/dhcp4.jpeg)

routing @ Foosha
#left side
	
	route add -net 10.40.7.0 netmask 255.255.255.128 gw 10.40.7.145
	route add -net 10.40.7.128 netmask 255.255.255.248 gw 10.40.7.145
	route add -net 10.40.0.0 netmask 255.255.252.0 gw 10.40.7.145

#right side

	route add -net 10.40.6.0 netmask 255.255.255.0 gw 10.40.7.150
	route add -net 10.40.7.136 netmask 255.255.255.248 gw 10.40.7.150
	route add -net 10.40.4.0 netmask 255.255.254.0 gw 10.40.7.150

routing @ Water7

	route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.40.7.146

routing @ Guanhao

	route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.40.7.149

DHCP

/isc-dhcp-relay @ Water7, Foosha, & Guanhao
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/relay%20water7.jpeg)
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/relay%20foosha.jpeg)
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/relay%20guanhao.jpeg)

No 1. In order for your topology to be able to access outside, you are required to configure Foosha using iptables, but Luffy doesn't want to use MASQUERADE.
Answer :

	iptables -t nat -A POSTROUTING -s 10.40.0.0/21 -o eth0 -j SNAT --to-source 192.168.122.127

Test :
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/SS%20%231.jpeg)

No 4. Access from the Blueno and Cipher subnets is only allowed from 07.00 - 15.00 Monday to Thursday.
Answer :

	iptables -A INPUT -s 10.40.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
	iptables -A INPUT -s 10.40.7.0/25 -j REJECT

	iptables -A INPUT -s 10.40.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
	iptables -A INPUT -s 10.40.0.0/22 -j REJECT

Test :
![alt text](https://github.com/salmalailia/Jarkom-Modul-5-IUP5-2021/blob/main/SS%205/ss%20%234.jpeg)
