# api_standard

Шаблон (starter) для FastAPI-сервиса с Docker, PostgreSQL, SQLAlchemy и базовой инфраструктурой разработки.

> Репозиторий содержит Dockerfile, docker-compose, пример конфига и исходники в `src/`.

---

## Возможности

- FastAPI-приложение, запуск через Uvicorn.
- Docker Compose окружение: приложение + PostgreSQL 16.
- Конфигурация через файл `config.yaml` (есть `config.yaml.example`).
- Инструменты разработки: pre-commit, pytest, pytest-asyncio.
- Асинхронный доступ к Postgres через `asyncpg` + SQLAlchemy 2.x.

---

## Стек

- Python 3.11+.
- FastAPI + Uvicorn.
- SQLAlchemy 2.x + asyncpg.
- Dynaconf / pydantic-settings для настроек.
- PostgreSQL 16.

---

## Быстрый старт (Docker)

1) Скопируй пример конфига:
```bash
cp config.yaml.example config.yaml
```
(Файл `config.yaml.example` лежит в корне репозитория.)

2) Запусти сервисы:
```bash
docker compose up --build
```

3) Приложение будет доступно на:
- http://localhost:3000

4) Swagger/OpenAPI:
- http://localhost:3000/docs
- http://localhost:3000/redoc

> По умолчанию контейнер запускает: `uvicorn --host 0.0.0.0 --port 3000 app.asgi:app --reload`.

---

## Локальная разработка (Poetry)

1) Установи зависимости:
```bash
poetry install
```

2) Запусти приложение локально (пример):
```bash
poetry run uvicorn app.asgi:app --reload --port 3000
```
Точка входа `app.asgi:app` используется и в docker-compose.

---

## Конфигурация

- Создай `config.yaml` на основе `config.yaml.example`.
- В Docker-окружении `config.yaml` монтируется внутрь контейнера.
- Параметры БД в compose по умолчанию:
  - user/password/db: `example` / `example` / `example`.

---

## Тесты

```bash
poetry run pytest
```
Зависимости для тестов (`pytest`, `pytest-asyncio`).

---

## Pre-commit

```bash
poetry run pre-commit install
poetry run pre-commit run --all-files
```
Конфигурация pre-commit хранится в `.pre-commit-config.yaml`.

---

