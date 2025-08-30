# Заметки по языку Си

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
## Функция main
~~~c
int main()
{
  return 0;
}
~~~
## выражения (expressions)
Характеризуются типом (type) и категорией значения (value category - lvalue/rvalue) 

## lvalue, rvalue
Есть две категории значений: lvalue и rvalue

Выражение lvalue - определяет объект, имеющий тип, отличный от void (идентификаторы, результаты разыменования и т.д.)

Выражение rvalues ﻿- не определяет объект, его значение не имеет объектной сущности или места хранения (константы и т.д.)

Подробный списко lvalues и rvalues [здесь](https://en.cppreference.com/w/c/language/value_category.html)

## метки
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

## switch
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

## ссылки
https://en.cppreference.com/w/c/language.html
