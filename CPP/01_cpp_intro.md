# Язык С++

## Перегрузка функций
```c++
#include <cstdio>
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(const char *s);
int print(double dvalue);            
int print(double dvalue, int prec);  // prec = precision.

using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;

    // These calls to print invoke print( char *s ).
    print("This program requires one argument.");
    print("The argument specifies the number of");
    print("digits precision for the second number");
    print("printed.");

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, 3);

    return 0;
}

// Print a string.
int print(const char* s)
{
    cout << "1 " << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << "2 " << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << "3 " << dvalue << endl;
    return cout.good();
}

```

## Смешение кода и данных

## Функции с параметрами по умолчанию
```cpp
// Function declaration with a default argument for 'count'
void printMessage(string message, int count = 1) {
    for (int i = 0; i < count; ++i) {
        cout << message << endl;
    }
}
```

## Исключения
```cpp
#include <iostream>
#include <stdexcept>

void check_value(int value) {
    if (value > 100) {
        throw std::invalid_argument("Value cannot be greater than 100");
    }
    std::cout << "Value is " << value << std::endl;
}

int main() {
    try {
        check_value(256); 
    } catch (const std::invalid_argument& e) {
        std::cerr << "Caught exception: " << e.what() << std::endl;
        return -1;
    }
    return 0;
}
```
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
 
