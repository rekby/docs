# Управление базами данных

Вы можете добавлять и удалять базы данных, а также просматривать информацию о них.

## Получить список баз данных в кластере {#list-db}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for PostgreSQL**.
  1. Нажмите на имя нужного кластера, затем выберите вкладку **Базы данных**.
  
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить список баз данных в кластере, выполните команду:
  
  ```
  $ yc managed-postgresql database list
       --cluster-name=<имя кластера>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
  
- API
  
  Получить список баз данных кластера можно с помощью метода [list](../api-ref/Database/list.md).
  
{% endlist %}

## Создать базу данных {#add-db}

Количество баз данных в кластере неограниченно.

{% note important %}

По умолчанию базы данных создаются с настройками сравнения и сортировки строк `LC_COLLATE=C` и `LC_CTYPE=C`.
Это позволяет PostgreSQL эффективнее выполнять запросы со строковыми типами данных, но может
работать неочевидным образом, например, с кириллицей.

Подробнее эти настройки освещены в [документации PostgreSQL](https://www.postgresql.org/docs/current/collation.html).

{% endnote %}

 После создания базы данных настройки сравнения и сортировки строк для базы в целом поменять нельзя.
 Чтобы создать базу с нужными значениями этих настроек, используйте, например, флаги `--lc-collate`
 и `--lc-type` в команде CLI `yc managed-postgresql database create`.

 После создания БД вы можете задавать настройки сравнения и сортировки для столбцов при создании и изменении
 таблиц. Подробнее читайте в  [документации PostgreSQL](https://www.postgresql.org/docs/current/sql-createtable.html).

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for PostgreSQL**.
  1. Нажмите на имя нужного кластера.
  1. Если владельцем новой базы данных должен стать еще не существующий пользователь, [создайте его](cluster-users.md#adduser).
  1. Выберите вкладку **Базы данных**.
  1. Нажмите кнопку **Добавить**.
  1. Введите имя для базы данных и выберите ее владельца.
  
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы создать базу данных в кластере:
  
  1. Посмотрите описание команды CLI для создания БД:
  
     ```
     $ yc managed-postgresql database create --help
     ```
  
  1. Запросите список пользователей кластера, чтобы выбрать владельца новой базы данных:
  
     ```
     $ yc managed-postgresql user list
          --cluster-name <имя кластера>
     ```
  
     Если нужного пользователя в списке нет, [создайте его](cluster-users.md#adduser).
  
  1. Выполните команду создания БД:
  
     ```
     $ yc managed-postgresql database create <имя базы данных>
          --cluster-name <имя кластера>
          --owner <имя пользователя-владельца>
     ```
  
     Managed Service for PostgreSQL запустит операцию создания базы данных.
  
  Имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
  
- API
  
  Создать новую базу данных в кластере можно с помощью метода [create](../api-ref/Database/create.md).
  
{% endlist %}

## Удалить базу данных {#remove-db}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for PostgreSQL**.
  1. Нажмите на имя нужного кластера и выберите вкладку **Базы данных**.
  1. Нажмите значок ![image](../../_assets/vertical-ellipsis.svg) в строке нужной БД и выберите пункт **Удалить**.
  
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы удалить базу данных, выполните команду:
  
  ```
  $ yc managed-postgresql database delete <имя базы данных>
       --cluster-name=<имя кластера>
  ```
  
  Имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
  
- API
  
  Удалить базу данных можно с помощью метода [delete](../api-ref/Database/delete.md).
  
{% endlist %}
