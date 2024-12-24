# Контроль/мониторинг ресурсов
## Введение
1. Запустила top
![image](https://github.com/user-attachments/assets/a3fbbef8-7efe-4f19-a7dd-ad43746d0c71)
* ID (PID) процесса, который потребляет больше всего ресурсов - 1154
* Уровень загрузки процессора в процентах - 0.3%

2. Объем свободной памяти - 1544
![image](https://github.com/user-attachments/assets/a22c428a-617d-4e1f-aadc-329b3fa2ab70)

## Зомби-процессы
Я создала следующий bash-скрипт
```bash
#!/bin/bash

echo "$(date): Checking for zombie processes..." >> zombie_process.log
ZOMBIES=$(ps aux | awk '$8 == "Z" {print $2, $11}')

if [ -z "$ZOMBIES" ]; then
    echo "$(date): No zombie processes found." >> zombie_process.log
else
    echo "$(date): Found zombie processes:" >> zombie_process.log
    echo "$ZOMBIES" >> zombie_process.log
fi

echo "------------------------" >> zombie_process.log
```


При выполнении скрипта в файл zombie_process.log добавляется следующая запись:
![image](https://github.com/user-attachments/assets/a1438e5a-f594-4009-b669-a9d832df6609)
т.е. уже есть зомби-процессы
