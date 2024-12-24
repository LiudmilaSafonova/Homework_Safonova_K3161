# Контроль/мониторинг ресурсов
## Введение
1. Запустила top
![Screenshot 2024-12-24 193315](https://github.com/user-attachments/assets/bcad3474-e6de-45af-8ae3-db21016dfeff)

* ID (PID) процесса, который потребляет больше всего ресурсов - 156676
* Уровень загрузки процессора в процентах - 0.7%

2. Объем свободной памяти - 97 MB
![Screenshot 2024-12-24 193345](https://github.com/user-attachments/assets/9f4d51d9-8d9e-4406-9522-ea3e5a91862d)
3. Использование iostat
![Screenshot 2024-12-24 193419](https://github.com/user-attachments/assets/047b43a5-0a6c-400e-84f3-a667e2545f0d)
4. Использование ss -l
![Screenshot 2024-12-24 193624](https://github.com/user-attachments/assets/89501eae-a73a-4a85-8d3d-435fd134f5b0)
 
## Создание стресс-ситуаций и их решение
### Работа с CPU
В одном из окон терминала запустила команду ```stress -c 2``` - на два ядра
![Screenshot 2024-12-24 194032](https://github.com/user-attachments/assets/795c6e88-249f-4d64-8582-b6f11e8e3d4f)

Для того, чтобы завершить процесс нашла его идентификатор PID и командой 
```
kill 171010
```
завершила весь процесс.

### Работа с диском
Создала стрессовую ситуацию командой
```
dd if=/dev/zero of=/tmp/testfile bs=1M count=5000 oflag=direct
```
![Screenshot 2024-12-24 194640](https://github.com/user-attachments/assets/a475162f-0ed2-4a38-8cab-23c191b6ab69)
![Screenshot 2024-12-24 195130](https://github.com/user-attachments/assets/b2d28416-ed14-4056-ace9-ac46e4154251)
```
kill 180795
```
завершила процесс.

Повторно начала прерванный процесс создания. С помощью команды ```fatrace``` установила путь, где создается файл.
![2d4cfd73-f302-43d9-8edb-7f5230236369](https://github.com/user-attachments/assets/f898495f-ec85-4582-8178-7a5ffaa849bf)

после удалила его
```
rm /tmp/testfile
```

### Работа с сетями

Серверная ВМ
![feba0008-15c3-4d65-8b57-be25027f81d4](https://github.com/user-attachments/assets/24dc3fa7-222b-45a7-b439-a78419d0bdd8)

Клиентская ВМ
![d548ca73-387f-4f90-88a9-8ebdcfb11437](https://github.com/user-attachments/assets/32540126-9f24-416c-8e9a-6633cfe61e25)

```
watch -d "ss | grep tcp"
```
![1996b5f1-1c3f-4e79-b6cd-cf9252b18b94](https://github.com/user-attachments/assets/5af7c8fb-34f2-459d-a9c4-0691f99c5854)

```
iftop
```
![5d210726-1fff-4f7a-bde1-091248ae8349](https://github.com/user-attachments/assets/1dd5bc90-1e68-43d6-ba09-a77e54a5ad22)

