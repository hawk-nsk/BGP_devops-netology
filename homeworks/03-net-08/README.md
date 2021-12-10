###1) Подключитесь к публичному маршрутизатору в интернет. Найдите маршрут к вашему публичному IP

Маршруты до публичного IPv6 адреса ниже. По непонятным причинам маршрутизатор не мщет bgp маршурт для IPv6 хоста и требует указание маски.
Логично , что при указании маски 128 префикса нет в таблице маршрутизации. Соответсвенно, был введен поиск маршурта для префикса /38, который провайдер анонсирует апстримам (префикс был найден на ripe.net, как route6 обьект).
	
	telnet route-views.routeviews.org
	Username: rviews

	route-views>show ipv6 route 2a02:2698:5022:85c0:9cd6:4d87:6972:5263
		Routing entry for 2A02:2698:5022::/47
		Known via "bgp 6447", distance 20, metric 0, type external
		Route count is 1/1, share count 0
			Routing paths:
			2001:470:0:1A::1
		MPLS label: nolabel
		Last updated 7w0d ago
		
	route-views>show bgp ipv6 unicast 2a02:2698:5022:85c0:9cd6:4d87:6972:5263
	% Incomplete command.
	
	route-views>    show bgp ipv6 unicast 2a02:2698:5022:85c0:9cd6:4d87:6972:5263/128
	% Network not in table	

	route-views>show bgp ipv6 unicast 2a02:2698:5000::/38
	BGP routing table entry for 2A02:2698:5000::/38, version 561455948
	Paths: (13 available, best #13, table default)
	  Not advertised to any peer
	  Refresh Epoch 1
	  101 174 1299 9049 43478
		2001:1860::223 from 2001:1860::223 (209.124.176.223)
		  Origin IGP, localpref 100, valid, external
		  Community: 101:20100 101:20110 101:22100 174:21000 174:22013
		  Extended Community: RT:101:22100
		  path 7FE188EC7F98 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  20130 6939 9049 43478
		2620:0:2250::FF0B from 2620:0:2250::FF0B (140.192.8.16)
		  Origin IGP, localpref 100, valid, external
		  path 7FE039B2D310 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  7018 1299 9049 43478
		2001:1890:111D:1::63 from 2001:1890:111D:1::63 (12.0.1.63)
		  Origin IGP, localpref 100, valid, external
		  Community: 7018:5000 7018:37232
		  path 7FE09F2FF708 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  57866 9002 9049 43478
		2A00:A7C0:E20A::17 from 2A00:A7C0:E20A::17 (37.139.139.17)
		  Origin IGP, metric 0, localpref 100, valid, external
		  Community: 9002:0 9002:64667
		  path 7FE0858536D8 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  20912 6939 9049 43478
		2001:40D0::126 from 2001:40D0::126 (212.66.96.126)
		  Origin IGP, localpref 100, valid, external
		  Community: 20912:65016
		  path 7FE0B1EB4F58 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 2
	  3303 6939 9049 43478
		2001:918:0:5::1 from 2001:918:0:5::1 (138.187.128.158)
		  Origin IGP, localpref 100, valid, external
		  Community: 3303:1006 3303:1021 3303:1030 3303:3067 6939:7040 6939:8752 6939:9002
		  path 7FE098C0E678 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  1351 174 1299 9049 43478
		2620:104:E000:1000::3 from 2620:104:E000:1000::3 (132.198.255.253)
		  Origin IGP, localpref 100, valid, external
		  path 7FE1142EB748 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 2
	  24441 6939 9049 43478
		2404:CC00:1::4 from 2404:CC00:1::1 (202.93.8.242)
		  Origin IGP, localpref 100, valid, external
		  path 7FE0361F4A50 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  49788 1299 9049 43478
		2A02:D140:1::60 from 2A02:D140:1::60 (91.218.184.60)
		  Origin IGP, localpref 100, valid, external
		  Community: 1299:30000
		  path 7FE00C62C268 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  8283 1299 9049 43478
		2A02:898:0:300::3 from 2A02:898:0:300::3 (94.142.247.3)
		  Origin IGP, metric 0, localpref 100, valid, external
		  Community: 1299:30000 8283:1 8283:101 8283:103
		  unknown transitive attribute: flag 0xE0 type 0x20 length 0x24
			value 0000 205B 0000 0000 0000 0001 0000 205B
				  0000 0005 0000 0001 0000 205B 0000 0005
				  0000 0003
		  path 7FE005A54D98 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  4901 6079 9002 9049 43478
		2620:118:5007:FFFF::FFFF from 2620:118:5007:FFFF::FFFF (162.250.137.254)
		  Origin IGP, localpref 100, valid, external
		  Community: 65000:10100 65000:10300 65000:10400
		  path 7FE046148FC8 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  701 1299 9049 43478
		2600:803::15 from 2600:803::15 (137.39.3.55)
		  Origin IGP, localpref 100, valid, external
		  Community: 701:333 701:1020
		  path 7FE04D073660 RPKI State valid
		  rx pathid: 0, tx pathid: 0
	  Refresh Epoch 1
	  6939 9049 43478
		2001:470:0:1A::1 from 2001:470:0:1A::1 (216.218.252.164)
		  Origin IGP, localpref 100, valid, external, best
		  path 7FE0284CB798 RPKI State valid
		  rx pathid: 0, tx pathid: 0x0	
			
			
			
		route-views>show bgp ipv4 unicast 94.180.96.17
		BGP routing table entry for 94.180.96.0/19, version 65712536
		Paths: (23 available, best #22, table default)
		  Not advertised to any peer
		  Refresh Epoch 1
		  53767 174 174 1299 9049 43478
			162.251.163.2 from 162.251.163.2 (162.251.162.3)
			  Origin IGP, localpref 100, valid, external
			  Community: 174:21000 174:22013 53767:5000
			  path 7FE0D303CF70 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  3549 3356 9002 9002 9002 9002 9002 9049 43478
			208.51.134.254 from 208.51.134.254 (67.16.168.191)
			  Origin IGP, metric 0, localpref 100, valid, external
			  Community: 3356:2 3356:22 3356:100 3356:123 3356:503 3356:903 3356:2067 3549:2581 3549:30840
			  path 7FE124AE22E0 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  3356 9002 9002 9002 9002 9002 9049 43478
			4.68.4.46 from 4.68.4.46 (4.69.184.201)
			  Origin IGP, metric 0, localpref 100, valid, external
			  Community: 3356:2 3356:22 3356:100 3356:123 3356:503 3356:903 3356:2067
			  path 7FE129722810 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  20130 6939 9049 43478
			140.192.8.16 from 140.192.8.16 (140.192.8.16)
			  Origin IGP, localpref 100, valid, external
			  path 7FE12745BD20 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  3333 9002 9049 43478
			193.0.0.56 from 193.0.0.56 (193.0.0.56)
			  Origin IGP, localpref 100, valid, external
			  path 7FE0AF767B40 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  852 1299 9049 43478
			154.11.12.212 from 154.11.12.212 (96.1.209.43)
			  Origin IGP, metric 0, localpref 100, valid, external
			  path 7FE10252E570 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  101 174 1299 9049 43478
			209.124.176.223 from 209.124.176.223 (209.124.176.223)
			  Origin IGP, localpref 100, valid, external
			  Community: 101:20100 101:20110 101:22100 174:21000 174:22013
			  Extended Community: RT:101:22100
			  path 7FE1714007A8 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  57866 9002 9049 43478
			37.139.139.17 from 37.139.139.17 (37.139.139.17)
			  Origin IGP, metric 0, localpref 100, valid, external
			  Community: 9002:0 9002:64667
			  path 7FE0DF330778 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  7660 2516 1299 9049 43478
			203.181.248.168 from 203.181.248.168 (203.181.248.168)
			  Origin IGP, localpref 100, valid, external
			  Community: 2516:1030 7660:9003
			  path 7FE0931B5628 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  2497 1299 9049 43478
			202.232.0.2 from 202.232.0.2 (58.138.96.254)
			  Origin IGP, localpref 100, valid, external
			  path 7FE1356760B8 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  20912 3257 1299 9049 43478
			212.66.96.126 from 212.66.96.126 (212.66.96.126)
			  Origin IGP, localpref 100, valid, external
			  Community: 3257:8101 3257:30055 3257:50001 3257:53900 3257:53902 20912:65004
			  path 7FE16645B320 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 3
		  3303 6939 9049 43478
			217.192.89.50 from 217.192.89.50 (138.187.128.158)
			  Origin IGP, localpref 100, valid, external
			  Community: 3303:1006 3303:1021 3303:1030 3303:3067 6939:7040 6939:8752 6939:9002
			  path 7FE00FECCCA8 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  4901 6079 9002 9049 43478
			162.250.137.254 from 162.250.137.254 (162.250.137.254)
			  Origin IGP, localpref 100, valid, external
			  Community: 65000:10100 65000:10300 65000:10400
			  path 7FE00B0E7238 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  7018 1299 9049 43478
			12.0.1.63 from 12.0.1.63 (12.0.1.63)
			  Origin IGP, localpref 100, valid, external
			  Community: 7018:5000 7018:37232
			  path 7FE04E8B74B0 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  49788 1299 9049 43478
			91.218.184.60 from 91.218.184.60 (91.218.184.60)
			  Origin IGP, localpref 100, valid, external
			  Community: 1299:30000
			  Extended Community: 0x43:100:1
			  path 7FE10AB0D418 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  8283 1299 9049 43478
			94.142.247.3 from 94.142.247.3 (94.142.247.3)
			  Origin IGP, metric 0, localpref 100, valid, external
			  Community: 1299:30000 8283:1 8283:101
			  unknown transitive attribute: flag 0xE0 type 0x20 length 0x18
				value 0000 205B 0000 0000 0000 0001 0000 205B
					  0000 0005 0000 0001
			  path 7FE1194100D0 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  1221 4637 9002 9049 43478
			203.62.252.83 from 203.62.252.83 (203.62.252.83)
			  Origin IGP, localpref 100, valid, external
			  path 7FE174418510 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  701 1299 9049 43478
			137.39.3.55 from 137.39.3.55 (137.39.3.55)
			  Origin IGP, localpref 100, valid, external
			  path 7FE00668F790 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  3257 1299 9049 43478
			89.149.178.10 from 89.149.178.10 (213.200.83.26)
			  Origin IGP, metric 10, localpref 100, valid, external
			  Community: 3257:8794 3257:30052 3257:50001 3257:54900 3257:54901
			  path 7FE1676F45E8 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  3561 3910 3356 9002 9002 9002 9002 9002 9049 43478
			206.24.210.80 from 206.24.210.80 (206.24.210.80)
			  Origin IGP, localpref 100, valid, external
			  path 7FE04910D610 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  1351 6939 9049 43478
			132.198.255.253 from 132.198.255.253 (132.198.255.253)
			  Origin IGP, localpref 100, valid, external
			  path 7FE0484C6B20 RPKI State not found
			  rx pathid: 0, tx pathid: 0
		  Refresh Epoch 1
		  6939 9049 43478
			64.71.137.241 from 64.71.137.241 (216.218.252.164)
			  Origin IGP, localpref 100, valid, external, best
			  path 7FE0D83D8190 RPKI State not found
			  rx pathid: 0, tx pathid: 0x0
		  Refresh Epoch 1
		  19214 174 1299 9049 43478
			208.74.64.40 from 208.74.64.40 (208.74.64.40)
			  Origin IGP, localpref 100, valid, external
			  Community: 174:21000 174:22013
			  path 7FE09FF34778 RPKI State not found
			  rx pathid: 0, tx pathid: 0
	

###2)Создайте dummy0 интерфейс в Ubuntu. Добавьте несколько статических маршрутов. Проверьте таблицу маршрутизации.

Создан интерфейс loop0 с IP 1.1.1.1/32, созданы два марршрута для подсетей 2.2.2.0/24 и 3.3.3.0/24. Список коанд ниже.


	$ cat /etc/netplan/00-installer-config.yaml
	network:
	  ethernets:
		eno1:
		  addresses:
		  - 81.149.44.69/28
		  gateway4: 81.149.44.65
		  nameservers:
			addresses:
			- 8.8.8.8
			search: []
		  routes: 
			- to:  2.2.2.0/24
			  via: 81.149.44.66
			- to:  3.3.3.0/24
			  via: 81.149.44.67
		eno2:
		  dhcp4: no
		eno3:
		  dhcp4: no
		eno4:
		  dhcp4: no
	  version: 2
	  bonds:
		bond0:
		  interfaces:
		  - eno3
		  - eno4
		  parameters:
			mode: active-backup
			primary: eno3
	  bridges:
		loop0:
		  addresses:
		  - 1.1.1.1/32


	$ ip route get 8.8.8.8
	8.8.8.8 via 81.149.44.65 dev eno1 src 83.149.49.69 uid 1000
		cache

	$ ip route get 1.1.1.1
	local 1.1.1.1 dev lo src 1.1.1.1 uid 1000
		cache <local>
		
	$ ip route get 2.2.2.2
	2.2.2.2 via 81.149.44.66 dev eno1 src 83.149.49.69 uid 1000
		cache
		
	$ netstat -rn
	Kernel IP routing table
	Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
	0.0.0.0         81.149.44.65    0.0.0.0         UG        0 0          0 eno1
	2.2.2.0         81.149.44.66    255.255.255.0   UG        0 0          0 eno1
	3.3.3.0         81.149.44.67    255.255.255.0   UG        0 0          0 eno1
	10.222.222.0    0.0.0.0         255.255.255.0   U         0 0          0 wg0
	81.149.44.64    0.0.0.0         255.255.255.240 U         0 0          0 eno1
	172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0

	$ ip route list
	default via 83.149.49.65 dev eno1 proto static
	2.2.2.0/24 via 83.149.49.66 dev eno1 proto static
	3.3.3.0/24 via 83.149.49.67 dev eno1 proto static
	10.222.222.0/24 dev wg0 proto kernel scope link src 10.222.222.1
	81.149.44.64/28 dev eno1 proto kernel scope link src 81.149.44.69
	172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown

	$ ip -br a show dev loop0
	loop0            UNKNOWN        1.1.1.1/32 fe80::c01f:90ff:fe94:6413/64


###3)Проверьте открытые TCP порты в Ubuntu, какие протоколы и приложения используют эти порты? Приведите несколько примеров.

Открыты порты 22 и 53. Это порты для доступа по SSH и DNS (systemd) соответсвенно. В первом случае порт слушает на всех интерфейсах (0.0.0.0), во втором случае только на lo интефоейсе. 

	$ ss -tnlp
	State          Recv-Q         Send-Q                 Local Address:Port                 Peer Address:Port        Process
	LISTEN         0              4096                   127.0.0.53%lo:53                        0.0.0.0:*            users:(("systemd-resolve",pid=2680293,fd=13))
	LISTEN         0              128                          0.0.0.0:22                        0.0.0.0:*            users:(("sshd",pid=189490,fd=3))
	LISTEN         0              128                             [::]:22                           [::]:*            users:(("sshd",pid=189490,fd=4))


###4)Проверьте используемые UDP сокеты в Ubuntu, какие протоколы и приложения используют эти порты?

Открытые UDP сокеты ниже. 

	dgolodnikov@goofy:/etc/netplan$ sudo ss -unap
	State          Recv-Q         Send-Q                 Local Address:Port                  Peer Address:Port        Process
	UNCONN         0              0                      127.0.0.53%lo:53                         0.0.0.0:*           users:(("systemd-resolve",pid=2680293,fd=12))
	UNCONN         0              0                            0.0.0.0:51820                      0.0.0.0:*
	UNCONN         0              0                            0.0.0.0:5353                       0.0.0.0:*            users:(("avahi-daemon",pid=122687,fd=12))
	UNCONN         0              0                            0.0.0.0:41492                      0.0.0.0:*            users:(("avahi-daemon",pid=122687,fd=14))
	UNCONN         0              0                               [::]:33333                         [::]:*            users:(("avahi-daemon",pid=122687,fd=15))
	UNCONN         0              0                               [::]:51820                         [::]:*
	UNCONN         0              0                               [::]:5353                          [::]:*            users:(("avahi-daemon",pid=122687,fd=13))


###5)Используя diagrams.net, создайте L3 диаграмму вашей домашней сети или любой другой сети, с которой вы работали.

Во вложении мнимая домашняя сеть. https://www.diagrams.net/ хороший инструмент для оперативной отрисовки схем.