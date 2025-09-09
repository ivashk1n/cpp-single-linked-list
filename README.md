# SingleLinkedList (Односвязный список)

## Описание
Реализация обобщённого односвязного списка на C++ с поддержкой:
- базового итератора (`Iterator`, `ConstIterator`);
- операций вставки, удаления и очистки;
- работы с диапазонами;
- перегрузки операторов сравнения;
- поддержки `initializer_list` и копирования.

Класс написан шаблонным (`template <typename Type>`), поэтому может хранить элементы любого типа.

---

## Основные возможности
- `PushFront(const Type& value)` — вставка элемента в начало списка.
- `PopFront()` — удаление первого элемента списка.
- `InsertAfter(ConstIterator pos, const Type& value)` — вставка элемента после указанной позиции.
- `EraseAfter(ConstIterator pos)` — удаление элемента после указанной позиции.
- `Clear()` — полная очистка списка.
- `GetSize()` — получение количества элементов.
- `IsEmpty()` — проверка, пуст ли список.

---

## Итераторы
Поддерживаются итераторы:
- `Iterator` — изменяемый;
- `ConstIterator` — только для чтения.

Методы для работы с итераторами:
- `begin(), end()` — начало и конец списка;
- `cbegin(), cend()` — константные версии;
- `before_begin(), cbefore_begin()` — позиция перед первым элементом.

---

##Сложность операций

-Вставка/удаление в начало (PushFront, PopFront) — O(1).
-Вставка/удаление после итератора (InsertAfter, EraseAfter) — O(1).
-Очистка (Clear) — O(N).
-Обход через итераторы — O(N).

---

##Особенности

-Используется фиктивный узел (head_) для упрощения вставки перед первым элементом.
-Операции гарантированно оставляют список в корректном состоянии даже при исключениях.
-Совместим со стандартными алгоритмами STL (итераторы forward-iterator).

---

## Пример использования

```cpp
#include <iostream>
#include "single-linked-list.h"

int main() {
    SingleLinkedList<int> list;

    list.PushFront(3);
    list.PushFront(2);
    list.PushFront(1);

    std::cout << "Список: ";
    for (int value : list) {
        std::cout << value << " ";
    }
    std::cout << std::endl;

    list.InsertAfter(list.begin(), 5);

    std::cout << "После вставки: ";
    for (int value : list) {
        std::cout << value << " ";
    }
    std::cout << std::endl;

    list.PopFront();
    std::cout << "После удаления первого элемента: ";
    for (int value : list) {
        std::cout << value << " ";
    }
    std::cout << std::endl;

    return 0;
}
