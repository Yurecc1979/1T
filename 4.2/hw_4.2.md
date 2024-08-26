Задание
Вам необходимо написать SQL-запросы для выполнения следующих задач:

Вам необходимо написать SQL-запросы для выполнения следующих задач:

- Загрузите в свою базу датафрейм Mall_Customers.  Напишите запрос, который вернёт долю мужчин и женщин среди посетителей магазина. (Хинт: количество посетителей можно посчитать отдельно).

```sql
SELECT Genre, count(Genre)
FROM mall_customers
GROUP BY Genre;
```

Напишите запрос, который вернёт всех мужчин, отсортированных по возрастанию возраста, убыванию Annual_Income и возрастанию Spending_Score (используйте иерархическую сортировку).
``` sql
SELECT *
FROM mall_customers
WHERE Genre = 'Male'
ORDER BY Age ASC, Annual_Income DESC, Spending_Score ASC;
```

Создайте новую схему в своей базе данных. 


Назовите её AERO и запустите на этой схеме следующий скрипт  aero_pg_script.sql Внимание! При первом запуске скрипта нужно будет пропустить 4 ошибки т.к. в начале  идёт удаление таблиц которых на данный момент не существует. 




3. Ознакомьтесь с моделью данных, представленной на схеме:



Напишите скрипт, который позволит узнать, какой компанией летал каждый из пассажиров.
``` sql
SELECT DISTINCT ps.name, co.name 
FROM passenger ps
JOIN pass_in_trip pit ON ps.ID_psg = pit.ID_psg 
JOIN trip tr ON tr.trip_no = pit.trip_no 
JOIN company co ON tr.ID_comp =co.ID_comp 
ORDER BY ps.name ASC 
```
Напишите скрипт, который вернёт всех пассажиров, не совершавших полёт (не имевших билетов).
```sql
SELECT ps.name , pit.trip_no 
FROM passenger ps
LEFT JOIN pass_in_trip pit ON ps.ID_psg = pit.ID_psg 
WHERE pit.trip_no IS NULL 
```

Напишите скрипт, который позволит узнать, в какие города летала Николь Кидман.
```sql
SELECT ps.name , tr.town_to
FROM passenger ps
JOIN pass_in_trip pit ON ps.ID_psg = pit.ID_psg AND ps.name = "Nikole Kidman"
JOIN trip tr ON tr.trip_no = pit.trip_no
```

 Создайте новую схему COMP для скрипта computer_pg_script.sql.

Напишите скрипт, который позволит узнать цену PC с маркером А.
```sql
SELECT *
FROM product p 
JOIN pc ON p.model = pc.model 
AND p.maker = "A"
```

Напишите скрипт, который позволит узнать, какие маркеры у лазерных принтеров.
```sql
SELECT p.maker, pr.`type` 
FROM product p 
JOIN printer pr ON p.model = pr.model
AND pr.`type` = "Laser"
```