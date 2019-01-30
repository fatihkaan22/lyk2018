#Disk Yönetimi

MBR: Master Boot Record (primary extended) (max 4'e kadar bölünebilir, primary ve extended seçilir.)

GPT: GUID Partition Table (512 MB) (daha güvenli)

* /etc/fstab: Diskleri bilgisayar açılışında mount eder.

---

###Yeni Disk Sistemi Oluşturma

1-Diski bölümle (fdisk/parted)
2 Diski formatla (mkfs)
3 Diski bağlama (mount+/etc/fstab)

####1a-fdisk
Disk yönetim aracı.

	$ fdisk [/dev/sdb] 

* n: new partition
* p: print partition table
* w: write changes !

####1b-parted

Diskleri listele;

	parted -l

* select: disk seçimi
* mklabel: bölümleme seçimi (MBR/GPT)
* mkpart: (ext4/fat32)
* print
* unit: MB/GB/TB

####2-Diski formatlama
oluşturduğumuz disk hala formatlı değil.

	$ mkfs -t ext4 /dev/sdb1

####3-Diski bağlama

	$ mount /dev/sdb1 /mnt/

disk bağlandı. Görüntülemek için;

	$ df -hT

Bilgisayar yeniden başladığında bağlantın kalıcı olması için */etc/fstab* a yazılır.

```
	...
	/dev/sdb1	ext4	defaults	0 0
```

####Yardımcı Komutlar
List block devices:

	$ lsblk
mount/unmount;

	$ mount [disk(/dev/sda1)] [bağlanılacak_dizin]       
	$ umount 

####fsck

Linux dosya sistemlerinin kontrol ve tamir işlemlerini gerçekleştirir.

Diskte hata taraması yapar. Örneğin badblock. Diskteki badblock karantına altına alınabilir ancak bulaşıcıdır. Diskin en kısa sürede değiştirilmesi gerekir.

[LVM](https://wiki.ubuntu.com/Lvm)

###Link oluşturma

#####1-Hard link

Linklenen tüm dosyalar aynı inode numarası ile kaydedilir. Diskte her biri ayrı ayrı yer kaplmamaz. Biri değişince diğerleri de değişir ancak biri silinince diğerleri silinmez. Hard link oluşturulurken tüm linkler için full path zorunludur. Hard link sadece aynı disk üzerinde oluşturulabilir. Çünkü inode numarası çağırır ve bu diske özeldir.

        $ ln [dosya_1] [dosya_2] [dosya_3]

* Neden etc/passwd dosyası hard link oluşturulmaz?

Oluşturulan dosyanın user:group değerleri farklı olacağından buna izin verilmez.


#####2-Soft link (Symbolic link)

Windows`taki kısayola benzer. Linklenen dosya inode numarasını değil, ana dosyayı gösterir. Farklı disklere soft linkler yapılabilir.

        $ ln -s [ana_dosya] [link_dosyasi_1] [link_dosyasi_2]

* Eğer soft link oluşturulurken full path yerine bağıl bir adres kullanılırsa, link dosyası taşındığında çalışmaz.


