# Практика №1

## Задание 1
> ````cut -d: -f1 /etc/passwd | sort````
- cut - извлечение определённых полей из каждой строки
- -d - делает ':' символом разделителя полей (split в общем и целом)
- -f1 - выбирает первое поле из этих строк

![task_1](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_1.png)


## Задание 2
> ````cat /etc/protocols | tail -n 5 | sort -nrk2 | awk '{print $2, $1}'````
- cat - распечатать содержимое файла
- tail -n 5 - выбирает 5 последниъ строк
- -n - значит числовая последовательность
- -r - в обратном порядке сортирует
- -k2 - по 2 столбцу
- awk - форматирование вывода ('{print $2, $1} значит сначала второй столбец, потом первый)


![task_2](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_2.png)
