# Сеть, кластеры и подкластеры

Все подкластеры кластера находятся в одной сети, все хосты каждого подкластера — в определенной подсети этой сети.

На стадии Preview вы не можете назначить хосту кластера публичный IP-адрес. Чтобы подключиться к кластеру Data Proc, создайте виртуальную машину в той же облачной сети. [Подробнее о работе сети в Облаке](../../vpc/).


## Адреса хостов в кластере {#hostname}

При создании хоста в подкластере Data Proc генерирует для него FQDN и IP-адрес. Их можно использовать для доступа к хосту в рамках одной облачной сети.

IP-адрес хоста может меняться в ходе эксплуатации, но FQDN хоста не меняется.

{% note important %}

Когда вы уменьшаете количество хостов в подкластере, сервис самостоятельно выбирает хосты, которые будут удалены. FQDN удаленных хостов перестают работать.

{% endnote %}
