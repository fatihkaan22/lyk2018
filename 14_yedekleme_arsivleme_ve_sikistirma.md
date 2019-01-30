##Sıkıştırma
####ZIP
####GZIP
* gzip
* gunzip
* zcat: İçeriğini görüntüler.
* zmore
* zless
* zgrep

* -k: keep
* -1-9: fast to best

####BZIP2

* bzip2
* bunzip2
* bzcat

####XZ

##Arşivleme

Klasörleri sıkıştırabilmek için önce arşivlemek gerekir. Arşivlerken eski dosyalar saklanır.

arşivleme:
```
$ tar -cvf [arsiv_olusturulacak_dizin.tar] [/arsive_eklenecek_dizinler]
```
arşivi görüntüleme:
```
$ tar -tvf [dosya adı] 
```
arşivden çıkarma:
```
$ tar -xvf [arsiv_dizini] [cikarilacak_dosya(girilmezse hepsini çıkarır)] -C [/çıkarılacak dizin]
```

* -c: create
* -v: verbose
* -f: file
* -x: extract

---

**aynı zamanda arşivleme ve zipleme:**

```
$ tar -cvzf arsiv.tar.gz [dizin]
```
* z: gzip
* j: bzip2
* J: xz

arşive dosya ekleme; (arşive dosya ekleyebilmek için sıkıştırılmamış olmalıdır.)
```
$ tar -rvf [arsiv] [eklenecek_dosyalar]
```
arşivi bölme; (herhangi bir dosyayı bölmek için de kullanılabilir.)
```
$ split -b [parca_bouyutu_K-M-G] [arsiv.tar.gz] ["arsiv.tar.gz.part"]
```

Bölünen dosyaları birleştirme;

```
$ cat "...part*" > a.iso
```


