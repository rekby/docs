# Управление доступом

Пользователь Яндекс.Облака может выполнять только те операции над ресурсами, которые разрешены назначенными ему ролями.
Пока у пользователя нет никаких ролей, почти все операции ему запрещены.

Чтобы разрешить доступ к ресурсам сервиса Yandex DataLens,
назначьте пользователю нужные роли из приведенного ниже списка. На данный момент роль может быть назначена только на
родительский ресурс (каталог или облако), роли которого наследуются вложенными ресурсами.

{% note info %}

Подробнее о наследовании ролей читайте в разделе [#T](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) документации сервиса Yandex Resource Manager.

{% endnote %}

## Заведение нового пользователя

Чтобы назначить пользователю роль:

1. {% include [grant-role-console-first-steps](../../_includes/iam/grant-role-console-first-steps.md) %}
1. На странице **Пользователи и роли** в правом верхнем углу нажмите кнопку **Добавить пользователя**.
1. Введите электронную почту пользователя в Яндексе.
1. Нажмите кнопку **Добавить**.
1. В строке с нужным пользователем нажмите **Настроить роли**.
1. Выберите каталог и нажмите **Назначить роль** в блоке **Роли в каталогах**.
1. Выберите роль `editor` из списка. Подробнее о ролях в разделе [Роли](../../iam/concepts/access-control/roles.md) документации сервиса Yandex Identity and Access Management.

## Роли

Ниже перечислены все роли, которые учитываются при проверке прав доступа в сервисе Yandex DataLens.

### Сервисные роли

_Сервисные роли_ — роли, дающие доступ к ресурсам определенного сервиса.

{% include [cloud-roles](../../_includes/cloud-roles.md) %}

### Примитивные роли

Примитивные роли можно назначать на любой ресурс в любом сервисе.

Разграничение прав доступа в DataLens реализовано на уровне объектов. Вы можете выдать права на все объекты:

- Папку.
- Подключение.
- Датасет.
- Виджет.
- Дашборд.

#### read

Пользователь с ролью `read` может просматривать созданные дашборды и виджеты.

#### write

Пользователь с ролью `write` может создавать дашборды, виджеты.

Помимо этого роль `write` включает в себя все разрешения роли `read`.

#### admin

Пользователь с ролью `admin` может создавать дашборды и виджеты, утверждать права доступа.

Помимо этого роль `admin` включает в себя все разрешения роли `write`.
