##İlişkisel Veritabanı

primary key/secondary key

SGL (Structured Query Language): veritabanlarında kullanılan dil

* DDL: Data Defination Language

* DML: Data manipulation language

**Numerik veri tipleri:** integer, float

**Metin veri tipleri:** characther/char, archer, text

**Tarih/saat veri tipleri:** date, time, timestamp

**Mantıksal veri tipleri:** booleon (true/false)

####DML (Data Manipulation Language)

SELECT: sorgulama

INSERT: veri girişi

DELETE: silme

UPDATE: güncelleme

```
kolon1,kolon2 FROM tablo1 WHERE kolon1=1;
... ORDER BY kolon2;
... GROUP BY kolon1,kolon2;
```

ASC/DESC: ascending/descending

WHERE: = , > , < , >= , <= , <> / ! (eşit değildir) , AND , OR

---

PostgreSQL kurulum;

```
# sudo yum install https://download.postgresql.org/pub/repos/yum/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm
# sudo yum install postgresql10-server postgresql10-contrib
# /usr/pgsql-10/bin/postgresql-10-setup initdb
# systemctl start postgresql-10
# systemctl enable postgresql-10
```

postgresql oturum açma;

```
# su - postgresql
$ psql
```

---

```
# su - postgresql
$ psql
# CREATE DATABASE dvdrental;
\q
```
---
```
wget http://www.postgresqltutorial.com/wp-content/uploads/2017/10/dvdrental.zip
unzip dvdrental.zip
pg_restore -d dvdrental dvdrental.tar
```
---
```
psql
\c dvdrental
```
---
```
\dt
```
---
```
SELECT * from film;
:Space:
:q:
```
