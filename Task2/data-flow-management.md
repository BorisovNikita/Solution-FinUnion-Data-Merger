# Управление потоками данных

|Источник|Приёмник|Сущность|Действие|Формат|Частота|Тип обмена|SLA|Владелец|Контроль качества|Требования к безопасности|Мониторинг|
|-|-|-|-|-|-|-|-|-|-|-|-|
|FU CRM|MDM|Участвующая сторона|Create/Update/Deduplicate|JSON|Near real-time|Async (CDC)|5 мин|Data Office|Проверка дублей, валидация ИНН|TLS 1.3, маскирование ПДн|Prometheus + Grafana (Latency)|
|RB CRM|MDM|Участвующая сторона|Create/Update/Deduplicate|JSON|Near real-time|Async (CDC)|5 мин|Data Office|Проверка дублей, валидация телефона|TLS 1.3, маскирование ПДн|Prometheus + Grafana|
|MDM|FU CRM|Участвующая сторона|Read (Golden Record)|JSON|Near real-time|Async|2 мин|Data Office|Сверка Global ID|TLS 1.3, RBAC|ELK Stack (логи)|
|MDM|RB CRM|Участвующая сторона|Read (Golden Record)|JSON|Near real-time|Async|2 мин|Data Office|Сверка Global ID|TLS 1.3, RBAC|ELK Stack|
|FU Core|DWH|Счет, Транзакция|Extract/Validate|Parquet / CSV|Batch (ночь)|Batch|4 часа|DWH Team|Контроль сходимости баланса|VPN/Выделенный канал, шифрование|Airflow + Grafana|
|RB Core|DWH|Счет, Транзакция|Extract/Validate|Parquet / CSV|Batch (ночь)|Batch|4 часа|DWH Team|Контроль сходимости баланса|VPN/Выделенный канал, шифрование|Airflow + Grafana|
|FU Cards|DWH|Карта|Extract/Validate|Parquet|Batch (ночь)|Batch|3 часа|DWH Team|Проверка статусов|VPN/Выделенный канал|Airflow|
|HR-система|MDM|Департамент, Сотрудник|Create/Update|JSON|Ежедневно|Batch|2 часа|HR / Data Office|Уникальность кодов|RBAC, TLS 1.3|Airflow|
|DWH|BI|Агрегаты (Все)|Aggregate/Read|SQL / OLAP|По запросу|Sync|30 сек|BI Team|Сверка метрик|RBAC, аудит доступа|BI-мониторинг|
|DWH|Регулятор|Отчетность|Extract|XML / CSV|По регламенту|Batch (защищенный канал)|1 день|Fin. Department|Валидация XSD-схем|ЭЦП, шифрование, ГОСТ|Ручной контроль + Логи|
|FU CRM, RB CRM|Поисковый движок|Обращение, Участвующая сторона|Index/Read|JSON|Near real-time|Streaming|1 мин|Контакт-центр|Полнотекстовая проверка|Маскирование ПДн, RBAC|Kibana|



