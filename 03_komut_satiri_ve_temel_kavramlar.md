#  Komut Satırı (Kabuk) ve Temel Komutlar
* **komut 1>log.txt 2>hatalog.txt:** komutun çıktı logları log.txt, hatalı çıktıları hatalog.txt ye yazdırır.
* **sudo su:** Root kullanısına geçme. **exit** komutu ile root kullanıcısından çıkılır.
* **curl:**bağlantıyı terminalde gösterir.
* **wget:**bağlantıyı indirir.
* **zip:** zipleme komutu **unzip** dosyayı çıkarır.
* **du:** (disk usage)
* **sort**
* **tail**
* **head**
* **more**
* **less**
* **script:** Terminalde yazılanları dosyaya kaydeder.
* **wc:** (word count)
* **which:** Programın konumunu gösterir.
* **whereis:** Programın binary, source ve manual dosyalarının konumlarını gösterir.
* **&&:** AND [ -a ]
* **||:** OR [ -o ]
* **df:** (disk free)  Bağlı diskleri gösterir.
* **w:** Kullanıcı hakkında ayrıntılı bilgi verir.
* **who:** Kullanıcı hakkında bilgi verir.
* **last:** Son sisteme giriş kayıtlarını görüntüler.


* **/dev/null:** Buraya gönderilen dosya ya da çıktılar silinir.
* **/dev/zero:** Sonsuz sayıda 0'lar oluşturabilen dizin.


##Çıktıdan Sütun-Satır Seçme
Ayırıcı varsa **cut**, boşluklar varsa **awk** komutu kullanılır.
```
awk '{print $[sütun sayısı]}'**
```

ls -l /home/near/ | awk '{print $1}'

```   
cut [dosya] | -d"[ayırıcı]" -f[sütun]
```
cut etc/passwd | cut -d":" -f1-3,6
* **-f:** field

* **uniq:** Çıktıda aynı satırlardan sadece birer tanesini gösterir.

---

sed: Çıktıdan satır seçmek için kullanılır.

Dosyadan 3. satırı seçmek için;

	sed -n 3p dosya.txt

Dosyadan 'abc' geçen bütün satırları seçmek için; 

	sed -n '/abc/p' dosya.txt

###Yardımcı Komutlar
* **nl:** Çıktıda her satırı numaralandırır.

---

* **grep:** Dosyadan arnan karakterleri getirir.

```
grep -Rin "[aranacak karakterler]" [dizin-dosya 1] [dizin-dosya 2]
```
* -v: invert matches (çıktıdan belli satırı çıkarmak için kullanılabilir.)
* R (recursive): Dizinleri de aramaya katar.
* i (ignore case) : Küçük büyük harfe dikkat etmez. 
* n (line number)

---

* **find:** Dosya özelliklerine göre arama yapar. Çıktı olarak sadece dosya isimlerini getirir.

```
$ find [aranacak_dizin] -name [] -type []
```

* iname: igonre case

access modify change değerlerini görüntüleme ve bu değerle göre arama yapma;
```
stat [dosya]
```

```
$ find -(amc)min -[sayi] [dizin]
```

```
$ find -(amc)time +[sayi] -(amc)time -[sayi] [dizin]
```

find ile istenilen dosyalar bulunduktan sonra *-exec* parametresi girilir, find ile bulunan dosyalar yerine '{}' yazılır ve \; ile komut kapanır.

```
$ find ... -exec ... [komut] '{}' \;
```

home daki txt uzantılı dosyaları /tmp/yedek/ dizinine kopyalama;
```
$ find /home/near/ -iname "*.txt" 2>/dev/null -exec cp -v '{}'  /tmp/yedek/ \;
```

---

```
$ locate a.txt
>...a.txt
>...sirala.txt
>...yaka.txt
```

---
Dosya ararken ya da listelerken kullanılabilir. (Wildcards)

* ?: 1 karakterlik
* *: karakter sınırı yok
---

rm -rf /home/deneme

rm /home/deneme -rf

(alttaki daha güvenli, dizin yazarken yanlışlıkla boşluk bırakılması durunda bir güvenlik önlemi daha ekler.)

