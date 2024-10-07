# Практика №3

## Задание 1

```jsonnet
local groupPrefix = 'ИКБО-';
local year = '-20';
local groupNum = std.range(1, 24);

local studentData = [
  {name: "Иванов И.И.", age: 19, groupIndex: 4},
  {name: "Петров П.П.", age: 18, groupIndex: 5},
  {name: "Сидоров С.С.", age: 18, groupIndex: 5},
  {name: "Какряцкий А.М.", age: 19, groupIndex: 12}
];

{
  groups: [groupPrefix + std.toString(i) + year for i in groupNum],

  students: [
    {
      age: student.age,
      group: groupPrefix + std.toString(student.groupIndex) + year,
      name: student.name
    } for student in studentData
  ],

  subject: "Конфигурационное управление"
}
```
![{F0A46732-6376-4491-B179-7904BDD32B50}](https://github.com/user-attachments/assets/b30614f1-637e-4c80-82b3-bd8029da140c)

## Задание 2

```
let Group = Text
let Student = { age : Natural, group : Group, name : Text }

let createGroup : Natural -> Group =
      λ(n : Natural) → "БИВТ-" ++ (Natural/show n) ++ "-21"

let groups =
      List/map
        Natural
        Group
        createGroup
        (List/replicate 10 (λ(i : Natural) → i + 1))

let createStudent : Natural -> Group -> Text -> Student =
      λ(age : Natural) → λ(group : Group) → λ(name : Text) →
        { age = age, group = group, name = name }

let students =
  [ createStudent 20 (createGroup 2) "Александров А.А."
  , createStudent 21 (createGroup 3) "Борисов Б.Б."
  , createStudent 22 (createGroup 1) "Васильев В.В."
  , createStudent 20 (createGroup 4) "Какряцкий А.М."
  ]

in  { groups = groups, students = students, subject = "Программирование" }
```

## Задание 3

```BNF
<digit> = 0 | 1
<string> = <digit> | <digit> <string>
```

## Задание 4

```BNF
<openFirst> = (
<openSecond> = {
<closeFirst> = )
<closeSecond> = }
<string> =  <openFirst> <closeFirst> | <openSecond> <closeSecond> | <openFirst> <string> <closeFirst> | <openSecond> <string> <closeSecond>

```

## Задание 5
'#' - разделитель

```BNF
<expression> = <term> # <open> <term> <operation> <term> <close> # <negative> <open> <term> <operation> <term> <close> # <open> <expression> <operation> <expression> <close> # <negative> <open> <expression> <close>
<term> = <variable> # <negative> <variable> # <open> <variable> <operation> <variable> <close> # <negative> <open> <variable> <operation> <variable> <close>
<variable> = x # y # z # w
<operation> = & # |
<negative> = ~
<open> = (
<close> = )
```
