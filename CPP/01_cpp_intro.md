# Язык С++

## История

* разработчик - Б.Страуструп (1979)
*  "С с классами"
* процедурное, объектно-ориентированное и обобщённое программирование
* cовместим с С лишь частично

Стандарты С++:    
* C++98
* C++03
* C++11
* C++14
* C++17
* C++20
* С++23

## Мелкие различия Си и Си++

Новые ключевые слова:
```cpp
class
virtual
template
```

С++ запрещает объявлять функции без возвращаемого значения:
```c
f()
{
    printf("Hello");    
}
```

Новые заголовочные файлы:

```сpp
#include <iostream>
```


Ввод-вывод:
* С: функции printf(), scanf();
* C++: объекты cout, cin

```cpp
    int a = 24;
    cout << "Value of "  << a;
```

Ссылочный тип данных:
```cpp
int &x;
```

## Объектно-ориентированное программирование

```c
class MyClass {
public:
    int x;

    void set_x(int arg) {
       x = arg;
    }
} ;
```

## Управление памятью

Динамическое выделение памяти:   
* С: функции malloc(), free();
* C++: операторы new, delete

```cpp
int *a = new int;
int *b = new int[10];
...
delete a;
delete[] b;
```


## Ссылочный тип данных

Cсылка - псевдоним (alias) переменной

```cpp
int    i;
int&    r = i;
```

Передача параметров по ссылке:
```cpp
void swap(int &x, int &y) {
    int z = x;
    x = y;
    y = z;
}
...
int a=2, b=4;
swap(a,b);
```

## Пространства имён

пример:
```c
namespace N{
    int f() {print("Hello");}
    } 
```

💡 точка с запятой после описания namespace не ставится

вызов функции f():
```c
N::f() ;
```

using для одной функции:
```c
using std::cout;
```

вложение пространств, описание члена пространства снаружи:
```cpp
// пример с cppreference.com

namespace Q
{
    namespace V   // V is a member of Q, and is fully defined within Q
    { // namespace Q::V { // C++17 alternative to the lines above
        class C { void m(); }; // C is a member of V and is fully defined within V
                               // C::m is only declared
        void f(); // f is a member of V, but is only declared here
    }
 
    void V::f() // definition of V's member f outside of V
                // f's enclosing namespaces are still the global namespace, Q, and Q::V
    {
        extern void h(); // This declares ::Q::V::h
    }
 
    void V::C::m() // definition of V::C::m outside of the namespace (and the class body)
                   // enclosing namespaces are the global namespace, Q, and Q::V
    {}
}

```


вложение пространств, описание члена пространства снаружи
```cpp
// пример с cppreference.com
namespace Q
{
    namespace V   // V is a member of Q, and is fully defined within Q
    { // namespace Q::V { // C++17 alternative to the lines above
        class C { void m(); }; // C is a member of V and is fully defined within V
                               // C::m is only declared
        void f(); // f is a member of V, but is only declared here
    }
 
    void V::f() // definition of V's member f outside of V
                // f's enclosing namespaces are still the global namespace, Q, and Q::V
    {
        extern void h(); // This declares ::Q::V::h
    }
 
    void V::C::m() // definition of V::C::m outside of the namespace (and the class body)
                   // enclosing namespaces are the global namespace, Q, and Q::V
    {}
}

```

## Пространство имён `std`

* функции стандартной библиотеки погружены в пространство `std`
* чтобы не писать каждый раз **std::имя_функции* можно использовать директиву `using`

директива `using` для пространства имён целиком:
```c
using namespace std ;
```

директива `using` для одной функции
```c
using namespace std::cout ;
```



## Литература

* Б. Страуструп "Язык программирования C++"
* А.В. Столяров "Введение в язык Си++"
* cppreference.com
* learncpp.com
 
