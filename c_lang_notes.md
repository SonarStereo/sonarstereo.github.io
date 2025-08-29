# Заметки по языку Си

## Функция main
~~~c
int main()
{
  return 0;
}
~~~

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

выражение expression должно приводиться к integer или character

должно быть не менее case в switch

у одного case может быть несколько значений: 
~~~c
case value1, value2: ... 
~~~

break: This is used to exit the switch statement once a case is executed. Without break, the program will continue executing the subsequent cases (this is called "fall through").
default: This block of code is executed if none of the case values match the expression. It is optional to add this block.
выражение case 1: - метка

пишут, что switch может быть без фигурных скобок; но это не работает, т.к. break не может быть вне цикла, case и default не могут быть вне switch

## ссылки
https://en.cppreference.com/w/c/language.html
