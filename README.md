# Урок 6 Функции для работы с типами данных, агрегатные функции и UDF

Данное домашнее задание выполнено в ClickHouse v24.12.3 установленного в docker container.
Все данные с которыми я работал во время выполнения ДЗ прокинуты в корень текущего репозитория и загружены в git
Если потребуется более детальная проверка ДЗ, контейнер запустится с базами которыми я работал. 

Как запустить контейнера ClickHouse?

``` 
docker compose up --build -d
```

Как попасть в контейнер с ClickHouse?

``` 
docker compose exec clickhouse-server bash
```
Как авторизоваться в ClickHouse?

```
clickhouse-client --user default --password 12345
```

Этапы выполнения ДЗ

### Агрегатные функции

#### Рассчитайте общий доход от всех операций.

![1.png](src%2Fimg%2F1.png)

#### Найдите средний доход с одной сделки.

![2.png](src%2Fimg%2F2.png)

#### Определите общее количество проданной продукции.

![3.png](src%2Fimg%2F3.png)

#### Подсчитайте количество уникальных пользователей, совершивших покупку.

![4.png](src%2Fimg%2F4.png)

### Функции для работы с типами данных

#### Преобразуйте `transaction_date` в строку формата `YYYY-MM-DD`.

![5.png](src%2Fimg%2F5.png)

#### Извлеките год и месяц из `transaction_date`.

![6.png](src%2Fimg%2F6.png)

#### Округлите `price` до ближайшего целого числа.

![7.png](src%2Fimg%2F7.png)

#### Преобразуйте `transaction_id` в строку.

![8.png](src%2Fimg%2F8.png)

#### Извлеките год и месяц из `transaction_date`.
Для разнообразия перейдем в DataGrid

```
SELECT
    formatDateTime(transaction_date, '%Y.%m') AS year_month,
    user_id,
    product_id,
    quantity,
    price
FROM
    transactions
limit 5;
```
![9.png](src/img/9.png)
