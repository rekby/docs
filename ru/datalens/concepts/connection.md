# Подключение

_Подключение_ содержит информацию о параметрах доступа к источнику данных. Например, IP-адрес хоста БД, порт подключения.
Подключение создается с помощью коннектора. Коннекторы содержат настройки подключения к популярным источникам данных.

## Коннектор

_Коннектор_ — это компонент сервиса DataLens, с помощью которого вы создаете соединение с
 определенным типом БД, API или файлом. С помощью подключения DataLens выполняет запрос данных у источника.

В DataLens доступны следующие типы коннекторов:

- **ClickHouse**
- **PostgreSQL**
- **MySQL**
- **CSV-файл**
- **MS SQL Server**
- **Metrica**
- **Metrica Logs API**
- **AppMetrica**

{% include [connection-note](../../_includes/datalens/datalens-connection-note.md) %}

## Управление доступом

Вы можете настроить права доступа к подключению. Подробнее в разделе [#T](../security/index.md).

#### См. также
- [#T](../operations/connection/create-clickhouse.md)
- [#T](../operations/connection/create-csv.md)
- [#T](../operations/connection/create-mysql.md)
- [#T](../operations/connection/create-postgresql.md)
- [#T](../operations/connection/create-mssql-server.md)
- [#T](../operations/connection/create-metrica-api.md)
- [#T](../operations/connection/create-metrica-logs-api.md)
- [#T](../operations/connection/create-appmetrica.md)
