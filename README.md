# Kittygram
Kittygram — социальная сеть для обмена фотографиями любимых питомцев.

![example event parameter](https://github.com/github/docs/actions/workflows/main.yml/badge.svg?event=push)
### Стек используемых технологий:
- Python
- Django
- Nginx 
- Gunicorn 
- React 
- Django Rest Framework
- Certbot


## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone <ссылка на GitHub репозитория>
```

Перейти в корневую директорию
```
cd kittygram_final
```

Создать файл .evn для хранения ключей:

```
POSTGRES_USER=kittygram
POSTGRES_PASSWORD=secret_password
POSTGRES_DB=kittygram
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<Указать серкретный ключ>
ALLOWED_HOSTS='<Ваш IP-адрес>, 127.0.0.1, localhost, <Ваш домен>'
```

Запустить docker-compose.production:

```
docker compose -f docker-compose.production.yml up
```

Выполнить миграции, сбор статики:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```

Создать суперпользователя, ввести почту, логин, пароль:

```
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```

##  Как работать с репозиторием финального задания

### Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

### Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

### Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.

### Автор
[Кабанов Антон](https://github.com/Och1ta) 
