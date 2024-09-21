# Практика №2

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
      λ(n : Natural) → "ИКБО-" ++ (Natural/show n) ++ "-20"

let groups =
  [ createGroup 1
  , createGroup 2
  , createGroup 3
  , createGroup 4
  , createGroup 5
  , createGroup 6
  , createGroup 7
  , createGroup 8
  , createGroup 9
  , createGroup 10
  , createGroup 11
  , createGroup 12
  , createGroup 13
  , createGroup 14
  , createGroup 15
  , createGroup 16
  , createGroup 17
  , createGroup 18
  , createGroup 19
  , createGroup 20
  , createGroup 21
  , createGroup 22
  , createGroup 23
  , createGroup 24
  ]

let createStudent : Natural -> Group -> Text -> Student =
      λ(age : Natural) → λ(group : Group) → λ(name : Text) →
        { age = age, group = group, name = name }

let students =
  [ createStudent 19 (createGroup 4) "Иванов И.И."
  , createStudent 18 (createGroup 5) "Петров П.П."
  , createStudent 18 (createGroup 5) "Сидоров С.С."
  , createStudent 19 (createGroup 10) "Какряцкий А.М."
  ]

in  { groups = groups, students = students, subject = "Конфигурационное управление" }

```
