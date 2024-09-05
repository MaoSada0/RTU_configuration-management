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

## Задание 6
```bash
#!/bin/bash

for file in "$@"; do
  if [[ "$file" =~ \.(c|js|py|java)$ ]]; then
    first_line=$(head -n 1 "$file")
    if [[ "$first_line" =~ ^# && "$file" =~ \.(py)$ ]]; then
      echo "$file has comment in the first line."
    elif [[ "$first_line" =~ ^// && "$file" =~ \.(c|java|js)$ ]]; then
      echo "$file has comment in first line"
    else
      echo "$file doesnt have comment in first line"
    fi
  fi
done
```

![task_6](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_6.png)


## Задание 7
```bash
find "./" -type f -exec md5sum {} + | sort | uniq -w32 -dD | awk '{print $2}'  
```
- -type f - только файлы
- exec md5sum - для каждого применить md5sum
- -w32 - первые 32 символа
- -d - выбрать только то что дубликат
- -D - выбрать эти стркои
![task_7](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_7.png)

## Задание 8
```bash
find . -name "*.txt" -print0 | tar -czvf ans.tar --null -T -
```
- -print0 - разделяет файлы нулевым байтом
- -c —создать новый архив
- -z — сжать с помощью gzip
- -v — выводить имена файлов которые добавляются в архив
- -f ans.tar - название
- --null - данные разделены нулевым байтом 
![task_8](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_8.png)

## Задание 9
```bash
#!/bin/bash

sed 's/    /\t/g' "$1" > "$2"
```
- sed - текстовые преобразования
- 's/ /\t/g' - s - значит замена; / 4 пробела / на \t (табуляция) / g - заменить все
- "$1" > "$2" - из первого файла во второй 
![task_9](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_9.png)

## Задание 10
```bash
find ./ -type f -empty -name "*.txt"
```

![task_10](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/1/task_10.png)
