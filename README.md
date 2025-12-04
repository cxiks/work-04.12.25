Выполнил: Козлов Артем
группа: Ипо8482

1.1

```mermaid
graph TD
    Start([Начало]) --> A[Кипячение воды]
    A --> Decision{Есть ли чай?}
    Decision -- Да --> B[Заварить чай]
    Decision -- Нет --> C[Купить чай]
    C --> B
    B --> D[Пить чай]
    D --> Finish([Конец])
```


1.2

```mermaid 
sequenceDiagram
    box
    participant К as Клиент
    participant П as Приложение
    participant С as Сервер
    participant В as Водитель
    end

    К->>П: Вызов такси
    activate П
    П->>С: Запрос на поиск водителя
    activate С
    С->>В: Новый заказ
    activate В
    В-->>С: Принятие заказа
    deactivate В
    С-->>П: Данные водителя
    deactivate С
    П-->>К: Заказ принят
    deactivate П
    
    В->>К: Забирает клиента
```


2.1

```mermaid 
classDiagram
    direction TB
    
    class Book {
        -String title
        -String author
        -String ISBN
        -boolean isAvailable
        +checkOut()
        +returnBook()
        +getBookInfo() String
    }
    
    class User {
        -String name
        -String userId
        -List~Book~ borrowedBooks
        +borrowBook(book: Book)
        +returnBook(book: Book)
        +getUserInfo() String
    }
    
    class Library {
        -List~Book~ books
        -List~User~ users
        +addBook(book: Book)
        +addUser(user: User)
        +findBookByISBN(isbn: String) Book
        +findUserById(userId: String) User
    }
    User --> Book
    Library --> Book
    Library --> User
```

2.2 

 ```mermaid 

gantt
    title Проект: Разработка мобильного приложения
    dateFormat  YYYY-MM-DD
    axisFormat  %d.%m

    section Подготовка
    Подготовка проекта          :prep, 2025-01-01, 5d

    section Дизайн
    Разработка дизайна          :design, after prep, 7d

    section Разработка
    Фронтенд‑разработка         :frontend, after design, 10d
    Бэкенд‑разработка           :backend, after prep, 12d

    section Тестирование
    Тестирование приложения     :tests, after frontend, 5d
    Тестирование бэкенда        :tests_backend, after backend, 5d
    Интеграционное тестирование :integration, after tests, 3d
```
 
3.1

 ```mermaid
graph TB
    subgraph "Frontend"
        A1[React]
        A2[Redux]
        A3[Router]
    end
    
    subgraph "Backend"
        B1[Node.js]
        B2[Express]
        B3[MongoDB]
    end
    
    subgraph "Внешние сервисы"
        C1[Stripe]
        C2[SendGrid]
    end
    
    A1 -- "HTTP запросы" --> B2
    B2 -- "Работа с данными" --> B3
    B2 -- "Обработка платежей" --> C1
    B2 -- "Отправка email" --> C2
    A2 -- "Управление состоянием" --> A1
    A3 -- "Навигация" --> A1
    B1 -- "Запуск сервера" --> B2

 ```

 3.2

  ```mermaid 
stateDiagram-v2
    [*] --> Новый
    Новый --> Подтвержденный: подтвердить
    Подтвержденный --> Оплаченный: оплатить
    Подтвержденный --> Отмененный: отменить
    
    state Оплата {
        [*] --> Ожидание
        Ожидание --> Успешно: платеж прошел
        Ожидание --> Ошибка: платеж не прошел
        Ошибка --> Ожидание: повторить
    }
    
    Оплаченный --> Оплата: начать оплату
    Оплата --> Оплаченный: завершить оплату
    
    Оплаченный --> Отправленный: отправить
    Отправленный --> Доставленный: доставить
    Доставленный --> [*]: завершен
    Доставленный --> Возвращенный: вернуть товар
    Отмененный --> [*]
    Возвращенный --> [*]

 ```

 4.1

```mermaid
erDiagram
    USERS {
        int id
        string name
        string email
    }

    POSTS {
        int id
        string content
        int author_id
    }

    COMMENTS {
        int id
        string content
        int post_id
        int author_id
    }

    LIKES {
        int user_id
        int post_id
    }

    FOLLOWS {
        int follower_id
        int followee_id
    }

    USERS ||--o{ POSTS : "создаёт"
    USERS ||--o{ COMMENTS : "пишет"
    POSTS ||--o{ COMMENTS : "имеет"
    USERS ||--o{ LIKES : "делает"
    POSTS ||--o{ LIKES : "получает"
    USERS ||--o{ FOLLOWS : "подписывается"
    USERS ||--o{ FOLLOWS : "имеет подписчиков"
```
    
    5

 ```mermaid
    graph TD
    Start([Начало]) --> A[Выбор ресторана]
    A --> B[Выбор блюд]
    B --> C{Корзина пуста?}
    C -->|Да| B
    C -->|Нет| D[Оформление заказа]
    D --> E[Выбор доставки]
    E --> F[Ввод адреса]
    F --> G[Оплата]
    G --> H{Оплата успешна?}
    H -->|Нет| G
    H -->|Да| I[Подтверждение заказа]
    I --> J[Приготовление]
    J --> K[Доставка]
    K --> L[Получение заказа]
    L --> M[Оценка сервиса]
    M --> Finish([Конец])

 ```
6
```mermaid
pie title Структура автомобильного рынка
    "Иномарки"             : 55
    "Отечественные"        : 30
    "Совместное производство" : 15
```