# Информация об имеющихся кластерах

Вы можете запросить детальную информацию о каждом созданном вами кластере Managed Service for MySQL.


## Получить список кластеров БД в каталоге {#list-clusters}

{% list tabs %}

- Консоль управления
  
  Перейдите на страницу каталога и выберите сервис **Managed Service for MySQL**.

- CLI

  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы запросить список MySQL-кластеров в каталоге по умолчанию, выполните команду:
  
  ```
  $ yc managed-mysql cluster list
  
  +----------------------+--------------+---------------------+--------+---------+
  |          ID          |     NAME     |     CREATED AT      | HEALTH | STATUS  |
  +----------------------+--------------+---------------------+--------+---------+
  | c9q5k4ve76jspng95lav | mysql-test   | 2019-07-09 11:05:25 | ALIVE  | RUNNING |
  | ...                                                                          |
  +----------------------+--------------+---------------------+--------+---------+
  ```
  
{% endlist %}


## Получить детальную информацию о кластере {#get-cluster}

{% list tabs %}

- Консоль управления
  
  1. Перейдите на страницу каталога и выберите сервис **Managed Service for MySQL**.
  1. Нажмите на имя нужного кластера.

- CLI
  
  {% include [cli-install](../../_includes/cli-install.md) %}
  
  {% include [default-catalogue](../../_includes/default-catalogue.md) %}
  
  Чтобы получить информацию о MySQL-кластере, выполните команду:
  
  ```
  $ yc managed-mysql cluster get <имя или идентификатор кластера>
  ```
  
  Идентификатор и имя кластера можно запросить со [списком кластеров в каталоге](#list-clusters).
  
{% endlist %}
