# Язык Си

## 📚 Литература
* Б.Керниган, Д.Ритчи *Язык программирования Си*
* S. Harbison, G. Steele *C: A Reference Manual*
* А.М. Робачевский  *Операционная система UNIX*

## 🖥️ Компилятор gcc
```console
user:~$ gcc hello.c
user:~$ ls
a.out
user:~$ ./a.out
Hello world!
```

```console
user:~$ gcc hello.c -o hello.out
user:~$ ls
hello.out
user:~$ ./hello.out
Hello world!
```

## История языка Си
* 1969 - язык B для замены ассемблера PDP-7
* 1972 - переименован в C
* 1973 - Unix переписан на C
* 1978 -  The C Programming Language, 1е издание
* 1989 - C89, ANSI C
* 1990 - C90
* 1995 - C95
* 1999 - C99
* 2011 - C11
* 2018 - C17
* 2023 - C23 

## Справочник man
1. Executable programs or shell commands (e.g., ls, man)
2. System calls (functions provided by the kernel)
3. Library functions (e.g., C standard library functions like printf)
4. Special files (devices, etc.)
5. File formats and conventions (e.g., /etc/passwd)
6. Games
7. Miscellaneous (e.g., man-pages, groff)
8. System administration commands (e.g., mount, ifconfig)

```console
user:~$ man 3 printf
user:~$ man 1 printf
user:~$ printf "Hello\n"
```

## Заголовочные файлы
~~~c
#include <stdio.h>
#include "myheader.h"
~~~
Системные заголовочные файлы ищутся в системных папках (/usr/include), пользовательские - сначала в текущей, затем - в папках, определённые с помощью -I, после чего в системных папках

## Функция main
Две формы:
~~~c
int main()
{
  return 0;
}
~~~

~~~c
int main(int argc, char *argv[])
{
  return 0;
}
~~~

## Препроцессор

Определение именованной константы:
~~~c
# define LEN 100 
~~~


## Типы данных
Базовые типы в ANSI C: int, char, short, long, float, double, long double
Модификаторы signed/unsigned можно добавить к int, char, long

В C99 добавлен long long (c вариантами signed/unsigned)

bool - только в C23

строки - массив символов, заканчивающийся '\0' 

## Выражения (expressions)
Характеризуются типом (type) и категорией значения (value category - lvalue/rvalue) 

## lvalue, rvalue
Есть две категории значений: lvalue и rvalue

Выражение lvalue - определяет объект, имеющий тип, отличный от void (идентификаторы, результаты разыменования и т.д.)

Выражение rvalues ﻿- не определяет объект, его значение не имеет объектной сущности или места хранения (константы и т.д.)

Подробный списко lvalues и rvalues [здесь](https://en.cppreference.com/w/c/language/value_category.html)

## Цикл for
~~~c
for (initializationStatement; testExpression; updateStatement) {
    // code block to be executed
}
~~~

* initializationStatement - выполняется один раз, перед выполнением всех итераций;
* testExpression - выполняется перед каждой итерацией;
* updateStatement - выполняется после каждой итерации.

## Функция scanf()
~~~c
#include <stdio.h>

int main() {
    int number;
    int result = scanf("%d", &number);

    if (result == 1) {
        printf("Successfully read an integer: %d\n", number);
    } else if (result == 0) {
        printf("No valid input matched\n");
    } else if (result == EOF) {
        printf("Input stream error\n");
    }

    return 0;
}
~~~

## Посимвольный ввод-вывод (getchar/putchar)
~~~c
int getchar(void);
int putchar(int c);
~~~

## Метки
Сразу после метки не должно быть объявления переменной.
Вот это не сработает:
~~~c
int main()
{
        goto AA;
        printf("shouldn't see this\n");
AA:
        int x=3;
        printf("AA label");

        return 0;
}
~~~
будет ошибка 
a label can only be part of a statement and a declaration is not a statement

А вот так можно:
~~~c
int main()
{
        goto AA;
        printf("shouldn't see this\n");
AA:
        printf("AA label");
        int x=3;

        return 0;
}
~~~
## Оператор goto

Когда допустимо использовать?

## Оператор switch
синтаксис: 
switch ( expression ) statement		

* выражение expression должно приводиться к integer или character
* должно быть не менее case в switch
* выражение case 1: - это метка
* у одного case может быть несколько значений: 
~~~c
case value1, value2: ... 
~~~

пишут, что switch может быть без фигурных скобок; но это не работает, т.к. break не может быть вне цикла, case и default не могут быть вне switch

## Утечки памяти (memory leak)

Процесс запрашивает некоторый кусок памяти, но позже не освобождает его. В итоге, этот кусок памяти не может быть использован другими процессами.

# Cсылки
https://en.cppreference.com/w/c/language.html
