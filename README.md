# om_api

# Установка библиотеки
## Установка пакета Windows
```
pip install om_api
```
## Обновление пакета Windows
```
pip install --upgrade om_api
```
## Импорт библиотеки в Python коде
```python
from om_api import om_api
```

Это библиотека с набором функций для работы с Optomacros API
В библиотеке есть функции:
- [make_request](#make_request)
- [DataFrame_to_List](#DataFrame_to_List)
- [get_properties](#get_properties)
- [get_list](#get_list)
- [get_parents](#get_parents)
- [get_items](#get_items)
- [add_item_to_list](#add_item_to_list)
- [change_properties](#change_properties)
- [add_item_with_properties](#add_item_with_properties)
- [filter_list_by_property](#filter_list_by_property)

## make_request
```
make_request(request_type: str, url: str, coockie: dict, param: dict = ..., data: dict = ...)
```

- `request_type` метод запроса, реализованы методы `get`, `post`
- `url` адрес к которому мы будем обращаться в формате строки https://***/api/v1/service/{название сервиса}
- `coockie` {'token' : "ваш токен"}
    - Времненный токен можно достать нажав `f12` в браузере и в cookie будет храниться ваш токен
- `param` {'название параметра':'значение параметра'}, параметры, которые мы хотим передать в запросе
- `data` {'':''} данные которые мы передаем с запрсом

## DataFrame_to_List
```
DataFrame_to_List(data)
```

Функция преобразования объекта класса DataFrame в список списков
Первый список будет содержать заголовки
Каждый последуйщий список будет содержать значения

## get_properties
```
get_properties(list_name: str, url: str, cookie: dict)
```

Функция возвращает все свойства справочника списком

## get_list
```
get_list(list_name: str, url: str, cookie: dict)
```

Функция возвращает справочник в виде DataFrame

## get_parents
```
get_parents(list_name: str, url: str, cookie: dict)
```

Функия возвращает всех парентов в справочнике списком

## get_items
```
get_items(list_name: str, url: str, cookie: dict, parent: str = ...)
```

Функция возвращает список всех эллементов справочника не являющиеся парентами другим эллементам.
- `parent` Опциональный параметр позволяет вывести элементы под определенным парентом

## add_item_to_list
```
add_item_to_list(list_name: str, item_name: str, url: str, cookie: dict, parent: str= ...)
```

Функция позволяет добавлять эллемент в справочник.
- `parent` Опциональный параметр позволяет создать эллемент под определенным парентом

## change_properties
```
change_properties(list_name: str, item_name: str, properties: dict, url: str, cookie: dict, parent: str = ...)
```

Функция позволяет изменить свойства эллемента справочника.

## add_item_with_properties
```
add_item_with_properties(list_name: str, item_name: str, properties: dict, url: str, cookie: dict, parent: str = ...)
```

Объединение функций [add_item_to_list](#add_item_to_list) и [change_properties](#change_properties) позволяет создавать эллемент с заполнением его параметров
## filter_list_by_property
```
filter_list_by_property(list_name: str, property_name: str, property_value: str, url: str, cookie: str)
```

Функция фильтрует справочник по одному свойству с заданным значением.
Возвращает DataFrame