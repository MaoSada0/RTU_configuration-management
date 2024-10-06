# Практика №4

## Задание 1

```python
import json

with open('civgraph.json', 'r') as file:
    dependencies = json.load(file)

with open('Makefile', 'w') as makefile:
    for tech, deps in dependencies.items():
        if deps:
            makefile.write(f'{tech}: {" ".join(deps)}\n')
        else:
            makefile.write(f'{tech}:\n')

        makefile.write(f'\t@echo "{tech} completed"\n\n')
```

![{C99D52DD-5CF8-4712-8833-59D552C06796}](https://github.com/user-attachments/assets/91d77ed7-f6a3-4b74-a14a-195e75919306)
