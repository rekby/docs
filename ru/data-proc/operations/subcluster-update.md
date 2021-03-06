# Изменить подкластер

Для каждого созданного подкластера вы можете:

* [Изменить количество хостов](#change-host-number).

* [Изменить класс хостов](#change-resource-preset).

* [Увеличить размер хранилища](#change-disk-size).


## Изменить количество хостов {#change-host-number}

Вы можете изменить количество хостов в кластерах `DATANODE` и `COMPUTENODE`:

1. В [консоли управления](https://console.cloud.yandex.ru/) выберите каталог с кластером, в котором нужно изменить подкластер.
1. Выберите сервис Data Proc и выберите нужный кластер.
1. Перейдите в раздел **Подкластеры**.
1. Нажмите значок ![image](../../_assets/options.svg) для нужного подкластера и выберите пункт **Изменить**.
1. Введите или выберите нужное количество хостов в поле **Хосты**.
1. Нажмите кнопку **Сохранить изменения**.

Data Proc запустит операцию добавления хостов.


## Изменить класс хостов {#change-resource-preset}

Вы можете изменить вычислительную мощность хостов в отдельном подкластере:

{% list tabs %}

- Консоль управления

    Чтобы изменить [класс хостов](../concepts/instance-types.md) для подкластера:

    1. В [консоли управления](https://console.cloud.yandex.ru/) выберите каталог с кластером, в котором нужно изменить подкластер.
    1. Выберите сервис Data Proc и выберите нужный кластер.
    1. Перейдите в раздел **Подкластеры**.
    1. Нажмите значок ![image](../../_assets/options.svg) для нужного подкластера и выберите пункт **Изменить**.
    1. Выберите нужную платформу и конфигурацию в блоке **Класс хоста**.
    1. Нажмите кнопку **Сохранить изменения**.

    Data Proc запустит операцию изменения подкластера. При этом все хосты изменяемого подкластера будут перезапущены.

{% endlist %}


## Увеличить размер хранилища {#change-disk-size}

Вы можете увеличить размер хранилища, доступного каждому хосту в определенном подкластере.

{% note info %}

Уменьшить размер хранилища на данный момент невозможно. Если это необходимо, пересоздайте подкластер Data Proc.

{% endnote %}

{% list tabs %}

- Консоль управления

    Чтобы изменить размер хранилища для подкластера:

    1. В [консоли управления](https://console.cloud.yandex.ru/) выберите каталог с кластером, в котором нужно изменить подкластер.
    1. Выберите сервис Data Proc и выберите нужный кластер.
    1. Перейдите в раздел **Подкластеры**.
    1. Нажмите значок ![image](../../_assets/options.svg) для нужного подкластера и выберите пункт **Изменить**.
    1. Введите или выберите нужный объем хранилища в блоке **Размер хранилища**.
    1. Нажмите кнопку **Сохранить изменения**.

    Data Proc запустит операцию изменения подкластера.

{% endlist %}