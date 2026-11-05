## ER-диаграмма: учёт лабораторных исследований

Диаграмма отражает модель данных для направлений, назначенных анализов, результатов и заключений.

```mermaid
erDiagram
    PATIENT ||--o{ REFERRAL : "получает"
    REFERRAL ||--|| CONCLUSION : "имеет заключение"
    DOCTOR ||--o{ REFERRAL : "выдает"
    REFERRAL ||--o{ REFERRAL_TESTS : "содержит позиции"
    TEST ||--o{ REFERRAL_TESTS : "входит в назначения"
    REFERRAL_TESTS ||--o| RESULT : "имеет результат"

    PATIENT {
        int patient_id PK
        string name
        date birth_date
    }

    REFERRAL {
        int referral_number PK
        date issue_date
        string state
        int doctor_id FK
        int patient_id FK
    }

    TEST {
        string test_code PK
        string test_name
        string test_ref_value
        string test_unit
    }

    RESULT {
        int referral_number PK, FK
        string test_code PK, FK
        string result_value
        date date_of_receipt
        boolean critical_value
    }

    CONCLUSION {
        int referral_number PK, FK
        date date_of_conclusion
        string text_of_conclusion
        int doctor_id FK
    }

    DOCTOR {
        int id PK
        string first_name
        string last_name
    }

    REFERRAL_TESTS {
        int referral_number PK, FK
        string test_code PK, FK
    }
```

### Гарантии целостности

- **Состав направления и результаты:** результат можно записать только для реально назначенного анализа (FK на составной ключ `REFERRAL_TESTS`).  
- **1:0..1 для результата:** у одной позиции направления — ровно один результат или ноль (составной PK в `RESULT`).  
- **1:1 для заключения:** у направления ровно одно заключение (PK `referral_number` в `CONCLUSION`).  
- **Статусы:** допустимые значения фиксируются на уровне БД через `CHECK`.  
- **Нормализация:** транзитивные зависимости минимизированы; `doctor_id` в `CONCLUSION` отражает автора заключения, а не дублирует врача направления.
