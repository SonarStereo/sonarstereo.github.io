# Язык Си

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

## Битовые операции
* сдвиг налево на отрицательное чиcло или на число, большее размера переменной - undefined behaviour
* сдвиг и integral promotion
* интересный алгоритм подсчёта битовых единиц - алгоритм Кернигана

[Weird integral promotions with left shift operator](https://stackoverflow.com/questions/16880187/weird-integral-promotions-with-left-shift-operator) 

[Bit twiddling hacks](https://graphics.stanford.edu/~seander/bithacks.html)

[Слайды - операции с двоичными числами](https://ee.usc.edu/~redekopp/cs356/slides/CS356Unit2_IntegerOperations.pdf)

[Дополнение до 2 (two-complement) - представление отрицательных чисел](https://www.geeksforgeeks.org/digital-logic/twos-complement/)

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

## Массивы
Нельзя инициализировать массив из массива
~~~c
char new_arr[] = old_arr;
~~~

Название массива превращается в указатель на нулевой элемент (array name decays to a pointer). Исключения:
* когда от имени массива берётся sizeof - в этом случае возвращается размер массива
* амперсанд от имени массива возвращает указатель на массив

~~~c
int a[4];
int b[5];

int (* ptr1)[4] = &a; // можно
int (* ptr2)[4] = &b; // нельзя
~~~

Как узнать количество элементов в массиве:
~~~c
int arr[] = { 12, 12, 14, 90, 14, 14, 14 };
int n = sizeof(arr) / sizeof(arr[0]);
~~~

Инициализация массива:
~~~c
// проверено только для локальных массивов
int a1[3] = {4,5,6}; //a1 = {4,5,6}
int a2[3] = {4}; //a2 = {4, 0, 0}
int a3[3] = {}; //a3 = {0,0,0} - даже в C89
~~~
## Указатели 

Адресная арифметика
* указатели можно сравнивать на больше-меньше
* ptr2 - ptr1 - количество элементов соотв типа между указателями 
* складывать нельзя
* можно неявно приводить 0 к любому указателю

Указатель на константу
~~~c
const int a = 10;
const int* ptr = &a; 
*ptr = 5; // нельзя
ptr++;    // можно
~~~

Константный указатель
~~~c
int a = 10;
int *const ptr = &a;  
*ptr = 5; // можно
ptr++;    // нельзя
~~~

Указатель на функцию
общий синтаксис
~~~c
return_type (*pointer_name)(parameter_types);
~~~
примеры указателей
~~~c
int (*fptr)(int, int); // указатель на функцию
int (*farr[])(int, int) = {add, sub, mul, divd}; // массив указателей
~~~

указатель на функцию в качестве аргумента 
~~~c
// A simple addition function
int add(int a, int b) {
    return a + b;
}

// A simple subtraction function
int subtract(int a, int b) {
    return a - b;
}

void calc(int a, int b, int (*op)(int, int)) {
    printf("%d\n", op(a, b));
}

int main() {
  
    // Passing different 
    // functions to 'calc'
    calc(10, 5, add);
  	calc(10, 5, subtract);
    return 0;
}
~~~

## Динамическое выделение памяти

Основные функции
~~~c
int* a0 = (int*)calloc(10, sizeof(int));
int* a = (int*)malloc(2 * sizeof(int));
a = (int*)realloc(a, 3 * sizeof(int));

free(a0);
free(a);
~~~

Быстрое заполнение памяти:
~~~c
//void * memset ( void * ptr, int value, size_t num );
~~~

Можно освободить память даже через другой указатель, даже другого типа!
~~~c
int *ptr = (int *)malloc(256);
double *dp = (double *) ptr;
free(dp);
~~~~

ещё интересный пример

~~~c
int *ptr = (int *)malloc(256);
ptr++;
ptr--;
free(ptr);//ошибка, если не сделать ptr--
~~~~

Задачи:
* скопировать argv
* создать матрицу как одномерный массив, заполнить главную и побочные диагонали

## valgrind

~~~bash
gcc -O0 -g vgcheck.c -o vgcheck
valgrind ./vgcheck
~~~

## Битовые операции

Обмен значений c помощью XOR
~~~c
c = a^b;
a = a^c;
b = b^c;
~~~

~~~c
a = a^b;
b = a^b;
a = b^a;
~~~

нужно помнить, что a XOR a = 0, a XOR 0 = a

## Старшинство операций (precedence & associativity)

PUMA'S REBL TAC

* Primary: (), [], ., ->
* Unary: ++, --, +, - (унарный), !, ~, (type), * (разыменование), & (адрес), sizeof
* Multiplicative: *,/,%
* Additive: +, -
* Shift: >>, <<
* Relational: >, <, >=, <=
* Equality: ==, !=
* Bitwise: &, ^, |
* Logical: &&, || 
* Ternary: ?:
* Assignment: =, +=, -=, *=, /=, %=, &=, ^=, |=, <<=, >>=
* Comma: ,

Ассоциативность справа налево только у unary, ternary, assignment

## Утечки памяти (memory leak)

Процесс запрашивает некоторый кусок памяти, но позже не освобождает его. В итоге, этот кусок памяти не может быть использован другими процессами.

## 📚 Литература
* Б.Керниган, Д.Ритчи *Язык программирования Си*
* S. Harbison, G. Steele *C: A Reference Manual*
* А.М. Робачевский  *Операционная система UNIX*

Cсылки
https://en.cppreference.com/w/c/language.html
