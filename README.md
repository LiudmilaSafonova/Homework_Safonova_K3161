# Лабораторная работа - Контроль/мониторинг ресурсов
## Введение
Мониторинг процессов позволяет отслеживать показатели центрального процессора, памяти, диска, т.е. узнать использование ресурсов компьютера.

1. Чтобы узнать, насколько загружен процессор, и какие процессы потредляют больше ресурсов, можно ввести команду:
```
top
```
Запишите ID (PID) процесса, который потребляет больше всего ресурсов, и уровень загрузки процессора в процентах

2. Узнайте объем свободной памяти с помощью команды ```free -m``` и запишите его

## Мониторинг "зомби-процессов"
Напишите скрипт, который ищет зомби-процессы (процессы в состоянии ```Z```), записывает их PID и имя в лог-файл, а также сообщает, если таких процессов нет.

1. Создайте файл zombie_process_monitor.sh
2. Сделайте скрипт исполняемым
```
chmod +x zombie_process_monitor.sh
```
3. Запустите скрипт вручную
```
./zombie_process_monitor.sh
```
4. Если таких процессов не оказалось запустите команду
```
bash -c 'sleep 5 & exit'
```

Таким образом был создан и проверен скрипт на выявление зомби-процессов.

## использованные источники
1. [Документация top](https://man7.org/linux/man-pages/man1/top.1.html)
2. [Руководство по команде free](https://man7.org/linux/man-pages/man1/free.1.html)
3. [Зомби-процессы](https://itsecforu.ru/2021/11/11/%f0%9f%a7%9f-%d0%ba%d0%b0%d0%ba-%d0%bd%d0%b0%d0%b9%d1%82%d0%b8-%d0%b8-%d1%83%d0%b1%d0%b8%d1%82%d1%8c-%d0%b7%d0%be%d0%bc%d0%b1%d0%b8-%d0%bf%d1%80%d0%be%d1%86%d0%b5%d1%81%d1%81%d1%8b-%d0%b2-%d1%81%d0%b8/)
