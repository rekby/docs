# CORS-конфигурация бакетов

## Пример конфигурации в виде XML-файла

```
<CORSConfiguration>
    <CORSRule>
        <AllowedOrigin>http://www.example.com</AllowedOrigin>
        <AllowedMethod>PUT</AllowedMethod>
        <AllowedMethod>POST</AllowedMethod>
        <AllowedMethod>DELETE</AllowedMethod>
        <AllowedHeader>*</AllowedHeader>
    </CORSRule>
</CORSConfiguration>
```

Конфигурация позволяет отправлять кросс-доменные запросы с сайта `http://www.example.com` методами PUT, POST, DELETE без ограничений по заголовкам.

## Возможные элементы

Элемент | Описание
----- | -----
`CORSConfiguration` | Корневой элемент конфигурации CORS. Не может содержать более 100 элементов `CORSRule`<br/><br/>Путь: `/CORSConfiguration`.
`CORSRule` | Правило для фильтрации входящих запросов к ресурсу. Каждое правило должно содержать хотя бы по одному элементу `AllowedMethod` и `AllowedOrigin`.<br/><br/>Путь: `/CORSConfiguration/CORSRule`.
`ID` | Уникальный идентификатор правила (не более 255 символов).<br/><br/>Не обязательный. Можно использовать для поиска правила в файле.<br/><br/>Путь: `/CORSConfiguration/CORSRule/ID`.
`AllowedMethod` | HTTP метод (`PUT`, `GET`, `HEAD`, `POST`, `DELETE`), разрешенный для использования при кросс-доменном запросе. Каждый метод следует указать в отдельном элементе. Обязательно указать хотя бы один метод.<br/><br/>Путь: `/CORSConfiguration/CORSRule/AllowedMethod`.
`AllowedOrigin` | Сайт, с которого разрешены кросс-доменные запросы к бакету. Должен быть указан хотя бы один элемент `AllowedOrigin`.<br/><br/>Может содержать не более одного символа `*`. Примеры: `http://*.example.com`, `*`.<br/><br/>Путь: `/CORSConfiguration/CORSRule/AllowedOrigin`.
`AllowedHeader` | Разрешенный заголовок в запросе к объекту. Если разрешенных заголовков несколько, то каждый следует указать в отдельном `AllowedHeader`. В имени заголовка можно использовать один символ `*` для определения шаблона, например `<AllowedHeader>*</AllowedHeader>` означает, что разрешены все заголовки.<br/><br/>Запрос методом [options](../s3/api-ref/object/options.md) содержит заголовок `Access-Control-Request-Headers`. Object Storage сопоставляет заголовки, переданные в `Access-Control-Request-Headers`, с набором `AllowedHeader` и отвечает на `options` списком разрешенных.<br/><br/>Путь: `/CORSConfiguration/CORSRule/AllowedHeader`.
`MaxAgeSeconds` | Время в секундах, в течение которого браузер сохраняет в кэше результат запроса к объекту методом [options](../s3/api-ref/object/options.md).<br/><br/>Путь: `/CORSConfiguration/CORSRule/MaxAgeSeconds`.
`ExposeHeader` | Заголовок, разрешенный к показу в JavaScript-приложении в браузере. Если допустимы несколько заголовков, то укажите каждый из них в отдельном элементе.<br/><br/>В запросе к объекту JavaScript-клиент может оперировать только заголовками, определенными в элементах `ExposeHeader`.<br/><br/>Путь: `/CORSConfiguration/CORSRule/ExposeHeader`.
