#Bash Betikleri

Shebang: #!

**#!/bin/bash**

* .sh uzantili

* chmod +x myscript.sh


	echo "xxx" | mail -s "Baslik" fatihkaansalgir@gmail.com

---

```
printf "Mesaj"

>Mesaj$
```

---

```
printf "Mesaj\n"

>Mesaj
>$
```

---

```
printf "%s\n" "bir" "iki" "uc"

>bir
>iki
>uc
```

---

```
printf "%.2f\t" 3.5 2.75 6.375

>3.50	2.75	6.37
```

---

```
printf "%03d\t" 1 3 12 405

>001	003	012	405
```

\t: ciktida karakterler arasina *tab* koyar. 

---

* Eşittirin sağında veya solunda boşluk birakılmaz.

```
Degisken="ahmet"  #dogru
```

* *** ve ? değişkende kullanılmaz.

* _ kullanilabilir.

```
_GREP=/bin/grep  #dogru
```
* Değişken çağırma;

```
echo "$_GREP"
>/bin/grep

echo '$_GREP'
>$_GREP
```

* Komut çağırmak için: *` komut `* veya (komut)

echo "Bulundugum yer: $(pwd)"

echo "Gunun tarihi: $`date +%d/%m/%y`"

---

Degisken="Ahmet geldi"

karakter=7

```
echo ${Degisken:0:Karakter}

>Ahmet g
```

---

* Son komutun/programın döndüğü değer: $?
* Betiğin PID: $$
* Kullanıcım: $USER
* Hangi dizindeyim: $PWD
* Kullandıgım path: $PATH

**./betik.sh <arg1> <arg2>;**
* Betiğe geçirilen argüman sayısı: $#
* Betiğe geçirilen argümanlar: $@
* Betiğin ismi(kendisi): $0
* 1. argüman: $1

---

```
echo "Isminiz?"
read Isim
echo "Merhaba, Isim!"
```

---

###Sayısal karşılatırma operatörleri

* eq (equal)
* ne (not egual)
* gt(grater than)
* ge(g)
* lt(lesser than)
* le()

###String karşılaştırma operatörleri

* == veya =: esit
* !=: esit degil
* -z: null
* -n: null degil

###Dosya karşılaştırma operatörleri

* d: dizin ise doğru
* f: dosya ise doğru
* r: okunabilir
* s: 0 byte boyutlu
* w: yazılabilir
* x: çalıştırılabilir
* L: link

test: , [ ]

0: doğru

1: yanlış

```
test a!=b && echo $?
>0
```

---

$((1+2))

* +: toplama
* -: çıkarma
* *: çarpma
* /: bölme
* %: mod alma
* ++: bir arttır
* --: bir azalt
* **: üssü

###Diziler

meyveler=(elma armut kivi muz)

echo ${meyveler[0]}: 0. elemanı yazdırır.

echo ${meyveler[@]}: tum elemanları yazdırır.

echo ${meyveler[*]}: dizideki eleman sayısı

echo ${meyveler[@]:1}: 1. elemandan sonrası

echo ${meyveler[@]:1:2}: 1. ile 2. arası

###Koşul yapilari (if, else, elif, case)

```
sayi=100
if [ "$sayi" -eq 100 ]
then
	echo "sayi 100"
fi
```

---

```
rakam=99
if ["$rakam" -eq 100]; then
	echo "Rakam 100"
else
	echo"Rakam 100 degil"
fi
```

---

```
if [ -f ~/.bash_profile ]; then
	echo "bash_profile dosyasi var."
else
	cp /etc/skul/.bash_profile ~/
fi
```

---
```
rakam=99
if [ "$rakam" -eq 100 ]; then
	echo "Rakam 100"
elif [ "$rakam" -gt 100 ]; then
	echo "rakma 100'den buyuk"
else 
	echo "rakam 100'den kucuk"
fi
```

---

```
BUGUN=$(LC_TIME=en_US.utf8 date + "%a")
case $BUGUN in
	Mon)
		echo ""
case $BUGUN in
	Tue|Wed|Thu|Fri)
		echo ""
case $BUGUN in
	Sat|Sun)
		echo ""
*)
		echo  "bir sorun olustu"
esac
```

###Döngü Yapıları (for, while, until)

```
for Degisken in {1..50}
do
	echo "$Degisken"
done
```

---

	$ SON=50; for i in $(seq 1 $SON); do echo $i; done

---

``` 
deger=0
while [ $deger -lt 4 ]
do
	deger=$((deger+1))
	echo "$deger"
done
```

---

```
deger=0
until [ $deger -gt 4 ]
do
	echo "$deger"
	deger=$((deger+1))
done
```

###Çıkış kodları

* 0: başarılı
* 1: genel hatalar
* 2: içsel komut yanlış kullanım

* 126: komut çalıştırılamayan
* 127: komut bulunamadı
* 128: exit'e yanlış parola
* 128+n: ölumcül hata (işlemci süreç kodları)

* 130: komut ctrl+c ile sonlandırıldı.
