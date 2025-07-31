# Завдання

✅ Завдання 1: Налаштування середовища

1. Розгортання Databricks Workspace
  * Створіть кластер із підтримкою DBR (Databricks Runtime) 13.0+

2. Налаштування Unity Catalog:
  * Створіть метастор (metastore), якщо його ще не існує.
  * Підключіть метастор до робочого простору.
  * Створіть:
    * Каталог <ім’я прізвище студента>_nyc_catalog
    * Схему trips_schema
    * Таблицю raw_trips

✅ Завдання 2: Імпорт, уніфікація та об’єднання

1. Імпорт даних:
  * Зчитайте yellow_tripdata_*.csv і green_tripdata_*.csv у Spark DataFrame.

2. Уніфікація схем:
  * Уніфікуйте назви колонок та типи даних.
  * Додайте колонку taxi_type зі значеннями yellow або green.

3. Фільтрація аномалій:
  * Видаліть записи:
    * Відстань < 0.1 км
    * Тариф < \$2
    * Тривалість < 1 хв

4. Збагачення колонками:
  * Додайте колонки:
    * pickup_hour
    * pickup_day_of_week
    * duration_min

5. JOIN з taxi_zone_lookup:
  * Додайте pickup_zone та dropoff_zone через join.

6. Збереження в Delta Lake:
* Запишіть результат у Unity Catalog:
* Формат: Delta Lake

✅ Завдання 3: Зведена аналітика zone_summary

1. Агрегація zone_summary:
  * Створіть датафрейм з колонками:
    * pickup_zone
    * total_trips
    * avg_trip_distance
    * avg_total_amount
    * avg_tip_amount
    * yellow_share / green_share
    * max_trip_distance
    * min_tip_amount
    * total_trip\amount

2. Збереження результатів:
  * Формат: Delta
  * Таблиця: zone_summary
  * Розміщення: Unity Catalog + S3 шлях (як external location або managed)

✅ Завдання 4: Додаткові аналітичні розрахунки

1. Агрегація по днях тижня:
  * Використайте raw_trips або zone_summary
  * Розрахуйте:
    * Total_trips_per_day
    * Avg_duration_per_zone
    * high_fare_share (fare > $30)

2. Збереження результату:
  * Таблиця: zone_days_summary
  * Формат: Delta
  * Розміщення: Unity Catalog + S3 шлях (як external location або managed)



Критерії оцінювання

* Notebook або .py файл у GitHub з чіткими коментарями.
* Дотримання best practices Unity Catalog (каталог → схема → таблиця).
* Використання Delta Lake (вказати формат у write).
* Скріншоти виконання notebook, pipeline jobs, та таблиць у Unity Catalog.
* Результати збережено у S3 або зовнішньому location.
