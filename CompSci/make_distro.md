# Создание загрузочного образа 

Создаём пустой файл образа
~~~bash
dd if=/dev/zero of=image.img iflag=fullblock bs=1M count=100 && sync
~~~

Размечаем
~~~bash
fdisk image.img
~~~

Форматируем под FAT32
~~~bash
mkfs.vfat -F 32 image.img
~~~

Инсталлируем загрузчик syslinux в файл образа
~~~bash
syslinux -install image.img
~~~

Монтируем образ диска как loop-устройство (туда можно будет скопировать файлы)
~~~bash
mount -o loop image.img /tmp/img
~~~

Размонтируем
~~~bash
umount /tmp/img
~~~

# QEMU

Загрузка с виртуального диска
~~~bash
qemu-system-i386 -hda image.img
~~~

Загрузка с CD ROM, данные - на образе жёсткого диска

# Ссылки
[Creating disk image with msdos partition table and fat32](https://unix.stackexchange.com/questions/771277/creating-disk-image-with-msdos-partition-table-and-fat32)   
[Where to get vmlinuz and initrd.gz files](https://www.linuxquestions.org/questions/debian-26/where-to-get-vmlinuz-and-initrd-gz-files-4175628735/)
