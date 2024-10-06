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


## Задание 2

```python
import json

with open('civgraph.json', 'r') as file:
    dependencies = json.load(file)

with open('Makefile', 'w') as makefile:
    for tech, deps in dependencies.items():
        completed_file = f'.{tech}.completed'

        if deps:
            makefile.write(f'{completed_file}: {" ".join(f".{dep}.completed" for dep in deps)}\n')
        else:
            makefile.write(f'{completed_file}:\n')

        makefile.write(f'\t@echo "{tech} completed"\n')

        makefile.write(f'\techo. > {completed_file}\n\n')

    makefile.write('civgraph: ' + ' '.join(f'.{tech}.completed' for tech in dependencies) + '\n')
    makefile.write('\t@echo "All tasks completed for civgraph."\n\n')
```

![{43720B6D-B916-428E-959C-2570BE7F7340}](https://github.com/user-attachments/assets/e190cecc-1013-43f9-8c78-14d424d8d9da)
![{7F479A6B-67F0-4307-A04B-191BCDBA6926}](https://github.com/user-attachments/assets/a29f2f07-8e9e-4b1a-80a5-bcaf174b485b)
