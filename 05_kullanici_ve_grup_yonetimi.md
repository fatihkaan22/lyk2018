#Kullanıcı Yönetimi

Kullanıcı değiştirme;

	su [kullanici]

Kullanıcıyı çevresel değişiliklerle birlikte değiştirme;

	su - [kullanici]

###Komutlar

* id [user] [group]: Kullanıcı ve group hakkında bilgi verir. 
* sudo: Komutu farklı bir kullanıcı üzerinden çalıştırır.
* usermod: diğer kullanıcıların hesaplarında değişiklik yapmayı sağlar. (parola, home dizini gibi)
* groups: Kullanıcının gruplarını gösterir.
* gpasswd: Kullanıcıyı gruba eklme ve çıkarma.
* addgroup/groupadd
* groupdel/delgroup
* useradd
* userdel

---

etc/sudoers: sudo kullanıcılarının yetkilerini belirler.

---

Kullanıcı terminal ayarları (renk,bilgisayar adı gibi) *.bashrc* dosyaysında tutulur.
Dosya düzenlenerek kullanıcıya özel komutlar oluşturulabilir. 

*alias isim='echo "Fatih Kaan Salgır"'*

olarak düzenlendiğinde;

```
$ isim
>>>Fatih Kaan Salgır
```
---

* Kullanıcılara özel uygulama kofigürasyon dosyaları kendi */home/.config* dizinlerinde saklanır.

---

* *etc/passwd* dosyasında tüm kullanıcıların kullanıcı adı, parola olup olmadığı, kullanıcı-grup id'leri, home dizinleri ve kullandıkları shell dizini bulunur.

##İzinler

![permissions](https://s-media-cache-ak0.pinimg.com/564x/ef/22/9e/ef229e5fa7b707e9254c7c8961a4e392.jpg) 

yetki vermek ya da almak için;
```
$ chmod [(ugo)(+-)(rwx)] [dizin]
``` 
user, group, others / / read, write, execute

* */bin/ls* altında çalıştırılabilir dosyalar bulunur (komutlar), bu komutlardan diğer kullanıcıların çalıştırma yetkisi alınabilir.

r=4

w=2

x=1

```
$ chmod [xxx] [dosya_adi]
```
-R: recursive (dizin altındaki tüm dosyaların yetkisini değiştirme)

* root kullaıcılarının bile yetkilerini engellemek için *chattr (change attribute)* komutu kullanılır.
```
$ chattr (-+)i [dosya]
```

i: immutable

a: append (sadece ekleme yapılabilir.)

* *etc/passwd* immutable yapılarak sisteme yeni kullanıcı ekleme kapatılabilir.

attribute görüntüleme;
```
$ lsattr [dosya]
```

user ve group değiştirme;
```
$ chown user:group [dosya]
``` 
---
###suid (2) - sgid (4)
etc/passwd ve /shadow dosyalarında kullanıcıların write izini yoktur.

	-rw-r--r--   1 root root     2469 Jul 21 18:26 passwd
	-rw-r-----   1 root shadow   1276 Jul 21 18:26 shadow

Ancak kullanıcı *passwd* komutuyla parolasını değiştirebilir. Çünkü passwd komutu suid sayesinde diğer kullanıcılar için de çalışır. Dosya sahibinin yetkilerini anlık olarak kullanıcıya verir.

	-rwsr-xr-x 1 root root 59640 Jan 25 18:09 ./passwd*


###sticky bit (1)

```
chmod +t
```

/tmp dizini;

	drwxrwxrwt  15 root root      4096 Jul 26 12:17 tmp/
---

	chmod xnnn

x: stickybit, suid, guid değerlerini toplamı girilerek kullanıabilir.


