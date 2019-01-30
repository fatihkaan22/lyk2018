##DNS Teknolojisine Giriş

kamp.linux.org.tr;

tr --> org --> linux --> kamp

---

Alan adı çözümleme;

**/etc/resolv.conf:** Dns sunucu tanımları

**/etc/hosts:** Yerel adresler

**/etc/nsswtich:** Dns ve yerel adresler arasında önceliği belirler.

---

https://www.iana.org/domains/root/servers 

TTL(time to leave) : Geçerlilik süreleri, daha hızlı cevap

---

DNS kayıtları;

* A
* CNAME
* MX
* SDA
* NS
* SPF

---

Hosts dosyası test ve kontrol amaçlı yereldeki web sitesi düzenlemelerinde kullanılabilir.

---

service network restart = systemctl restart network

---

Domain bilgileri;

	whois [domain]

IP/isim dns sorgulama;

	nslookup [domain] -query (-q) a: ns(name server), mx(mail exchange), any ...
 
	dig [domain]
 
	host [domain]

isim --> IP  (forword lookup)

IP --> isim  (reverse lookup)

dns primary (8.8.8.8) - secondary (8.8.4.4):




FQDN: www.deneme.com

host: www

domain: deneme.com


