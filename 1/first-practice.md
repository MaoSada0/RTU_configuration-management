# Практика №1

## Задание 1
```bash
cut -d: -f1 /etc/passwd | sort
```
- cut - извлечение определённых полей из каждой строки
- -d - делает ':' символом разделителя полей (split в общем и целом)
- -f1 - выбирает первое поле из этих строк

![task_1](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_1.png)


## Задание 2
```bash
cat /etc/protocols | tail -n 5 | sort -nrk2 | awk '{print $2, $1}'
```
- cat - распечатать содержимое файла
- tail -n 5 - выбирает 5 последниъ строк
- -n - значит числовая последовательность
- -r - в обратном порядке сортирует
- -k2 - по 2 столбцу
- awk - форматирование вывода ('{print $2, $1} значит сначала второй столбец, потом первый)


![task_2](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_2.png)

## Задание 3
```bash
#!/bin/bash
string=$1
size=${#string}
echo -n "+"
for ((i=0;i<size+2;i++))
do
echo -n "-"
done
echo "+"
echo "| $string |"
echo -n "+"
for ((i=0;i<size+2;i++))
do
echo -n "-"
done
echo "+"
```
- -n в echo убирает "\n" 

![task_3](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task3.png)


## Задание 4
```bash
grep -o '\b[a-zA-Z_][a-zA-Z0-9_]*\b' Main.java | sort | uniq
```
- grep - поиск шаблона в файле
- -o - выводит только то что соответствует шаблону
- \b[a-zA-Z_][a-zA-Z0-9_]*\b - шаблон (\b - граница, * -ноль или больше символов)

![task_4](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_4.png)



## Задание 5
```bash
#!/bin/bash

chmod +x "$1"
sudo cp "$1" /usr/local/bin/
```

![task_5](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_5.png)
