1. Запрос, который вернет характеристики размера вооружённых сил Катара. 

```sql
select `Armed Forces size`
from `world-data-2023`.`world-data`
where Country = 'Qatar'
```

2. Запрос, который вернет все страны с Fertility Rate менее 2.

```sql
select Country
from `world-data-2023`.`world-data`
where `Fertility Rate` < 2 
```

3. Запрос, который вернет все страны с аббревиатурой  abbreviation, начинающейся на S, или продолжительностью жизни «Life expectancy» менее 60 лет.

```sql
select Country
from `world-data-2023`.`world-data`
where  Abbreviation like 'S%' or  `Life expectancy` < 60 
```

4. Запрос который вернёт все страны, где официальный язык английский.

```sql
select Country
from `world-data-2023`.`world-data`
where  `Official language` = 'English'
```

5. Запрос который вернёт все страны, где официальный язык английский с «Maternal mortality ratio»  менее 20  или  Life expectancy < 60. 

```sql
select Country
from `world-data-2023`.`world-data`
where  `Official language` = 'English' and (`Maternal mortality ratio` < 20 or `Life expectancy` < 60)
```
