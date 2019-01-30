#Servis Yönetimi

SysV: Kernel yüklendikten sonra init başlar. Init belli scriptleri çalıştırarak sırayla sitem servislerini başlatır.

	$ chkconfig
	$ service

Systemd: Servisler paralel olarak başlatılabilir. Sadece talep edilen servisler başlatılabilir.

d: deamon (arkada çalışan)

/usr/lib/systemd/system: RPM ile gelen dosyalar

/run/systemd/system/: çalışan dosyalar 

/etc/system.d/system/: kullanıcı tanımlı

	$ systemctl

---

|SysV					| Systemd		|
|---------------------------------		|
|init0: halt (shutdown -h) 		| poweroff.target	|
|init1: single				| rescue.target		|
|init2: multi/terminal			| multiuser.target	|
|init3: multi-user with networking	| multiuser.target	| 
|init4: undefined			| 			|
|init5: X11				| graphical.target	|
|init6: reboot (shutdown -r)		| reboot.target		|

* Uzak sunucu *init1 single mod (troubleshooting modu burada başlar)* ile başlatılırsa bazı servisler çalışmayacağından bağlantı kopar.

```
$ systemctl (start-stop-status) service

$ systemctl list-units --type target

$ systemctl get-default

$ systemctl is-enabled

$ systemctl isolate poweroff.target
```

Guvenlik modeli;

chkkconfig on/off

Debian, Suse --> apparmor
RHEL --> sellinux

/etc/sysconfig/selinux: ayar dosyası (SELINUX=0 yapılırsa devre dışı)

Durum göruntüleme;

	$ getenforce

Çalışan sistemde değişiklik;

	$ setenforce [0-1]

/var/log/audit/audit.log: log dosyaları

---

/proc dizini altinda processler vardır. top, ps komutları bu dizinleri okuyarak gosterir.

####Komutlar

* **jobs:** Çalışan işlemlerin listesini verir.

* **bg:** Durdurulmuş işlemleri arkaplanda devam ettirir.

	bg [job]

* **fg:** Durdurulmuş işlemi önplanda devam ettirir.

	$ fg

En son durdurulmuş ya da arka plana atılmış işlemi devam ettirir.

**uptime:** Sistemin ne zamandır açık olduğunu ve son 1, 5 ve 15 dakikalık *system load avarages* gösterir.

* **ps:** Mevcut işlemlerin-süreçlerin raporunu verir.

	ps auxf

f: ağaç yapısı 

---

Sisteme sorun durumunda kontrol komutları;

* **top:** İşlemci durumu
(htop)

* **free:** Ram bilgileri

* **df:** Disk bilgileri

* **du:** Dosya bazında disk bilgisi

Tüm dizinlerin boyutlarını incelme;

	$ du /*

**Zombie Süreç:** Parent süreçlerin altında child süreçler bulunur. Bazı durumlarda child processler ölür ancak parent'a bu bilgi bir şekilde gidemez. Bu child sürece zombie süreç denir. Zombie süreci oldurmek için parenti oldürmek gerekir.


	$ kill

	$ kill -9

	$ killall

	$ killall -u [user]

Kullanıcı işlemleri +19'dan -20'ye (düşük öncelik > yüksek öncelik) kadar öncelik sıralaması yapabilir.

* **nice:** yeni işlem başlatarak öncelik belirler.
```
$ nice --12 large-job
```
--: ikinci -, eksiyi temsile eder. Pozitif değer için + girilmez.

* **renice:** Çalışmakta olan işlem için öncelik belirler.
```
$ renice -3 -p 1134
```
Öncelik sırasını -3 olarak değiştirir.

---

*etc/init.d* dizininde servisler bulunur.

