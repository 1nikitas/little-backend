# Little Backend

## Описание проекта

Этот проект демонстрирует микросервисную архитектуру на базе FastAPI. Включает два сервиса: `cast-service` для работы с данными актеров и `movie-service` для работы с данными фильмов. Сервисы оркестрируются с помощью Docker и NGINX для маршрутизации.

## Архитектура

#### cast-service

**Основные компоненты:**

- **app/main.py**: Главный файл, содержащий создание FastAPI приложения и регистрацию маршрутов.
- **app/api/**: Содержит маршруты и обработчики запросов.
    - **app/api/endpoints/**: Содержит отдельные файлы с endpoint-ами (например, `casts.py`).
- **app/core/**: Важные конфигурации и настройки (например, настройки базы данных).
- **app/models/**: Определения моделей для базы данных.
- **app/schemas/**: Pydantic схемы для валидации данных.
- **app/crud/**: Функции для работы с базой данных (CRUD операции).

#### movie-service

**Основные компоненты:**

- **app/main.py**: Главный файл, содержащий создание FastAPI приложения и регистрацию маршрутов.
- **app/api/**: Содержит маршруты и обработчики запросов.
    - **app/api/endpoints/**: Содержит отдельные файлы с endpoint-ами (например, `movies.py`).
- **app/core/**: Важные конфигурации и настройки (например, настройки базы данных).
- **app/models/**: Определения моделей для базы данных.
- **app/schemas/**: Pydantic схемы для валидации данных.
- **app/crud/**: Функции для работы с базой данных (CRUD операции).

#### NGINX

**Файл:** `nginx_config.conf`

- Содержит настройки для маршрутизации запросов к соответствующим сервисам на основе пути URL.

### Структуры проекта

.
├── cast-service
│   ├── app
│   │   ├── api
│   │   │   └── endpoints
│   │   │       └── casts.py
│   │   ├── core
│   │   │   └── config.py
│   │   ├── models
│   │   │   └── cast.py
│   │   ├── schemas
│   │   │   └── cast.py
│   │   ├── crud
│   │   │   └── cast.py
│   │   └── main.py
├── movie-service
│   ├── app
│   │   ├── api
│   │   │   └── endpoints
│   │   │       └── movies.py
│   │   ├── core
│   │   │   └── config.py
│   │   ├── models
│   │   │   └── movie.py
│   │   ├── schemas
│   │   │   └── movie.py
│   │   ├── crud
│   │   │   └── movie.py
│   │   └── main.py
├── docker-compose.yml
└── nginx_config.conf



## Установка и запуск

1. Убедитесь, что установлены `docker` и `docker-compose`.
2. Запустите команду:
    ```bash
    docker-compose up -d
    ```
3. Откройте [документацию для movie-service](http://localhost:8080/api/v1/movies/docs) и [документацию для cast-service](http://localhost:8080/api/v1/casts/docs).
