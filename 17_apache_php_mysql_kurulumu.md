Apache kurulumu;

```
# yum install httpd

# systemctl start httpd

# systemctl enable httpd
```

modül ekleme;

```
# yum install mod_ssl(ornek modul)

# systemctl reload httpd
```


sürüm bilgisi;

```
# apachectl -version

# rpm -qa | grep httpd

# httpd -V
```

* /etc/httpd/conf/httpd.conf
* /etc/httpd/conf.d/*.conf
* /etc/httpd/conf.modules.d/*.conf

---

LAMP (linux apache mysql php)

