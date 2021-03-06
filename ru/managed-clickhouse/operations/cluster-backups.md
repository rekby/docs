# Управление резервными копиями

Вы можете создавать [резервные копии](../concepts/backup.md) и восстанавливать кластеры из имеющихся резервных копий.

## Создать резервную копию {#create-backup}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  
  2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.
  
  3. Нажмите кнопку **Создать резервную копию**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы создать резервную копию кластера:
  
  1. Посмотрите описание команды CLI для создания резервной копии ClickHouse:
  
      ```
      $ yc managed-clickhouse cluster backup --help
      ```
  
  2. Запросите создание резервной копии, указав имя или идентификатор кластера:
  
      ```
      $ yc managed-clickhouse cluster backup my-ch-cluster
      ```
  
      Имя и идентификатор кластера можно получить со [списком кластеров](cluster-list.md#list-clusters).
  
{% endlist %}

## Восстановить кластер из резервной копии {#restore}

Восстанавливая кластер из резервной копии, вы создаете новый кластер с данными из резервной копии. Если в облаке не хватает [ресурсов](../concepts/limits.md) для создания такого кластера, восстановиться из резервной копии не получится.

Для нового кластера необходимо задать все параметры, обязательные при создании, кроме типа кластера (резервную копию ClickHouse не получится восстановить как кластер PostgreSQL).

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  
  2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.
  
  3. Нажмите значок ![image](../../_assets/dots.svg) для нужной резервной копии, затем нажмите **Восстановить кластер**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы восстановить кластер из резервной копии:
  
  1. Посмотрите описание команды CLI для восстановления кластера ClickHouse:
  
      ```
      $ yc managed-clickhouse cluster restore --help
      ```
  
  2. Получите список доступных резервных копий ClickHouse-кластеров:
  
      ```
      $ yc managed-clickhouse backup list
  
      +--------------------------+----------------------+----------------------+----------------------+
      |            ID            |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
      +--------------------------+----------------------+----------------------+----------------------+
      | c9qlk4v13uq79r9cgcku:... | 2018-11-02T10:08:38Z | c9qlk4v13uq79r9cgcku | 2018-11-02T10:08:37Z |
      | ...                                                                                           |
      +--------------------------+----------------------+----------------------+----------------------+
      ```
  
  3. Запросите создание кластера из резервной копии:
  
      ```
      $ yc managed-clickhouse cluster restore \
             --backup-id c9q22suuefrmrp2lrv9f:20181109T101204 \
             --name mynewch \
             --environment=PRODUCTION \
             --network-name default \
             --host type=clickhouse,zone-id=ru-central1-c,subnet-id=b0rcctk2rvtr8efcch63 \
             --clickhouse-disk-size 20 \
             --clickhouse-disk-type network-nvme \
             --clickhouse-resource-preset s1.nano
      ```
  
      В результате будет создан ClickHouse-кластер со следующими характеристиками:
  
  
  
      - С именем `mynewch`.
      - В окружении `PRODUCTION`.
      - В сети `default-net`.
      - С одним хостом класса `s1.nano` в подсети `b0rcctk2rvtr8efcch63`, в зоне доступности `ru-central1-c`.
      - С базами данных и пользователями из резервной копии.
      - С сетевым SSD-хранилищем объемом 20 ГБ.
  
{% endlist %}

## Получить список резервных копий {#list-backups}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  
  2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить список резервных копий кластеров ClickHouse, доступных в каталоге по умолчанию, выполните команду:
  
  ```
  $ yc managed-clickhouse backup list
  
  +----------+----------------------+----------------------+----------------------+
  |    ID    |      CREATED AT      |  SOURCE CLUSTER ID   |      STARTED AT      |
  +----------+----------------------+----------------------+----------------------+
  | c9qv4... | 2018-10-31T22:01:07Z | c9qv4ql6bd4hfo1cgc3o | 2018-10-31T22:01:03Z |
  | c9qpm... | 2018-10-31T22:01:04Z | c9qpm90p3pcg71jm7tqf | 2018-10-31T22:01:04Z |
  +----------+----------------------+----------------------+----------------------+
  ```
  
{% endlist %}


## Получить информацию о резервной копии {#get-backup}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  
  2. Нажмите на имя нужного кластера и выберите вкладку **Резервные копии**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить данные о резервной копии кластера ClickHouse, выполните команду:
  
  ```
  $ yc yc managed-clickhouse backup get <идентификатор резервной копии>
  ```
  
  Идентификатор резервной копии можно получить со [списком резервных копий](#list-backups).

{% endlist %}

## Задать время начала резервного копирования {#set-backup-window}

{% list tabs %}

- Консоль управления
  
  В консоли управления задать время начала резервного копирования можно только при [изменении кластера](update.md).

- CLI

  Чтобы задать время начала резервного копирования, используйте флаг `--backup-window-start`. Время задается в формате ``ЧЧ:ММ:СС``.

  ```
  $ yc yc managed-clickhouse cluster create \
        --name <имя кластера> \
        --environment <окружение, prestable или production> \
        --network-name <имя сети> \
        --host type=<clickhouse или zookeeper>,zone-id=<зона доступности>,subnet-id=<идентификатор подсети> \
        --resource-preset <класс хоста> \
        --clickhouse-disk-type <network-hdd | network-nvme | local-nvme> \
        --clickhouse-disk-size <размер хранилища в гигабайтах> \
        --user name=<имя пользователя>,password=<пароль пользователя> \
        --database name=<имя базы данных>
        --backup-window-start 10:00:00
  ```
  
  Изменить время начала резервного копирования в существующем кластере можно с помощью команды `update`:

  ```
  $ yc yc managed-clickhouse cluster update \
     --name <имя кластера> \
     --backup-window-start 11:25:00
  ```

{% endlist %}
