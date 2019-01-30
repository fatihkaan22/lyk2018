#ssh (Secure Shell)

OpenSSH

port:22

-x: x11 (grafik bağlantı)

	ssh kullanici_adi@sunucu

karşıda komut çalıştırma;

	ssh kullanici_adi@sunucu "komut"

-p: 22 (default port) nin dışında port vermek için

-v: verbose

---

**genel ayarlar:** /etc/ssh/

**kullanıcı:** /home/near/.ssh/

**ssh_config:** istemci ayarları

**sshd_config:** sunucu ayarları

**systemctl status sshd:** çalışan sunucu servisi

Sunucuya bağlanmak için;
```
$ ssh kullanici_adi@sunucu_ip
```
Sunucuya parola girmeden bağlanabilmek için ssh key dosyaları (anahtar seti) sunucuya kopyalanır. Yoksa;
```
$ ssh-keygen
```
komutu ile oluşturulur.

Sunucuya kopyalamak için;
```
$ ssh-copy-id kullanici_adi@sunucu_ip
```
-idnetify file ~/.ssh/id_rsa: başka dizindeki anahtar seçimi

Sunucya özel konfigürasyon ayarları yapmak için */home/x/.ssh/cofig* dosyası oluşurulur.
```
host sunucu
user kullanici_adi
hostname 178.128.244.33
```
Paroala değiştirme;
```
$ passwd
```

###Sunucu - Bilgisayar Dosya Kopyalama

yerel --> sunucu

	scp dosya_adi kullanici@sunucu:dizin

sunucu --> yerel

	scp kullanici@sunucu:dosya /home/near

####rsync
Sunucudan bilgisayara;
```
$ rsync -turv sunucu:[sunucu_dizini] [bilgisayar_dizini]
```
Bilgisayardan sunucuya;
```
$ rsync -turv sunucu:[bilgisayar_dizini] [sunucu_dizini] 
```
* t: preserve modification times 
* u: update (dosya güncelleme)
* r: recursive
* v: verbose
* a: metadatalari da kopyalar (kullanici izinleri)
---


FTP (file transfer protocol)

SFTP (secure file transfer protocol)


---

Uzak sunucuya anahtar taşıyarak bağlanma;

	ssh-add 

* -l: list agent
* -D: delete

####Yerel port tünelleme 

Uzaktaki sunucuda guvenlik gibi sorunlardan dolayı erişilemeyen web hizmetine tünelleme yaparak yakın sunucudan erişebiliriz.

	ssh -L 2201:192.178.56.101:22(uzak sunucu) 192.168.56.102(yakin sunucu)

2201: yakın sunucuda açılacak port

22: uzak sunucuyu aktarmak istediğimiz port

---

####Uzak (ters) port tünelleme 

(Dışarıdan ulaşılamayan uzak sunucudan ters tünelleme yapılır, böylece istemci yakın sunucu aracılığıyla artık uzak sunucuya bağlanabilir. Teknik destek amaçlı kullanılabilir. (NOT: yakın sunucu ile istemci aynı bilgisayar olabilir.)) Uzak makineden asağıdaki komut çalıştırılır.

	$ ssh -R 2201:127.0.0.1:22 192.168.56.102

..102: yakın

..localhost: uzak (ters tünelleme açan bilgisayar)

22: uzak sunucu portu

2201: yakın sunucu (kendi belirlediğimiz)

yakın sunucudan uzak suncunun bağlanıp baglanmadığı kontrol edilir;

	$ netstat -ntlp | grep 2201

yakın sunucudan uzak sunucuya bağlanmak için;

	$ ssh -p 2201 127.0.0.1
---

grafik arayüzü ile bağlanma;

ssh bağlantısı kurulan istemcide xorg-server kurulu olmalıdır.

	$ ssh -X kullanici@sunucu
---

sertifika: LPIC, SUSE, RHEL

