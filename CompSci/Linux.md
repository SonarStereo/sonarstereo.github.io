# Диск

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

## Очистка

Удаление файлов журнала до размера 500 Мб:
~~~bash
sudo journalctl --vacuum-size=500M
~~~

