#Sistem Kayıtaları (Loglar)

|Facility |	Priority|
|---------|		|
|kern	  |	emerg	|	
|user	  |	alert	|
|mail	  |	info	|
|syslog   |	warning|
|user  	  |	crit	|
|auth 	  |	err	|		
|...	  |	debug	|
|local 0-7|	

###/etc/rsyslog

Logları yönetir.

**rsyslog = syslog + module**

rsyslog.conf dosyaysı düzenlenerek log sunucusu haline getirilebilir.

```
...
# provides UDP syslog reception
#module(load="imudp")
#input(type="imudp" port="514")

# provides TCP syslog reception
#module(load="imtcp")
#input(type="imtcp" port="514")
...
```
izinler:
```
# Set the default permissions for all log files.
#
$FileOwner syslog
$FileGroup adm
$FileCreateMode 0640
$DirCreateMode 0755
$Umask 0022
$PrivDropToUser syslog
$PrivDropToGroup syslog
```

/etc/rsyslog.conf: ayar dosyaları tutulur. Ancak bu yapının değiştirilmesi pek istenmez. Bu yüzden bir de *rsyslog.d* dizini bulunur. Değişiklikler buraya eklenir.

|**Facility Örn.**	|	**Hedef**
|-----------------------------------------------
|mail.alert             | /var/log/mail.alert.log
|mail.*                 | /var/log/mail.log	
|			| /var/log/httpd/httpd.log
|local0.*               | @syslogsunucu:port

	logger -p mail alert

####Log dosyası oluşturma

1-rsyslog.conf'a facility ve dizini eklenir.

```
	local5.*	/var/log/deneme.log
```
2-servis yeniden başlatılır.

	$ service rsyslog restart

3-logger ile log gönderilir.

	$ logger -p local5.info "test logu"

####/var/log:

* /messages: sistem 
* /dmesg: çekirdek logları
* /boot.log: sistem açılış
* /yum.log: paket yüklemeleri
* /cron: zamanlanmış görevler
* /last 
* /wtmp: kullanıcı güvenliği
* /btmp  

**logrotate:** Belli aralıklara göre logların başka işlmelerden geçmesi gerekir. (Taşınması, sıkıştırılması ve zamanlanması gibi.)

**/etc/logrotate.d/:** Belli zaman arakıklarrıyla logların arşivlenmesini yapaer.

**last:** sistem loglarını görüntüler. (/var/log/wtmp) 

**lastb:** yanlış parola girme gibi güvenlik ihlali loglarını gösterir. (/var/log/btmp)

####Merkezi log sistemleri

* syslog
* graylog
* logstash

