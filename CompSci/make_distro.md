# Создание загрузочного образа, рецепт 2

# Создание загрузочного образа, рецепт 1 

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

Создание первичного раздела FAT32
~~~bash
fdisk image.img << EOF n p 1 t c w EOF
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


# Просмотр, диагностика

Посмотреть содержимое iso - достаточно просто примонтировать его как loop-устройство куда-нибудь в ФС: 
~~~bash
sudo mount -o loop /path/to/yourfile.iso /tmp/iso
~~~

# Tiny Core Linux
[Форум](forum.tinycorelinux.net)   
[Основные файлы: vmlinuz, core.gz, rootfs, modules](http://tinycorelinux.net/14.x/x86/release/distribution_files/)   
[How to make a legacy bios/uefi dual boot usb stick with syslinux](https://forum.tinycorelinux.net/index.php/topic,20939.0.html)   
[Howto make a legacy bios/uefi dual boot usb stick with grub2](https://forum.tinycorelinux.net/index.php/topic,19364.0.html)   


# DOS
Основные системные файлы:
* IO.SYS: инициализация системы, встроенные драйвера; 
* MSDOS.SYS: ядро DOS;
* COMMAND.COM: командный интерпретатор;
* AUTOEXEC.BAT: выполняется интерпретатором для выполнения команд при запуске;
* CONFIG.SYS: конфигурация DOS, загрузка драйверов устройств.

# QEMU

Загрузка с виртуального диска
~~~bash
qemu-system-i386 -hda image.img
~~~

Загрузка FreeDOS с CD ROM, данные - на образе жёсткого диска
~~~bash
qemu-system-i386 -drive file=image.img -cdrom FD14LIVE.iso -boot d
~~~

# Минималистичные ОС


[Документация и книга по TinyCore](https://distro.ibiblio.org/tinycorelinux/book.html)

[Minimal Linux Live](https://github.com/ivandavidov/minimal)   
маленький Линукс, пошаговая компиляция - сначала ядро, потом BusyBox, glibc, создание initramfs;    
процесс сборки описан в
[DAO MLL](https://github.com/ivandavidov/minimal/blob/master/docs/the_dao_of_minimal_linux_live.txt)

[KolibriOS](http://old-dos.ru/index.php?page=files&mode=files&do=show&id=856)   
написана энтузиастами из СНГ полностью на ассемблере

# Ссылки
[Creating disk image with msdos partition table and fat32](https://unix.stackexchange.com/questions/771277/creating-disk-image-with-msdos-partition-table-and-fat32)   
[Where to get vmlinuz and initrd.gz files](https://www.linuxquestions.org/questions/debian-26/where-to-get-vmlinuz-and-initrd-gz-files-4175628735/)

