# Вопросы о ClickHouse

#### Почему стоит использовать ClickHouse в Managed Service for ClickHouse, а не собственную установку на виртуальной машине? {#clickhouse-advantages-vm}

Managed Service for ClickHouse автоматизирует рутинное обслуживание БД:

* быстрое развертывание БД с необходимыми доступными ресурсами;

* резервное копирование данных;

* регулярное обновление ПО;

* обеспечение отказоустойчивости кластеров БД;

* мониторинг и статистика использования БД.


#### Когда стоит использовать ClickHouse вместо PostgreSQL? {#clickhouse-advantages-pg}

ClickHouse поддерживает только добавление и чтение данных, так как предназначен прежде всего для аналитики (OLAP). В остальных случаях, скорее всего, удобнее использовать PostgreSQL.


#### Можно ли подключаться к отдельным хостам ClickHouse? {#connect-node}

Да. Подключиться к хостам ClickHouse-кластера можно с помощью шифрованного соединения:

* Через [HTTPS-интерфейс](https://clickhouse.yandex/docs/ru/interfaces/http_interface/), порт 8443.

* Через [клиент командной строки](https://clickhouse.yandex/docs/ru/interfaces/cli/), порт 9440.


Подключение по SSH не поддерживается.


#### Как загружать данные в ClickHouse? {#load-data}

Используйте запрос INSERT, описанный в [документации ClickHouse](https://clickhouse.yandex/docs/ru/query_language/queries.html#insert).


#### Как загрузить в ClickHouse очень большое количество данных? {#loadalot}

Используйте [CLI](https://clickhouse.yandex/docs/en/interfaces/cli/) для эффективного сжатия данных при передаче (рекомендуемая частота — не больше 1 команды INSERT в секунду).

Перенос данных с физических носителей пока не поддерживается.


#### Что случится с кластером, если выйдет из строя одна из нод? {#node-out}

Кластеры БД состоят минимум из 2 реплик, поэтому при потере одной ноды кластер продолжит работу.

Данные могут потеряться только если вышла из строя нода с [нереплицируемой таблицей](https://clickhouse.yandex/docs/ru/table_engines/replication/).


#### Можно ли развернуть кластер БД ClickHouse в нескольких зонах доступности? {#multiple-az}

Да. Кластер БД может состоять из хостов, расположенных как в разных зонах, так и в разных регионах доступности.


#### Как проводится резервное копирование для БД ClickHouse? {#backup}

Резервные копии создаются каждые 24 часа и хранятся 7 дней после создания. Восстановить данные можно только на момент создания копии.


#### Как устроена репликация для ClickHouse? {#zookeeper-access}

Для репликации используется ZooKeeper. Managed Service for ClickHouse создает отдельный кластер ZooKeeper для каждого кластера ClickHouse.

Для пользователей Облака доступ к ZooKeeper и его настройка недоступны.


#### Почему кластер ClickHouse занимает на 3 хоста больше, чем должен?

При создании кластера ClickHouse из 2 и более хостов Managed Service for ClickHouse автоматически создает кластер из 3 хостов ZooKeeper для управления репликацией и отказоустойчивостью. Эти хосты учитываются в расчете использованной [квоты ресурсов](https://console.cloud.yandex.ru/cloud?section=quotas) в облаке и в расчете стоимости кластера. По умолчанию хосты ZooKeeper создаются с минимальным [классом хостов](../concepts/instance-types.md).

Подробнее об использовании ZooKeeper см. [документацию ClickHouse](https://clickhouse.yandex/docs/ru/operations/table_engines/replication/).
