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
