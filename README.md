# Qual Exam Django Template

Шаблон Django-проекта для тренировочного экзаменационного билета.

В проекте уже есть:

- модели `Product` и `Event` из PDF;
- миграции, админ-панель и простой Bootstrap CRUD;
- серверная валидация данных;
- обработка несуществующих записей через стандартный HTTP 404;
- middleware с метриками запросов в консоли и `metrics.log`;
- настройки через `.env`;
- `/ping/` и интеграционный тест;
- `whitenoise` для статических файлов при `DEBUG=False`.

## Запуск

```bash
uv sync
cp .env.example .env
uv run python manage.py migrate
uv run python manage.py createsuperuser
uv run python manage.py runserver
```

Открыть:

- `http://127.0.0.1:8000/products/`
- `http://127.0.0.1:8000/events/`
- `http://127.0.0.1:8000/admin/`
- `http://127.0.0.1:8000/ping/`

## Проверка

```bash
uv run python manage.py test
uv run python manage.py collectstatic --noinput
```

Для проверки статики при `DEBUG=False` поменяйте значение в `.env`, выполните `collectstatic` и перезапустите сервер.

## Подготовка под конкретный вариант

Если нужен вариант с товарами, оставьте `Product` и маршруты `/products/`.
Если нужен вариант с мероприятиями, оставьте `Event` и маршруты `/events/`.

Зависимости указаны без жесткой фиксации версий: `uv` установит актуальные совместимые пакеты.
