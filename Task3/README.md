# Task 3: Целевая архитектура данных и аналитическая платформа

## Описание решения

В рамках третьего задания спроектирована целевая архитектура данных (To-Be) через 12 месяцев после слияния FinUnion и RetailBank. Проведен сравнительный анализ архитектурных подходов (DWH на PostgreSQL, Data Lakehouse, Data Mesh), обоснован выбор гибридной архитектуры. Спроектированы пайплайны данных (включая промежуточный и целевой), аналитическая модель данных (схема «звезда») и доменные data-продукты.

## Структура директории

* [**target-data-architecture.md**](./target-data-architecture.md) — описание целевой To-Be архитектуры и диаграмма компонентов.
* [**architecture-options.md**](./architecture-options.md) — сравнение трех подходов (DWH, Lakehouse, Data Mesh) и обоснование выбора.
* [**dwh-lakehouse.md**](./dwh-lakehouse.md) — детальное сравнение PostgreSQL DWH и Data Lakehouse, роль Iceberg/Trino, ограничения.
* [**data-pipelines.md**](./data-pipelines.md) — описание 4+ пайплайнов данных (включая промежуточный и сценарии Big Data).
* [**analytical-model.md**](./analytical-model.md) — аналитическая модель (схема «звезда») для домена транзакций.
* [**data-products.md**](./data-products.md) — 4 доменных data-продукта с привязкой к BIAN.
* [**diagrams/target\_architecture.puml**](./diagrams/target_architecture.puml) — код PlantUML для целевой архитектуры.

