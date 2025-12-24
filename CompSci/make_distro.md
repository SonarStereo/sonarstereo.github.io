# Создание загрузочного образа 

Создаём пустой файл образа
~~~bash
dd if=/dev/zero of=image.img iflag=fullblock bs=1M count=100 && sync
~~~

Форматируем под FAT32
~~~bash
mkfs.vfat -F 32 image.img
~~~

Инсталлируем загрузчик syslinux в файл образа
~~~bash
syslinux -install image.img
~~~

Загружаем в qemu
~~~bash
qemu-system-i386 -hda image.img
~~~

# Ссылки
[Creating disk image with msdos partition table and fat32](https://unix.stackexchange.com/questions/771277/creating-disk-image-with-msdos-partition-table-and-fat32)   
[Where to get vmlinuz and initrd.gz files](https://www.linuxquestions.org/questions/debian-26/where-to-get-vmlinuz-and-initrd-gz-files-4175628735/)
