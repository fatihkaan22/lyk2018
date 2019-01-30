#cron

Cron oluşturma;

	$ sudo crontab -e

```
#
#
* * * * * "date >> /tmp/cron.txt"
```
eklediğimiz cron her dakika cron.txt'ye tarih yazar.

![](http://itekblog.com/wp-content/uploads/2013/03/crontab2.png) 

* ***/10:** 10 (dk-saat...)'da bir.

* **6-18/3:** 6 ile 18 arasinda her 3 saatte bir.

* **12,18:** 12'de ve 18'de

---

çevresel değişkenleri sisteme tanımlama;

	export
---

**history komutuna tarih saat bilgileri ekleme;**

_/etc/profile.d/histdate_ dosyası oluşturulur ve aşağıdki satır eklenir.

	export  HISTTIMEFORMAT="%d%m%y %T "

ekleme;

	source /etc/profile.d/histdate

kontrol;

	$ $HISTTIMEFORMAT
	>%d%m%y %T

---

* **source:** Bir dosyadaki komutu mevcut shell de çalıştırır.
* **set:** Tanımlanmış çevresel değişiliklerinin listesi görüntülenir.

