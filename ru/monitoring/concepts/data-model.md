# Модель данных

Данные в сервисе Yandex Monitoring хранятся в виде [временных рядов](https://en.wikipedia.org/wiki/Time_series).

## Метрики
_Метрика_ — это временной ряд, который показывает изменение какой-либо величины во времени. Например, состояние ресурса
одного из сервисов Яндекс.Облака: количество занятого места на диске, скорость передачи данных по сети и т. д.
Для идентификации метрик используются текстовые метки.

### Метки
_Метка_ — характеристика метрики в формате `ключ: "значение"`. Каждая метрика идентифицируется неупорядоченным набором меток. Обычно в качестве метки используется параметр, который принимает ограниченное множество значений. Например, код состояния HTTP, тип выполняющихся процедур в базе данных и т. д.

Метки бывают обязательные и дополнительные. Список обязательных меток:

- `project` — идентификатор облака, в котором находится ресурс.
- `cluster` — идентификатор каталога, в котором находится ресурс.
- `service` — указывает на сервис Яндекс.Облака, которому принадлежит ресурс. Например, `compute` или `managed-postgresql`.

{% note important %}

При загрузке пользовательских метрик необходимо записать значение `custom` в метку `service`.

{% endnote %}

### Типы метрик
В сервисе Yandex Monitoring есть следующие типы метрик:

Тип | Описание
----- | -----
`DGAUGE` | Числовой показатель. Показывает значение метрики в определенный момент времени. Например, количество занятой оперативной памяти
`RATE` | Производная. Показывает изменение значения метрики во времени. Например, количество запросов в секунду

### Запросы

Перечисляя метки и их значения, можно строить запросы для выборки набора метрик и отображения их на графике. В качестве значений меток могут использоваться шаблоны.

В сервисе Yandex Monitoring доступны следующие шаблоны:

Синтаксис | Описание
----- | -----
`label="*"` | Выводит все метрики с указанной меткой. Например, запрос `host="*"` выведет все метрики, у которых есть метка `host`.
`label="glob"` | Выводит все метрики, значение метки которого удовлетворяет [glob-выражению](https://ru.wikipedia.org/wiki/Шаблон_поиска):<br/><br/>`*` — любое количество символов (в том числе отсутствие). Например, `name="folder*"` выведет все метрики, у которых значение метки `name` начинается с префикса `folder`.<br/><br/>`?` — один произвольный символ. Например, `name="metric?"` выведет все метки, у которых есть в значении есть один символ после `metric`<br/><br/>`|` — все указанные варианты. Например,  `name="metric1|metric2"` — две метрики, со значениями метки `metric1` и `metric2`.

Пример запроса метрики можно увидеть в разделе [#T](../operations/chart/create-query.md).

#### См. также
- [#T](visualization/index.md)

