# Практика 7

## Задание 1

- 11 0 LOAD_FAST 0 (x):
> Команда LOAD_FAST загружает локальную переменную x в стек. В данном случае, индекс переменной 0 соответствует переменной x.

- LOAD_CONST 1 (10):
> Команда LOAD_CONST загружает константу 10 в стек.

- BINARY_MULTIPLY:
> Команда BINARY_MULTIPLY умножает два верхних значения на стеке и помещает результат обратно на стек. Операции выполняются над переменными x и 10, которые были ранее загружены.

- LOAD_CONST 2 (42):
> Команда LOAD_CONST загружает константу 42 в стек.

- BINARY_ADD:
> Команда BINARY_ADD складывает два верхних значения на стеке и помещает результат обратно на стек. Операции выполняются над результатом умножения и константой 42.

- RETURN_VALUE:
> Команда RETURN_VALUE возвращает верхнее значение из стека в качестве результата выполнения функции.

### Итог
```python
result = (x * 10) + 42
return result
```
## Задание 2

- LOAD_CONST 1 (1):
> Загружает константу 1 в стек.

- STORE_FAST 1 (r):
> Сохраняет значение 1 в локальной переменной r. Теперь переменная r инициализирована значением 1.

- LOAD_FAST 0 (n):
> Загружает текущее значение переменной n в стек.

- LOAD_CONST 1 (1):
> Загружает константу 1 в стек.

- COMPARE_OP 4 (>):
> Сравнивает два значения на стеке (n и 1). Проверяет, больше ли n единицы.

- POP_JUMP_IF_FALSE 30:
> Если результат сравнения — False (то есть, n <= 1), то происходит переход к инструкции по адресу 30, которая завершает цикл. Если n > 1, выполнение продолжается.

- LOAD_FAST 1 (r):
> Загружает текущее значение переменной r в стек.

- LOAD_FAST 0 (n):
> Загружает текущее значение переменной n в стек.

- INPLACE_MULTIPLY:
> Умножает значение r на n и сохраняет результат в r.

- STORE_FAST 1 (r):
> Сохраняет результат умножения обратно в переменную r.

- LOAD_FAST 0 (n):
> Загружает текущее значение переменной n в стек.

- LOAD_CONST 1 (1):
> Загружает константу 1 в стек.

- INPLACE_SUBTRACT:
> Вычитает единицу из n, уменьшая его на 1.

- STORE_FAST 0 (n):
> Сохраняет обновлённое значение n обратно в переменную n.

- JUMP_ABSOLUTE 4:
> Безусловный переход на инструкцию по адресу 4, чтобы повторить цикл.

- LOAD_FAST 1 (r):
> Загружает текущее значение переменной r в стек. Это будет результат вычисления факториала.

- RETURN_VALUE:
> Возвращает значение r как результат функции.

### Итог 
> Это функция факториала
``` python
def factorial(n):
    r = 1
    while n > 1:
        r *= n
        n -= 1
    return r
```

## Задание 3

### Java

> Код Java 1
```java
package ru.qq;

public class Main {
    public static void main(String[] args) {
        foo(10);
    }

    private static int foo(int x){
        int result = (x * 10) + 42;
        return result;
    }
}
```
> Байткод Java 1
```bytecode
public class ru.qq.Main {
  public ru.qq.Main();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: invokestatic  #7                  // Method foo:(I)I
       5: pop
       6: return
}
```

> Код Java 2
```java
package ru.qq;

public class Factorial {
    public static void main(String[] args) {
        factorial(2);
    }

    private static int factorial(int n){
        int r = 1;
        while (n > 1) {
            r *= n;
            n -= 1;
        }
        return r;
    }
}

```
> Байткод Java 2
```bytecode
public class ru.qq.Factorial {
  public ru.qq.Factorial();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: iconst_2
       1: invokestatic  #7                  // Method factorial:(I)I
       4: pop
       5: return
}
```
