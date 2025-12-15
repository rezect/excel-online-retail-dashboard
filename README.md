# Excel Online Retail Dashboard (Power Query + Power Pivot + DAX)

Дашборд и аналитическая модель в Excel для транзакций интернет‑магазина на датасете UCI Online Retail (2010–2011). Данные содержат строки позиций в инвойсах; отмены помечаются InvoiceNo, начинающимся с "C", валюта цен — фунты стерлингов. [web:1]

## Status 

**Done:** ---
**In progress:** Sprint 0
**Planned:** Sprint 1+

## Что внутри
- (планируется) Обновляемый ETL в Power Query: импорт, типизация, очистка, вычисляемые поля. [web:41]
- (планируется) Модель данных (звезда) в Excel Data Model/Power Pivot: факт продаж + измерения (Date/Product/Customer/Country). [web:41]
- (планируется) DAX‑меры для KPI и аналитики по времени, товарам и клиентам. [web:25]
- (планируется) Отчётные листы:
  - `Dashboard` — основные KPI и визуализации.
  - `Customers` — клиентская аналитика (в т.ч. RFM).
  - `Products` — товарная аналитика (в т.ч. ABC/Pareto).
  - `Data_Quality` — контроль качества данных и допущения.

## Бизнес-вопросы
- Как меняется выручка во времени и какие страны дают основной вклад? [web:1]
- Какие товары лидируют по выручке и где высокая доля отмен? [web:1]
- Какие клиенты приносят больше всего денег и как выглядят сегменты по поведению (RFM)? [web:25]

## Источник данных
- Dataset: **UCI Machine Learning Repository — Online Retail**. [web:1]
- Состав полей (основные): InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country. [web:1]
- Правило отмен: InvoiceNo начинается с "C". [web:1]
- Лицензия датасета: CC BY 4.0 (см. страницу набора данных). [web:1]

## Определения метрик
> Полные определения и допущения: см. лист `Metrics Dictionary` в Excel-файле.

- Revenue (выручка): сумма по строкам \(Quantity * UnitPrice\). [web:1]
- Orders (заказы): количество уникальных InvoiceNo (отдельно считаются “все” и “без отмен”). [web:1]
- AOV (средний чек): Revenue / Orders. [web:25]
- Customers (активные клиенты): количество уникальных CustomerID. [web:1]
- Cancel Rate (доля отмен): доля заказов/строк с InvoiceNo="C…". [web:1]

## Как запустить
1. Скачайте исходный файл датасета `Online Retail.xlsx` со страницы UCI и положите его в папку `data/` (или укажите свой путь в параметре на листе `Control`). [web:1]
2. Откройте файл проекта Excel: `excel-online-retail-dashboard.xlsx` (замените на ваше фактическое имя).
3. Нажмите **Data → Refresh All** (Обновить всё), чтобы обновить запросы, модель и отчёты. [web:41]

## Требования
- Excel с Power Query и Data Model/Power Pivot (обычно Microsoft 365 / Excel 2019+). [web:41]
- Доступ к файлу датасета (локально).

## Структура репозитория
.
├─ data/ # папка для исходного датасета
├─ docs/
│ └─ sprint-plan.md # план работ по спринтам
├─ screenshots/ # скриншоты дашборда
├─ excel-online-retail-dashboard.xlsx
└─ README.md

## Допущения и ограничения
- Отмены определяются по признаку InvoiceNo="C…"; это влияет на подсчёт заказов и “net” метрики. [web:1]
- UnitPrice в фунтах стерлингов; конвертация валюты не выполняется. [web:1]
- Качество данных (пропуски CustomerID и др.) отражается на листе `Data_Quality`. [web:1]

## Roadmap
Подробный план развития: `docs/sprint-plan.md`.

## Лицензия проекта
Код/шаблон Excel: (укажите свою лицензию, например MIT).  
Данные: UCI Online Retail, условия — CC BY 4.0 (см. источник). [web:1]
