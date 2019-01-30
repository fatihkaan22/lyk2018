#Temel TCP/IP Bilgisi ve Ağ Yönetimi

|TCP/IP modeli - OSI referasns modeli
|-----------------------------------------------------------
|Uygulama (HTTP, HTTPS, FTP, DNS , DHCP, SSL, SSH, IRC...) 	|
|Sunum 								|
|Oturum (SMB, NFS)						|
|Ulaşım (TCP, UDP)						|
|Ağ (IPV4, IPV6, ICMP)						|
|Veri (ethernet, wifi)						|
|Donanaım (RS-232, fiber optik)					|


![model](http://fiberbit.com.tw/wp-content/uploads/2013/12/TCP-IP-model-vs-OSI-model.png)

IPv4 = 4x8 = 32

IPv6 = 8x16 = 128

1. Dış (Public) IP
2. Özel (Private) IP
3. subnet (alt ağ)
4. broadcast (yayın)


192.168.0.0 (IP ağ adresi) - 255.255.0.0 (alt ağ adresi): 16 (8: Private ip)

gateway

ARPANET

CIDR (Classles Inter-Domain Routing)

TCP (Transmission Control Protocol): Verilerin bütünlüğünü korumak temelli kullanılır. Three handsahke yöntemi ile çalışır, UDP'ye göre daha yavaş.

UDP (User Data Protocol): Veri kaybı önemsenmez, genelde tek yönlü çalışır. Oyun servisleri ve tv servisleri örnek verilebilir. Paketleri daha küçük.

![tcp](http://image.slidesharecdn.com/08-moduleinterconnectingciscorouter-100917011729-phpapp01/95/08-module-interconnecting-cisco-router-16-728.jpg?cb\x3d1284686325)

DHCP (Dynamic Host Configuration Protocol): Otomatik ip dağıtma sistemi. Sunucu ve istemci olması gerekir.

Statik (elle) IP

hosts

13 root rare server (TLD)

IP bilgisi;

	ip a (ip addr)

	route

Erişim kontrolü bilgileri;

	traceroute 

-n: IP adresleri ve host name'leri eşleştirmeye çalışmaz.

-i: interface

-T: TCP


Ağ kullanım bilgileri;

	iftop -i enp0s3

---

/etc/services

**telnet:** TCP port kontrolü (güvensiz)

no route to host: DROP

unable connect to host: REJECT

---

TCP/UDP port kontrolü: **netcat**

listening;

	nc -lu 8000

-u: udp

	nc 192.168.56.101 -u 8000

yaparak bilgi gidip gitmediği kontrol edlebilir.

firewall'u kapatmak için; 

	systemctl stop firewalld

---

İstatistik verileri (hop):

	mtr

	ethtool -i enp053

---

Ağ kartı ışığını yakıp söndürme;

	ethtool -p enp053

	netstat (nettools) -nt(u)lp | grep ssh

n: isim (numeric)

t: tcp

l: listening

p: show PID name

---

	tcpdump -i enp053

-w: deneme.pcap

-r: deneme.pcap

(wiresharck, air-crack-engine pcap dosyalarini okuyabilir)

Ağ taraması;

	nmap -sP 192.168.56.0/24

-f: 

-p:

-A: işletim sistemi bilgileri

---

Network Manager

Terminal ağ yönetim uygulaması

	nmtui

Bilgi alma;

	nmcli

