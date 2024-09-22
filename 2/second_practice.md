
# Практика №2

## Задание 1
Установка:
- С помощью менеджера пакетов:
```bash
pip install matplotlib
```
- Прямо из репозитория:
```bash
git clone https://github.com/matplotlib/matplotlib.git
cd matplotlib
pip install .
```

Вывести служебную информацию:
```bash
pip show matplotlib
```
![task_1](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/2/task_1.png)

## Задание 2
Установка:
- С помощью менеджера пакетов:
```bash
npm install express
```
- Прямо из репозитория:
```bash
git clone https://github.com/expressjs/express.git
cd express
npm install .
```

Вывести служебную информацию:
```bash
npm show express
```
![task_2](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/2/task_2.png)

## Задание 3
### Matplotlib
- graphviz-код matplotlib
```graphviz
digraph MatplotlibDeps {
    node [shape=box];

    "matplotlib" -> "contourpy";
    "matplotlib" -> "cycler";
    "matplotlib" -> "fonttools";
    "matplotlib" -> "kiwisolver";
    "matplotlib" -> "numpy";
    "matplotlib" -> "packaging";
    "matplotlib" -> "pillow";
    "matplotlib" -> "pyparsing";
    "matplotlib" -> "python-dateutil";

    "contourpy" [label="contourpy"];
    "cycler" [label="cycler"];
    "fonttools" [label="fonttools"];
    "kiwisolver" [label="kiwisolver"];
    "numpy" [label="numpy"];
    "packaging" [label="packaging"];
    "pillow" [label="pillow"];
    "pyparsing" [label="pyparsing"];
    "python-dateutil" [label="python-dateutil"];
}
```
- Получение изображения зависимостей
```bash
dot -Tpng matplotlib_deps.dot -o matplotlib_deps.png
```
- -Tpng - расширение выходного файла
- -o - имя выходного файла
![matplotlib_deps](https://github.com/user-attachments/assets/197ae33e-2f8b-4b18-bbbb-2ac3177c9f69)

### Express
- graphviz-код express
```graphviz
digraph ExpressDeps {
    node [shape=box];

    "express" -> "accepts";
    "express" -> "array-flatten";
    "express" -> "body-parser";
    "express" -> "content-disposition";
    "express" -> "content-type";
    "express" -> "cookie";
    "express" -> "cookie-signature";
    "express" -> "debug";
    "express" -> "depd";
    "express" -> "encodeurl";
    "express" -> "escape-html";
    "express" -> "etag";
    "express" -> "finalhandler";
    "express" -> "fresh";
    "express" -> "http-errors";
    "express" -> "merge-descriptors";
    "express" -> "methods";
    "express" -> "on-finished";
    "express" -> "parseurl";
    "express" -> "path-to-regexp";
    "express" -> "proxy-addr";
    "express" -> "qs";
    "express" -> "range-parser";
    "express" -> "safe-buffer";
    "express" -> "send";
    "express" -> "serve-static";
    "express" -> "setprototypeof";
    "express" -> "statuses";
    "express" -> "type-is";
    "express" -> "utils-merge";
    "express" -> "vary";

    "accepts" [label="accepts"];
    "array-flatten" [label="array-flatten"];
    "body-parser" [label="body-parser"];
    "content-disposition" [label="content-disposition"];
    "content-type" [label="content-type"];
    "cookie" [label="cookie"];
    "cookie-signature" [label="cookie-signature"];
    "debug" [label="debug"];
    "depd" [label="depd"];
    "encodeurl" [label="encodeurl"];
    "escape-html" [label="escape-html"];
    "etag" [label="etag"];
    "finalhandler" [label="finalhandler"];
    "fresh" [label="fresh"];
    "http-errors" [label="http-errors"];
    "merge-descriptors" [label="merge-descriptors"];
    "methods" [label="methods"];
    "on-finished" [label="on-finished"];
    "parseurl" [label="parseurl"];
    "path-to-regexp" [label="path-to-regexp"];
    "proxy-addr" [label="proxy-addr"];
    "qs" [label="qs"];
    "range-parser" [label="range-parser"];
    "safe-buffer" [label="safe-buffer"];
    "send" [label="send"];
    "serve-static" [label="serve-static"];
    "setprototypeof" [label="setprototypeof"];
    "statuses" [label="statuses"];
    "type-is" [label="type-is"];
    "utils-merge" [label="utils-merge"];
    "vary" [label="vary"];
}
```
- Получение изображения зависимостей
```bash
dot -Tpng express_deps.dot -o express_deps.png
```
- -Tpng - расширение выходного файла
- -o - имя выходного файла

![express_deps](https://github.com/MaoSada0/configuration-management-RTU/blob/main/screenshot/2/express_deps.png)


## Задание 4
Код MiniZinc
```MiniZinc
include "globals.mzn";
var 0..9: a;
var 0..9: b;
var 0..9: c;
var 0..9: d;
var 0..9: e;
var 0..9: f;

constraint a + b + c == d + e + f;
constraint all_different([a, b, c, d, e, f]);

solve minimize a + b + c;
```
![изображение](https://github.com/user-attachments/assets/f7451081-09dd-483f-9f6d-49252e8c7766)

## Задание 5
Код MiniZinc
```MiniZinc
set of int: Root = {1};
set of int: Menu_Versions = {150, 140, 130, 120, 110, 100}; 
set of int: Dropdown_Versions = {230, 220, 210, 200, 180}; 
set of int: Icons_Versions = {200, 100};  

var Menu_Versions: menu_version;
var Root: root;
var Dropdown_Versions: dropdown_version;
var Icons_Versions: icons_version;

constraint
    if root = 1 then
        (menu_version = 100 \/ menu_version = 150 \/ icons_version = 100) endif;

constraint
    if (menu_version = 150 \/ menu_version = 140 \/ menu_version = 130 \/ 
     menu_version = 120 \/ menu_version = 110) then
        (dropdown_version = 230 \/ dropdown_version = 200) endif;

constraint
    if menu_version = 100 then dropdown_version = 180 endif;

constraint
    if (dropdown_version = 230 \/ dropdown_version = 220 \/ 
     dropdown_version = 210 \/ dropdown_version = 200) then
        icons_version = 200 endif;
    
solve satisfy;
```

![изображение](https://github.com/user-attachments/assets/b6501c1c-bc73-4509-a04e-a81f831ac655)

## Задание 6
Код MiniZinc
```MiniZinc
int: root = 100;
var 100..300: foo;
var 100..300: target;
var 100..300: right;
var 100..300: left;
var 100..300: shared;


constraint
    if root = 100 then
        (foo >= 100 /\ foo < 200) /\ (target >= 200 /\ target < 300) endif;

constraint
    if (foo = 110) then
        (left >= 100 /\ left < 200) /\ (right >= 100 /\ right < 200) endif;
        
constraint    
    if (foo = 100) then true endif;
    
constraint
    if (left = 100) then
        shared >= 100 endif;    
        
constraint
    if (right = 100) then
        shared < 200 endif;    
        
constraint    
    if (shared = 200) then true endif;

constraint
    if (shared = 100) then
       (target >= 100 /\ target < 200) endif;   
     
constraint    
    if (target = 100 \/ target = 200) then true endif;
    
solve satisfy;
```

![{37907F86-48D9-4AE7-8771-A79D06CBD92F}](https://github.com/user-attachments/assets/c84ddcb5-c789-4f53-baa9-fad7d803f8ed)




