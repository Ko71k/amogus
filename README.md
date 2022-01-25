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