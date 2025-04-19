# 🐱 Kittygram

![Main Kittygram workflow](https://github.com/Port-tf/kittygram/actions/workflows/main.yml/badge.svg)

Kittygram — это веб-сервис, на котором пользователи могут делиться фотографиями своих кошек, добавлять информацию о них и просматривать профили других котиков.

## 🚀 Функциональность

- Регистрация и авторизация пользователей
- Добавление и редактирование карточек котиков
- Возможность отметить любимых котиков
- Просмотр карточек других пользователей

## 🛠️ Технологии

- Python 3.9
- Django
- Gunicorn
- Nginx
- PostgreSQL
- React
- Node.js
- Docker / Docker Compose
- GitHub Actions (CI/CD)
- Яндекс.Облако

## 📦 Установка и запуск проекта

### 🔧 Запуск в Docker

```bash
git clone https://github.com/Dzmitry-Radziuk/kittygram_final.git
cd kittygram_final
```
# 2. Создайте файл .env и заполните его по шаблону:

```h
SECRET_KEY=ваш_секретный_ключ
DEBUG=False
ALLOWED_HOSTS=ваш_домен
POSTGRES_DB=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
## 3. Cоберите и запустите контейнеры:

```bash
docker compose -f docker-compose.production.yml up -d --build
```
## 4. После запуска выполните миграции и сбор статических файлов:

```bash
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic --noinput
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
 
## 5. Проект будет доступен по адресу: https://<ваш_домен>

## 💻 Локальный запуск без Docker

## 1. Установите зависимости Python:

```bash
cd backend/
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```
## 2. Установите зависимости для фронтенда:

```bash
cd ../frontend/
npm ci
```
## 3. Настройте базу данных и переменные окружения, затем выполните миграции и запуск:
```bash
cd ../backend/
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver

```

## ✅ CI/CD

Автоматический деплой на сервер после пуша в ветку main реализован с помощью GitHub Actions и Яндекс.Облака. После успешного деплоя приходит уведомление в Telegram.

## 🧪 Тестирование
## Для запуска автотестов необходимо указать необходимые данные в tests.yml:

repo_owner: Dzmitry-Radziuk
kittygram_domain: https://<ваш_домен_kittygram>
taski_domain: https://<ваш_домен_taski>
dockerhub_username: <ваш_логин_на_докерхабе>

## Тесты можно запустить локально командой:

```bash
cd backend/
pytest
```
## 👤 Автор:
Дмитрий Радюк — Python-разработчик
[Dzmitry-Radziuk](https://github.com/Dzmitry-Radziuk)
