# Информация об имеющихся кластерах

Вы можете запросить детальную информацию о каждом созданном вами кластере Managed Service for ClickHouse.


## Получить список кластеров БД в каталоге {#list-clusters}

{% list tabs %}

- Консоль управления
  
  Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы запросить список ClickHouse-кластеров в каталоге по умолчанию, выполните команду:
  
  ```
  $ yc managed-clickhouse cluster list
  
  +----------------------+---------------+-----------------------------+--------+---------+
  |          ID          |     NAME      |         CREATED AT          | HEALTH | STATUS  |
  +----------------------+---------------+-----------------------------+--------+---------+
  | c9wlk4v14uq79r9cgcku | mypg          | 2018-11-02T10:04:14.645214Z | ALIVE  | RUNNING |
  | ...                                                                                   |
  +----------------------+---------------+-----------------------------+--------+---------+
  ```
  
{% endlist %}


## Получить детальную информацию о кластере {#get-cluster}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for ClickHouse**.
  1. Нажмите на имя нужного кластера.
  
- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить информацию о ClickHouse-кластере, выполните команду:
  
  ```
  $ yc managed-clickhouse cluster get <имя или идентификатор кластера>
  ```
  
  Идентификатор и имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
{% endlist %}
