# amogus
## 4. Класс std::unordered_map. Внутренняя реализация unordered_map, его основные методы. Сложность поиска, сортировки, удаления элемента, добавления элемента. Пример работы с std::unordered_map

**Unordered map** - ассоциативный контейнер, который содержит пары ключ-значение с уникальными ключами. Поиск, вставка и удаление выполняются за константное время.

### Основные методы

| Метод | Функция |
| --- | --- |
| empty | Проверяет отсутствие элементов в контейнере |
| size | Возвращает количество элементов в контейнере |
| max_size | Возвращает максимально допустимое количество элементов в контейнере |
| clear | Очищает контейнер |
| insert | Вставляет элементы |
| emplace | Конструирует элементы "на месте" и вставляет их начиная с заданной позиции pos |
| emplace_hint | Элементы конструкций на месте использования подсказки |
| erase | Удаляет элементы |
| swap | Обменивает содержимое |
| at | Предоставляет доступ к указанному элементу с проверкой индекса |
| operator[] | Предоставляет доступ к указанному элементу |
| count | Возвращает количество элементов, соответствующих определенному ключу |
| find | находит элемент с конкретным ключом |
| equal_range | возвращает набор элементов для конкретного ключа |
| begin(int) cbegin(int) | возвращает итератор на начало указанного сегмента |
| end(int) cend(int) | возвращает итератор на конец указанного сегмента |
| bucket_count | Возвращает количество bucket'ов |
| max_bucket_count | Возвращает максимальное количество bucket'ов |
| bucket_size | Возвращает количество элементов в конкретном bucket'е |
| bucket | Возвращает bucket для конкретного ключа |
| load_factor | Возвращает среднее количество элементов на bucket |
| max_load_factor | Управляет максимальным средним количеством элементов на bucket |
| rehash | Резервирует количество bucket'ов, не меньшее запрошенного, соответственно перестраивая хэш-таблицу. |
| reserve | Запасает место для, как минимум, указанного числа элементов. Это восстанавливает хэш-таблицу. |

### Пример работы с std::unordered_map:
```cpp
int main()
{
    // Create an unordered_map of three strings (that map to strings)
    std::unordered_map<std::string, std::string> u = {
        {"RED","#FF0000"},
        {"GREEN","#00FF00"},
        {"BLUE","#0000FF"}
    };
 
    std::cout << "Iterate and print keys and values of unordered_map, being explicit with\n"
                 "the type of the iterator, n:\n";
    for( const std::pair<std::string, std::string>& n : u ) {
        std::cout << "Key:[" << n.first << "] Value:[" << n.second << "]\n";
    }
}
```

## 6. Парадигмы ООП. Полиморфизм (статический, динамический). Инкапсуляция. Наследование. Примеры.

Основная идея ООП — что угодно это объект.

**Классы и объекты** — есть шаблоны, через них и описываются классы. Если использовать шаблон, то будет объект, у которого будут свойства класса, которые мы задаём уже индивидуально. 
``
class Car
{
    //Data members
    char name[20];
    int speed;
    int weight;
    
public:
    //Functions
    void brake(){
    }
    void slowDown(){
    }
};
 
int main()
{
   //ford is an object
   Car ford; 
}
``

**Абстракция** — необязательно знать что конкретно происходит, достаточно понимать идею и модель действий. Когда мы пишем деструктор, необязательно чистить каждый байт отдельно, например.
```
~Massiv() // деструктор
    {
		delete[] m_array;
	}
```

**Инкапсуляция** — это процесс объединения данных и кода так, что к нему нет доступа напрямую вне класса. Чтобы получить данные типа private (доступны только классу, в котором определены) и protected(доступны ещё и наследованным), нужны public(доступны всем) функции. В случае определения функции как *extern*, она будет видна в любом файле, скомпилированном вместе с ней. В случае определения функции как *static*, она будет видна только в файле, в котором была определена.
```
#include <iostream>

class Contact
{
private:
    int mobile_number;           // private variable
    int home_number;             // private variable
public:
    Contact()                    // constructor
    {
        mobile_number = 12345678;
        home_number = 87654321;
    }
    void print_numbers()
    {
        std::cout << "Mobile number: " << mobile_number;
        std::cout << ", home number: " << home_number << std::endl;
    }
    void set_mobile_number(int a)
    {
        mobile_number = a;
    }
    void set_home_number(int a)
    {
        home_number = a;
    }
    friend void print_numbers(Contact some_contact);
};

void print_numbers(Contact some_contact)
{
    std::cout << "Mobile number: " << some_contact.mobile_number;
    std::cout << ", home number: " << some_contact.home_number << std::endl;
}
```
**Наследование** — класс может использовать переменные и методы другого класса как свои собственные. Наследование полезно, поскольку оно позволяет структурировать и повторно использовать код, что, в свою очередь, может значительно ускорить процесс разработки. Осторожно — изменения в родительском классе повлияют и на дочерний. Есть 3 типа наследования:

*public* —public и protected данные наследуются без изменения уровня доступа к ним; 
*protected* — все унаследованные данные становятся protected;
*private* — все унаследованные данные становятся private.

В C ++ конструкторы и деструкторы не наследуются. Конструкторы вызываются один за другим иерархически, начиная с базового класса и заканчивая последним производным классом. Деструкторы вызываются в обратном порядке.

Проблема ромба та проблема возникает когда классы B и C наследуют A, а класс D наследует B и C. В случае вызова метода в D неясно какой метод должен быть вызван — метод класса A, B или C.

```
class Device {
    public:
        // constructor
        Device() {
            std::cout << "Device constructor called" << std::endl;
        }
        // destructor
        ~Device() {
            std::cout << "Device destructor called" << std::endl;
        }
};

class Computer: public Device {
    public:
        Computer() {
            std::cout << "Computer constructor called" << std::endl;
        }
        ~Computer() {
            std::cout << "Computer destructor called" << std::endl;
        }
};

class Laptop: public Computer, public Monitor {
    public:
        Laptop() {
            std::cout << "Laptop constructor called" << std::endl;
        }
        ~Laptop() {
            std::cout << "Laptop destructor called" << std::endl;};
};
```
Виртуальное наследование — инструмент для решения проблемы ромба. Базовый класс, наследуемый множественно, определяется виртуальным с помощью ключевого слова virtual.

```
class Device {
    public:
        Device() {
            cout << "Device constructor called" << endl;
        }
        void turn_on() {
            cout << "Device is on." << endl;
        }
};
class Computer: virtual public Device {
    public:
        Computer() {
            cout << "Computer constructor called" << endl;
        }
};
class Monitor: virtual public Device {
    public:
        Monitor() {
            cout << "Monitor constructor called" << endl;
        }
};

class Laptop: public Computer, public Monitor {};
```

**Полиморфизм** — атрибут, который позволяет использовать один и тот же интерфейс при реализации целого класса различных действий. Выбор того, какое именно действие будет совершено, определяется конкретной ситуацией.
```
#include <iostream>
#include <string>
#include <sstream>
#include <cstdlib>

class Unit{
protected:
    int health;
    virtual string getInfo() = 0;
public:
    Unit(int _health)
        :health(_health)
    {}
    virtual void getDamage(int damage) = 0;
friend ostream& operator<<(ostream &out, Unit *a);
friend ostream& operator<<(ostream &out, Unit &a);
};

ostream& operator<<(ostream &out, Unit &a)
{
    out << a.getInfo();
    return out;
}
class Human:public Unit{
public:
    Human(int _health):Unit(_health)
    {}
};

class Soldier:public Human{
private:
    static const int max_health = 100;
protected:
    string getInfo()
    {
        stringstream info;
        info << "Soldier, health = " << health;
        return info.str();
    }
public:
    Soldier():Human(max_health)
    {}
    void getDamage(int damage)
    {
        if (health > damage) {
            health -= damage;
        } else {
            health = 0;
        }
    }
};
```

**Инкапсуляция** - объединение кода и данных таким образом, чтобы защищать данные от непреднамеренного использования и внешнего вмешательства. Основные типы доступа: private, protected, public.

**Наследование** - приобретение одним объектом свойств другого. Объект может унаследовать характерные черты одного объекта и внести в них изменения, характерные только для него.

**Полиморфизм** - использование одно и того же имени для решения схожих, но технически разных задач. Целью полиморфизма является использование одного имени для задания общих для класса действий.

**Статический полиморфизм** реализуется с помощью шаблонов классов. Класс создаётся во время компиляции из шаблона (статическое связывание)

Пример:
```C++
template <typename T>
class Comparison {
public:
    T max(T a, T b) {
        return (a > b) ? a : b;
    }
    T min(T a, T b) {
        return (a < b) ? a : b;
    }
};
```

**Диинамический полиморфизм** реализуется с помощью перезагрузки функций и абстрактного базового класса. Динамическое связывание происходит во время исполнения программы.

Пример:
```C++
class Comparison {
public:
    int max(int a, int b);
    double max(double a, double b);
};
```
