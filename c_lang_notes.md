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
~~~с
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
~~~с
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

выражение case 1: - метка

## ссылки
https://en.cppreference.com/w/c/language.html
