# Excel Online Retail Dashboard (Power Query + Power Pivot + DAX)

Дашборд и аналитическая модель в Excel для транзакций интернет‑магазина на датасете UCI Online Retail (2010–2011). Данные содержат строки позиций в инвойсах; отмены помечаются InvoiceNo, начинающимся с "C", валюта цен — фунты стерлингов.

## Что внутри
- Обновляемый ETL в Power Query: импорт, типизация, очистка, вычисляемые поля.
- Модель данных (звезда) в Excel Data Model/Power Pivot: факт продаж + измерения (Date/Product/Customer/Country).
- DAX‑меры для KPI и аналитики по времени, товарам и клиентам.
- Отчётные листы:
  - `Dashboard` — основные KPI и визуализации.
  - `Customers` — клиентская аналитика (в т.ч. RFM).
  - `Products` — товарная аналитика (в т.ч. ABC/Pareto).
  - `Data_Quality` — контроль качества данных и допущения.

## Бизнес-вопросы
- Как меняется выручка во времени и какие страны дают основной вклад?
- Какие товары лидируют по выручке и где высокая доля отмен?
- Какие клиенты приносят больше всего денег и как выглядят сегменты по поведению (RFM)?

## Источник данных
- Dataset: [**UCI Machine Learning Repository — Online Retail**](https://archive.ics.uci.edu/dataset/352/online+retail).
- Состав полей (основные): InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country.
- Правило отмен: InvoiceNo начинается с "C".
- Лицензия датасета: CC BY 4.0 (см. страницу набора данных).

## Определения метрик
> Полные определения и допущения: см. лист `Metrics Dictionary` в Excel-файле.

- Revenue (выручка): сумма по строкам \(Quantity * UnitPrice\).
- Orders (заказы): количество уникальных InvoiceNo (отдельно считаются “все” и “без отмен”).
- AOV (средний чек): Revenue / Orders.
- Customers (активные клиенты): количество уникальных CustomerID.
- Cancel Rate (доля отмен): доля заказов/строк с InvoiceNo="C…".

## Как запустить
1. Скачайте исходный файл датасета `Online Retail.xlsx` со страницы UCI и положите его в папку `data/` (или укажите свой путь в параметре на листе `Control`).
2. Откройте файл проекта Excel: `excel-online-retail-dashboard.xlsx` (замените на ваше фактическое имя).
3. Нажмите **Data → Refresh All** (Обновить всё), чтобы обновить запросы, модель и отчёты.

## Требования
- Excel с Power Query и Data Model/Power Pivot (обычно Microsoft 365 / Excel 2019+).
- Доступ к файлу датасета (локально).

## Структура репозитория
```txt
.
├─ data/ # папка для исходного датасета
├─ docs/
│ └─ sprint-plan.md # план работ по спринтам
├─ screenshots/ # скриншоты дашборда
├─ excel-online-retail-dashboard.xlsx
└─ README.md
```

## Допущения и ограничения
- Отмены определяются по признаку InvoiceNo="C…", отрицательной Quantity или UnitPrice; это влияет на подсчёт заказов и “net” метрики.
- UnitPrice в фунтах стерлингов; конвертация валюты не выполняется.
- Качество данных (пропуски CustomerID и др.) отражается на листе `Data_Quality`.

## Roadmap
Подробный план развития: `docs/sprint-plan.md`.

## Скриншоты
![Главный Дашборд](https://github.com/rezect/excel-online-retail-dashboard/blob/main/imgs/01_dashboard.png?raw=true)

![Пользовательский Дашборд](https://github.com/rezect/excel-online-retail-dashboard/blob/main/imgs/02_customers.png?raw=true)

![Продуктовый Дашборд](https://github.com/rezect/excel-online-retail-dashboard/blob/main/imgs/03_products.png?raw=true)

## Лицензия проекта
Код/шаблон Excel: MIT.  
Данные: UCI Online Retail, условия — CC BY 4.0 (см. источник).
