# ANRI-PHARM — автоматичний звіт Bolt Food UA

Пакет для автооновлюваного звіту партнера **ANRI-PHARM** (аптечна мережа).
Побудований за зразком інших партнерських звітів (вкладки Monthly + Weekly + Активність локацій, блок «Активація мережі»).

## Параметри звіту

| Параметр | Значення |
|----------|----------|
| `PARTNER_NAME` (group_name у Databricks) | `ANRI-PHARM` (85 закладів) |
| `PARTNER_DISPLAY` (заголовок) | `ANRI-PHARM` |
| `DATA_START` | `2025-01-01` |
| Initials (лого) | `AP` |
| Slug публічного репо / Pages | `anri-pharm-report` |
| Live URL | https://khrystynaberezna-lgtm.github.io/anri-pharm-report/ |
| Дані | Unity Catalog `main.ng_delivery` (UA) |

## Файли

```
ANRI-PHARM/
├── generate_report.py                 # тягне дані з Databricks → index.html
├── template.html                      # HTML-шаблон (брендинг Bolt, Chart.js)
├── publish.sh                         # генерація + git push у публічний репо
├── requirements.txt                   # databricks-sql-connector
├── .env                               # конфіг + Databricks PAT (НЕ в git)
├── .env.example                       # шаблон конфігу
├── .gitignore                         # .env та report_data.json не комітяться
├── cursor-rule.mdc                    # правило Cursor для цього звіту
├── README.md                          # цей файл
└── .github/workflows/update-report.yml  # автооновлення щопонеділка (05:00/07:00/09:00 UTC)
```

## Оновлення

- **Автоматично**: GitHub Actions щопонеділка (резервні запуски 05:00 / 07:00 / 09:00 UTC).
- **Вручну**: репо → Actions → «Оновлення звіту ANRI-PHARM» → Run workflow.
- **Локально**: `cd "ANRI-PHARM" && ./publish.sh`.

> Databricks PAT живе 90 днів — після прострочення згенеруй новий і онови `.env`
> та секрет `DATABRICKS_TOKEN` у репо.
