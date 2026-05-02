FROM python:3.9-slim-buster

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /app

# Копируем файл зависимостей и устанавливаем их
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Копируем весь код проекта
COPY . .

# Устанавливаем переменные окружения для Django
# Это можно будет переопределить через docker-compose.yml
ENV DJANGO_SETTINGS_MODULE=kittygram_backend.settings

# Открываем порт, который будет использовать Gunicorn
EXPOSE 8000

# Команда для запуска Gunicorn
# Предполагается, что kittygram_backend/wsgi.py - это ваш WSGI-файл
CMD ["gunicorn", "kittygram_backend.wsgi:application", "--bind", "0.0.0.0:8000"]