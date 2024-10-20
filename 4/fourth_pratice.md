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

## Задание 3

```python
import json
import os

COMPLETED_TASKS_FILE = "records.txt"

def load_completed_tasks():
    return set(open(COMPLETED_TASKS_FILE).read().splitlines()) if os.path.exists(COMPLETED_TASKS_FILE) else set()

def save_completed_tasks(tasks):
    with open(COMPLETED_TASKS_FILE, 'w') as f:
        f.write('\n'.join(tasks))

def clean():
    try:
        os.remove(COMPLETED_TASKS_FILE)
        print("Completed tasks have been cleaned.")
    except FileNotFoundError:
        print("No tasks to clean.")

def generate_makefile(civgraph, target):
    to_visit = [target]
    result = []
    visited = set()
    completed_tasks = load_completed_tasks()

    while to_visit:
        tech = to_visit.pop()
        if tech in visited or tech in completed_tasks:
            continue

        visited.add(tech)
        to_visit.extend(civgraph.get(tech, []))
        result.append(tech)

    new_tasks = [task for task in result if task not in completed_tasks]
    if new_tasks:
        print("\n".join(new_tasks))
        completed_tasks.update(new_tasks)
        save_completed_tasks(completed_tasks)

def load_civgraph(file_path):
    with open(file_path) as f:
        return json.load(f)

if __name__ == '__main__':
    civgraph = load_civgraph('civgraph.json')
    action = input('Enter action (make/clean): ').strip().lower()

    if action == 'clean':
        clean()
    elif action == 'make':
        target = input('Enter the target technology: ').strip()
        generate_makefile(civgraph, target)
    else:
        print("Invalid action. Please enter 'make' or 'clean'.")
```
![{A856A5C8-6332-4B81-9052-D170BA8DECFF}](https://github.com/user-attachments/assets/9fef55bc-da21-4aae-a4e3-3b9ca885fbfd)
![{34B7691F-EE82-4F02-8AE4-703F9D636C31}](https://github.com/user-attachments/assets/08b1ec10-96a6-4f70-92bb-96b9e0246fc7)
