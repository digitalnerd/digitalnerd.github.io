---
layout: post
title: Elasticsearch
---
https://docs.google.com/document/d/1ddJfydl9N93XNfVSZYjRqwv_yI3ljkeuExkbhKIUrbI
### Почему выбирают Elasticsearch?
* высокая производительность индексов
* легко масштабируется
* высокая отказоустойчивость
* хорошо интегрируется с другими системами

### Использование Elasticsearch:
* анализ большого количества данных
* Data Analytics, Machine Learning
* Kibana
* фильтрация и поиск на сайте, когда SQL уже не справляется; но это не замена SQL, а дополнение

### Понятия:
* индекс == БД
* тип == таблица
* документ == запись в таблице

Протокол коммуникации REST API
```bash
curl -XGET http://localhost:9200/blog/_mapping?pretty
```
*Postman

Что такое индекс?
Это некая группировка логических данных.

Что такое документ?
Под документом понимаем какую-то единицу данных.
