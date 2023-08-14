# Домашнее задание к занятию «SQL. Часть 1»

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### Решение 1

Написан запрос:

```sql
SELECT DISTINCT district
FROM sakila.address
WHERE district LIKE 'K%a' 
AND district NOT LIKE '% %';
```

Получили результат: 

![1](https://github.com/SKA1010/hw_db_3/assets/125235217/dba581c1-3cc0-4f6a-9b34-4b80df4f467b)

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

### Решение 2

Написан запрос:

```sql
SELECT * 
FROM sakila.payment
WHERE payment_date BETWEEN '2005-06-15 00:00:00' AND '2005-06-18 23:59:59'
AND amount > 10.00;
```

Получили результат: 

![2](https://github.com/SKA1010/hw_db_3/assets/125235217/88dc2ffe-84ac-4051-aae7-c6c7350de78b)

### Задание 3

Получите последние пять аренд фильмов.

### Решение 3

Написан запрос:

```sql
SELECT * 
FROM sakila.rental
ORDER BY rental_date DESC LIMIT 5;
```

Получили результат: 

![3](https://github.com/SKA1010/hw_db_3/assets/125235217/9639a5f9-ca58-41d1-aeb9-d871210018d0)


### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

### Решение 4

Написан запрос:

```sql
SELECT LOWER(REPLACE (first_name, 'LL', 'PP')), LOWER (last_name) 
FROM sakila.customer
WHERE active = 1
AND first_name LIKE 'Kelly'
OR first_name LIKE 'Willie';
```

Получили результат: 

![4](https://github.com/SKA1010/hw_db_3/assets/125235217/45ea1237-a73e-4299-945a-9463965d6356)

 Написан запрос:

 ```sql
SELECT CONCAT_WS(' ', LOWER(REPLACE (first_name, 'LL', 'PP')), LOWER (last_name))
FROM sakila.customer
WHERE active = 1
AND first_name LIKE 'Kelly'
OR first_name LIKE 'Willie';
```
Получили результат: 

![4-2](https://github.com/SKA1010/hw_db_3/assets/125235217/68bd93e0-76cb-4e57-bb4f-6dcd6b552229)

