Установка ncurses (пригодится для отображения меню при компиляции ядра с menuconfig)
~~~bash
sudo apt-get install libncurses-dev
~~~

Посмотреть информацию о процессе с PID 1:
~~~bash
ps -q 1
~~~

# Загрузка 

Микрокод
* BIOS
* UEFI

Загрузчики
* GRUB
* syslinux (лёгкий)
* U-Boot (для embedded)

# Диск

## Устройство

* контроллер
* DMA
* интерфейсы SATA, NVME, IDE
* сектора (512 байт или 4 Кб), цилиндры
* группа секторов - кластер, размер определяется при форматировании
* LBA - logical block

  
## Иерархия папок
File hierarchy standard (FHS)


```/bin```: основные утилиты типа ```cat```, ```ls```

```/etc```: файлы конфигурации

```/var```: логи и прочие быстро меняющиеся (variative) файлы

```/var/log/journal```: системный журнал

## Диагностика 
Просмотр размера папок первого уровня (```/bin```, ```/etc``` и т.д.)
~~~bash
sudo du -hx --max-depth=1 /
~~~

Просмотр размера файлов журнала
~~~bash
sudo journalctl --disk-usage
~~~

Свободное место (показывает разделы snap)
~~~bash
df -kh
~~~

## Очистка

Удаление файлов журнала до размера 500 Мб:
~~~bash
sudo journalctl --vacuum-size=500M
~~~


  
# Сборка образа
Минимум
* загрузчик
* сжатое ядро vmlinuz
* образ корневой системы initrd/initramfs

  
# Информация
[Linux Device Drivers](https://lwn.net/Kernel/LDD3/)   
[Building Embedded Linux Systems](https://www.esys.ir/Files/Ref_Books/Linux/esys.ir_Building.Embedded.Linux.Systems.2nd.Edition.pdf)    
[Linux Kernel Labs Бухарест](https://linux-kernel-labs.github.io/refs/heads/master/)   

