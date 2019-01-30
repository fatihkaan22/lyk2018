#Web Teknolojisine Giriş

İstemciler, sunucular, uygulama ve verıtabanı

HTTP: 80 numarali porttan çalışır.

HTTPS: 443 numarali porttan çalışır.

URL: https://kamp.linux.org.tr

#####**İstemci:** Chrome, Firefox

**Teknolojiler:** 
* HTML 
* CSS 
* JS

#####**Sunucular:** Apache, Nginx, IIS, Google

**Teknolojiler:** 
* PHP 
 * Apache 
 * mail.php 
 * PHP-FPM
* .Net 
* Java 
 * Tomcat 
 * JBoss 
 * Wildfly 
 * Webklogic 
 * Glassfish 
* Python 
* Ruby on Rails 
 * Unicorn 
 * Passenger

#####**Veritabnı** 
* İlişkisel veritabanı
 * MySQL 
 * Oracle 
* İlişkisel olmayan veritabanı 
 * MongaDB 
 * Redis 
 * Cassandra 
* Aarama veritabanı 
 * Elastic search 
 * Solar 
* Nesne Önbelleği veritabanı 
 * Redis
 * Memeache

Sayfa Bütünlüğü;

* GET: adres satırında
* POST: sayfa kaynağında
* COOKIE: oturum yönetimi, kullanıcıya özel sayfa, sunucu takibi
* SSL (Secure Shell Layer): OpenSSL
* ssllabs: sertifika doğrulama sitesi
* letsencrpt: sertifika oluşturma

###List of HTTP status codes

* 1xx (informational response)

* 2xx (success)
* 200: OK

* 3xx (redirection)
* 301: moved permanently 
* 302: found
* 304: not modified

* 4xx (client errors-istemci hata kodlari)
* 400: bad request
* 401: unauthorized
* 403: forbidden
* 404: not found
* 451: Unavailable for legal reasons

* 5xx (Server errors)
* 500: internal server error
* 502: bad geteway
* 503: service unavailble
* 504: gateway timeout

[tüm kodlar](http://www.wiki-zero.co/index.php?q=aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvTGlzdF9vZl9IVFRQX3N0YXR1c19jb2Rlcw)

---

Uzkatan erişemediğimiz sunucuya port açarak ulaşma;

	ssh -D 6868 centos

firefox socks proxy port eklendiğinde istemciden ulaşılabilir.

---

Konsoldan web sayfası içeriklerini görüntüleme;

	# yum install elinks

	# links 192.168.56.101

---

nginx kurulumu;

```
$ yum install http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm

$ yum install nginx

$ systemctl start nginx

$ systemctl enable nginx 
```

Güvenlik duvarına ekleme;

```
$ firewall-cmd --permanent --add-service=http
```

kontrol;
```
$ firewall-cmd reload
```

---

yum bilinmeyen paket kaldırma;

	$ yum -qa | grep nginx

	$ yum remove ...

---

DiskDuplicator (convert and copy file)

biçimlendirme;

	$ dd if=/dev/null of=/dev/sdb

