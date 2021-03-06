# yc

Интерфейс командной строки поможет вам взаимодействовать с сервисами Яндекс.Облака.

{% note important %}

Список команд может отличаться в зависимости от версии YC CLI.

{% endnote %}

#### Использование команды

Синтаксис:

`yc <group|command>`

#### Команды

- `yc init` — инициализация CLI.
- `yc version` — вывод версии YC CLI.
- `yc help` — вывод справки о YC CLI.

#### Управление YC CLI

- `yc operation` — [управление операциями](manage-yc/operation.md).
- `yc config` — [управление конфигурациями YC CLI](manage-yc/config.md).
- `yc components` — [управление установленными компонентами](manage-yc/components.md).

#### Управление сервисами

- `yc iam` — [управление ресурсами Yandex Identity and Access Management](manage-services/iam.md).
- `yc resource-manager` — [управление ресурсами Yandex Resource Manager](manage-services/resource-manager.md).
- `yc compute` — [управление ресурсами Yandex Compute Cloud](manage-services/compute.md).
- `yc vpc` — [управление ресурсами Yandex Virtual Private Cloud](manage-services/vpc.md).
- `yc managed-clickhouse` — [управление ClickHouse](manage-services/managed-clickhouse.md).
- `yc managed-mongodb` — [управление MongoDB](manage-services/managed-mongodb.md).
- `yc managed-postgresql` — [управление PostgreSQL](manage-services/managed-postgresql.md).
