# Tasks API

## Описание

Этот проект представляет собой REST API на Django для управления задачами. Включает в себя создание, редактирование, удаление и просмотр задач. Использует Django REST Framework и PostgreSQL в качестве базы данных.

## Технологии

- Python 3.10+
- Django 4.2+
- Django REST Framework
- PostgreSQL
- CORS Headers
- Docker и Docker Compose

## Функционал

- Аутентификация пользователей через Django
- CRUD-операции для задач
- Поддержка CORS для фронтенда
- Хранение данных в PostgreSQL
- Разграничение прав доступа
- Поддержка контейнеризации с Docker

## Установка и запуск

### 1. Клонирование репозитория
```bash
git clone https://github.com/iurkinvalentin/Tasks-docker
cd django_backend_api
```

### 2. Создание виртуального окружения и установка зависимостей
```bash
python -m venv venv
source venv/bin/activate  # Для macOS/Linux
venv\Scripts\activate  # Для Windows
pip install -r requirements.txt
```

### 3. Настройка переменных окружения
Создайте файл `.env` в корневой директории и добавьте:
```env
POSTGRES_DB=django
POSTGRES_USER=django
POSTGRES_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432
```

### 4. Применение миграций и запуск сервера
```bash
python manage.py migrate
python manage.py runserver
```

## Запуск с Docker

### 1. Убедитесь, что установлен Docker и Docker Compose
Проверьте установку командой:
```bash
docker --version
docker-compose --version
```

### 2. Запуск контейнеров в продакшн-режиме
```bash
docker-compose -f docker-compose.production.yml up -d --build
```

### 3. Описание Docker Compose
Проект использует несколько сервисов:
- **db** – PostgreSQL 13.10 с сохранением данных в volume `pg_data_production`
- **backend** – Образ Django backend с сохранением статики в `backend_static`
- **frontend** – React frontend, загружаемый с Docker Hub
- **gateway** – Nginx gateway, раздающий статику и проксирующий запросы

## Использование API

После запуска API доступно по адресу: `http://127.0.0.1:8000/api/`

### Основные эндпоинты

- `GET /api/tasks/` – Получение списка задач
- `POST /api/tasks/` – Создание задачи
- `GET /api/tasks/{id}/` – Просмотр задачи
- `PUT /api/tasks/{id}/` – Обновление задачи
- `DELETE /api/tasks/{id}/` – Удаление задачи

## Разрешения

- Все пользователи могут просматривать задачи.
- Только авторизованные пользователи могут создавать, редактировать и удалять задачи.

## Контакты
Юркин Валентин

