# Управление хостами кластера

Вы можете добавлять и удалять хосты кластера, а также управлять настройками ClickHouse для отдельных кластеров.

{% note important %}

На данный момент невозможно как добавить хост к кластеру из одного хоста, так и уменьшить количество хостов в кластере до 1. Решение о том, что данные в ClickHouse-кластере должны реплицироваться, необходимо принять при создании кластера.

{% endnote %}


## Получить список хостов в кластере {#list-hosts}

{% list tabs %}

- Консоль управления

  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.

  2. Нажмите на имя нужного кластера, затем выберите вкладку **Хосты**.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  Чтобы получить список баз данных в кластере, выполните команду:

  ```
  $ yc managed-clickhouse host list
       --cluster-name=<имя кластера>

  +----------------------------+--------------+---------+--------+---------------+
  |            NAME            |  CLUSTER ID  |  ROLE   | HEALTH |    ZONE ID    |
  +----------------------------+--------------+---------+--------+---------------+
  | rc1b...mdb.yandexcloud.net | c9qp71dk1... | MASTER  | ALIVE  | ru-central1-b |
  | rc1c...mdb.yandexcloud.net | c9qp71dk1... | REPLICA | ALIVE  | ru-central1-c |
  +----------------------------+--------------+---------+--------+---------------+
  ```

  Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md#list-clusters).


- API

  Получить список хостов кластера можно с помощью метода [listHosts](../api-ref/Cluster/listHosts.md).

{% endlist %}


## Добавить хост {#add-host}

Количество хостов в кластерах Managed Service for ClickHouse ограничено квотами на количество CPU и объем памяти, которые доступны кластерам БД в вашем облаке. Чтобы проверить используемые ресурсы, откройте страницу [Квоты](https://console.cloud.yandex.ru/cloud?section=quotas) и найдите блок **Yandex Managed Service for ClickHouse**.

{% list tabs %}

- Консоль управления

  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  1. Нажмите на имя нужного кластера и перейдите на вкладку **Хосты**.
  1. Нажмите кнопку **Добавить хост**.

  1. Укажите параметры хоста:

      * зону доступности;

      * подсеть (если нужной подсети в списке нет, [создайте ее](../../vpc/operations/subnet-create.md));

      * выберите опцию **Публичный доступ**, если хост должен быть доступен извне Облака.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  Чтобы добавить хост в кластере:

  1. Запросите список подсетей кластера, чтобы выбрать подсеть для нового хоста:

      ```
      $ yc vpc subnet list

      +-----------+-----------+------------+---------------+------------------+
      |     ID    |   NAME    | NETWORK ID |     ZONE      |      RANGE       |
      +-----------+-----------+------------+---------------+------------------+
      | b0cl69... | default-c | enp6rq7... | ru-central1-c | [172.16.0.0/20]  |
      | e2lkj9... | default-b | enp6rq7... | ru-central1-b | [10.10.0.0/16]   |
      | e9b0ph... | a-2       | enp6rq7... | ru-central1-a | [172.16.32.0/20] |
      | e9b9v2... | default-a | enp6rq7... | ru-central1-a | [172.16.16.0/20] |
      +-----------+-----------+------------+---------------+------------------+
      ```

      Если нужной подсети в списке нет, [создайте ее](../../vpc/operations/subnet-create.md).

  1. Посмотрите описание команды CLI для добавления хостов:

     ```
     $ yc managed-clickhouse host add --help
     ```

  1. Выполните команду добавления хоста:

     ```
     $ yc managed-clickhouse host add
          --cluster-name <имя кластера>
          --host zone-id=<зона доступности>,subnet-id=<ID подсети>
     ```

     Managed Service for ClickHouse запустит операцию добавления хоста.

     Идентификатор подсети необходимо указать, если в зоне доступности больше одной подсети, в противном случае Managed Service for ClickHouse автоматически выберет единственную подсеть. Имя кластера можно запросить со [списком кластеров в каталоге](cluster-list.md#list-clusters).


- API

  Добавить хост в кластер можно с помощью метода [addHosts](../api-ref/Cluster/addHosts.md).

{% endlist %}


## Удалить хост {#remove-host}

Вы можете удалить хост из ClickHouse-кластера, если в кластере 3 и более хостов.

{% list tabs %}

- Консоль управления

  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.

  2. Нажмите на имя нужного кластера и выберите вкладку **Хосты**.

  3. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) в строке нужного хоста и выберите пункт **Удалить**.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  Чтобы удалить хост из кластера, выполните команду:

  ```
  $ yc managed-clickhouse host delete <имя хоста>
       --cluster-name=<имя кластера>
  ```

  Имя хоста можно запросить со [списком хостов в кластере](#list-hosts), имя кластера — со [списком кластеров в каталоге](cluster-list.md#list-clusters).


- API

  Удалить хост можно с помощью метода [deleteHosts](../api-ref/Cluster/deleteHosts.md).

{% endlist %}
