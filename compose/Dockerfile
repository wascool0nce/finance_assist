# Используем официальный образ Python для Django
FROM python:3.11-slim-buster
ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# Устанавливаем переменные среды
RUN apt-get update \
    && apt-get install -y netcat

# Создаем и устанавливаем директорию приложения
WORKDIR /finance_assist

# Устанавливаем зависимости
COPY requirements.txt requirements.txt
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
COPY ./apps .
# Копируем проект в контейнер

COPY ./compose/entrypoint /entrypoint
RUN sed -i 's/\r$//g' /entrypoint
RUN chmod +x /entrypoint

COPY ./compose/start /start
RUN sed -i 's/\r$//g' /start
RUN chmod +x /start
