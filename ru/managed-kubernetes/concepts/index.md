# Взаимосвязь ресурсов сервиса

[Kubernetes](https://Kubernetes.io) — система для управления контейнерными приложениями. Kubernetes предоставляет механизмы взаимодействия с кластером, с помощью которых осуществляется автоматизации развертывания, масштабирования и управления приложениями в контейнерах.

Основная сущность, которой оперирует сервис — _кластер Kubernetes_.

## Кластер Kubernetes {#kubernetes-cluster}

Кластер Kubernetes состоит из мастера и одной или нескольких групп узлов. Мастер отвечает за управление кластером Kubernetes. На узлах запускаются контейнеризованные приложения пользователя.

Сервис полностью управляет мастером, а также следит за состоянием и работоспособностью группы узлов. Пользователь может управлять узлами напрямую, а также настраивать кластер Kubernetes с помощью консоли управления Облака, CLI и API Managed Service for Kubernetes.

{% note important %}

Группам узлов Kubernetes требуется доступ в интернет для скачивания образов и компонентов.
Предоставить доступ в интернет можно следующими способами:
- Назначить каждому узлу в группе [публичный IP адрес](../../vpc/concepts/address.md#publichnye-adresa).
- [Настроить виртуальную машину в качестве NAT-шлюза](../operations/nat-instance.md). В таком случае будет использован только один публичный IP-адрес — тот, который присвоен шлюзу.

{% endnote %}

При работе с кластером Kubernetes на инфраструктуре Яндекс.Облака задействуются следующие ресурсы:

| Ресурс | Количество | Комментарий |
|----|:---:|----|
|Подсеть |2| Kubernetes резервирует диапазоны IP-адресов, которые будут использоваться для подов и сервисов. |
|Таблица маршрутизации |1|Используется для маршрутизации трафика между подами внутри кластера Kubernetes.|
|Публичный IP |N|В количество N входит:</br> - **Один** публичный IP для NAT-шлюза.</br> - Публичный IP **каждому** узлу в группе, если вы используете технологию one-to-one NAT.</br> |

### Мастер {#master}

_Мастер_ — узел, который управляет кластером Kubernetes.

Мастер запускает управляющие процессы Kubernetes, которые включают сервер Kubernetes API, планировщик и контроллеры основных ресурсов. Жизненный цикл мастера управляется сервисом при создании или удалении кластера Kubernetes. Мастер отвечает за глобальные решения, которые выполняются на всех узлах кластера Kubernetes. Они включают в себя планирование рабочих нагрузок, таких как контейнерные приложения, управление жизненным циклом рабочих нагрузок и масштабированием.

### Группа узлов {#node-group}

_Группа узлов_ — группа виртуальных машин с одинаковой конфигурацией в кластере Kubernetes, на которых запускаются пользовательские контейнеры.

#### Конфигурация {#config}

При создании группы узлов пользователь может сконфигурировать следующие параметры виртуальных машин:
- Тип виртуальной машины.
- Тип и количество ядер(vCPU).
- Объем памяти (RAM) и диска.

В одном кластере можно создавать группы с разными конфигурациями и размещать их в разных [зонах доступности](../../overview/concepts/geo-scope.md).

#### Подключение к узлам группы {#node-connect-ssh}

К узлам группы можно подключаться по SSH. О том, как это сделать, читайте в разделе [Подключиться к узлу по SSH](../operations/node-connect-ssh.md).
