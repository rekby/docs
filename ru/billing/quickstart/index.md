# Как начать работать с Биллингом

{% include [yandex-account](../_includes/yandex-account.md) %}

Чтобы начать пользоваться Биллингом:

- [Создайте платежный аккаунт](#create_billing_account)
- [Начните знакомство с Яндекс.Облаком](#start)


### Создайте платежный аккаунт {#create_billing_account}

Чтобы создать [платежный аккаунт](../concepts/billing-account.md):

1. Откройте [консоль управления](https://console.cloud.yandex.ru/) Яндекс.Облака.
1. Авторизуйтесь на Яндексе:
    - Если вы авторизованы на Яндексе или в Яндекс.Коннекте через ваши логин и пароль, перейдите к шагу 4.
    - Если вы авторизованы на Яндексе через профиль в социальной сети, [заведите логин и пароль](https://passport.yandex.ru/passport?mode=postregistration&create_login=1) для вашей учетной записи и затем перейдите к шагу 4.
    - Если вы не авторизованы на Яндексе или в Яндекс.Коннекте, нажмите кнопку **Войти**. Затем введите логин и пароль и нажмите кнопку **Войти**.

1. Ознакомьтесь и подтвердите согласие с [Политикой конфиденциальности](https://yandex.ru/legal/confidential/) и [Условиями использования](https://yandex.ru/legal/cloud_termsofuse/).

1. В консоли управления нажмите на ![image](../../_assets/ugly-sandwich.svg) и перейдите в раздел **Биллинг**.

1. Нажмите кнопку **Создать аккаунт** на странице **Список аккаунтов**.

1. Если ваш аккаунт на Яндексе привязан к личному кабинету [Яндекс.Баланса](https://balance.yandex.ru/), в блоке **Плательщики** будет показан список доступных [плательщиков](../concepts/glossary.md). Выберите нужный или перейдите к шагу 7.

1. Задайте имя для нового платежного аккаунта.

1. Выберите тип аккаунта: **Личный аккаунт** или **Бизнес-аккаунт**.

1. Заполните анкету:

   {% list tabs %}

    - Личный аккаунт

       Укажите ваши ФИО и привяжите банковскую карту:
        - Нажмите кнопку **Добавить карту**.
        - Укажите данные карты: 16-значный номер, срок действия, код CVV (с обратной стороны карты).
        - Нажмите кнопку **Привязать**.

        {% include [payment-card-types](../_includes/payment-card-types.md) %}

        {% note info %}

        Средства с привязанной карты могут быть списаны только после [активации платной версии](../operations/activate-commercial.md) и использования сервисов Яндекс.Облака.

        {% endnote %}

        {% include [payment-card-validation](../_includes/payment-card-validation.md) %}

    - Бизнес-аккаунт

      10.1. Выберите способ оплаты:
      - **Банковская карта**.
      <br/>Привяжите корпоративную банковскую карту:
        - Нажмите кнопку **Добавить карту**.
        - Укажите данные карты: 16-значный номер, срок действия, код CVV (с обратной стороны карты).
        - Нажмите кнопку **Привязать**.

        {% include [payment-card-types](../_includes/payment-card-types.md) %}

        {% note info %}

        Привязка банковской карты необходима только для создания платежного аккаунта. Средства с привязанной карты могут быть списаны только после [активации платной версии](../operations/activate-commercial.md). В любой момент после создания платежного аккаунта вы можете [изменить способ оплаты](../operations/change-payment-method.md).

        {% endnote %}

        {% include [yandex-account](../_includes/payment-card-validation.md) %}
      - **Банковский перевод**.
      <br/>После того, как вы нажмете кнопку **Активировать** (шаг 11), платежный аккаунт будет создан в статусе [Не подтвержден](../concepts/billing-account.md#conditions). На вашу почту, указанную в аккаунте Яндекса или Яндекс.Коннекта, будет отправлено письмо с описанием дальнейших действий. Активация платежного аккаунта может занять до трех рабочих дней.

     10.2. Укажите юридическую информацию о вашей организации.

   {% endlist %}

   {% note info %}

   Внимательно заполняйте контактные данные и реквизиты. Эта информация нужна не только для связи с вами, но и для выставления счетов и финансовых документов.

   {% endnote %}

1. Ознакомьтесь с договором. Если вы согласны с условиями, установите опцию **Я ознакомился с Офертой и принимаю ее условия**.

1. Нажмите кнопку **Активировать**.

    {% note info %}

    При создании платежного аккаунта вам автоматически выдается роль _Владелец (owner)_. Изменить владельца или предоставить доступ к платежному аккаунту другому пользователю невозможно. Подробную информацию см. в разделе [Управление доступом](../security/index.md).

    {% endnote %}


### Начните знакомство {#start}

Чтобы начать знакомство с Яндекс.Облаком, воспользуйтесь инструкциями:

   {% include [quickstart-all-no-billing](../../_includes/quickstart-all-no-billing.md) %}
