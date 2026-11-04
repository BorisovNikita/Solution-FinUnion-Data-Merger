# Логическая модель данных

```mermaid
erDiagram
    COUTERPARTY ||--o{ ACCOUNT : "владеет"
    COUTERPARTY ||--o{ CONTRACT : "заключает"
    COUTERPARTY ||--o{ LOAN : "берет"
    COUTERPARTY ||--o{ REQUEST : "инициирует"
    COUTERPARTY ||--o{ CARD : "использует"

    ACCOUNT ||--o{ CARD : "выпускает"
    ACCOUNT ||--o{ TRANSACTION : "содержит"
    ACCOUNT ||--o{ PAYMENT : "совершает"
    
    CONTRACT ||--o{ LOAN : "обслуживает"
    CONTRACT ||--o{ ACCOUNT : "открывает"

    PRODUCT ||--o{ CONTRACT : "определяет"
    PRODUCT ||--o{ LOAN : "типизирует"

    DEPARTMENT ||--o{ EMPLOYEE : "включает"
    DEPARTMENT ||--o{ REQUEST : "маршрутизирует"
    DEPARTMENT ||--o{ COUTERPARTY : "обслуживает"

    EMPLOYEE ||--o{ REQUEST : "обрабатывает"

    COUTERPARTY {
        string COUTERPARTY_id PK
        string full_name
        string inn
        string passport
        string phone
        string email
        string segment
    }

    ACCOUNT {
        string account_id PK
        string COUTERPARTY_id FK
        string account_number
        decimal balance
        string currency
        string status
    }

    CARD {
        string card_id PK
        string account_id FK
        string card_number
        string card_type
        string status
    }

    LOAN {
        string loan_id PK
        string COUTERPARTY_id FK
        string contract_id FK
        decimal amount
        decimal rate
        string status
    }

    CONTRACT {
        string contract_id PK
        string COUTERPARTY_id FK
        string product_id FK
        string contract_type
        date sign_date
        string status
    }

    TRANSACTION {
        string transaction_id PK
        string account_id FK
        decimal amount
        string type
        datetime date
        string status
    }

    PAYMENT {
        string payment_id PK
        string account_id FK
        decimal amount
        string recipient
        string status
    }

    PRODUCT {
        string product_id PK
        string name
        string category
        decimal rate
    }

    REQUEST {
        string request_id PK
        string COUTERPARTY_id FK
        string department_id FK
        string type
        string channel
        string status
        datetime created_at
    }

    EMPLOYEE {
        string employee_id PK
        string full_name
        string role
        string department_id FK
    }

    DEPARTMENT {
        string department_id PK
        string name
        string code
        string manager
        string region
    }
'''