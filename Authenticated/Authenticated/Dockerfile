# Build from the repository root:
# docker build -f Authenticated/Authenticated/Dockerfile .
FROM python:3.13.17-slim

WORKDIR /app

ENV PYTHONUNBUFFERED=1 \
    LANG=C.UTF-8 \
    PORT=8000

COPY Authenticated/Pipfile Authenticated/Pipfile.lock ./
RUN pip install --no-cache-dir pipenv==2026.10.2 \
    && pipenv verify \
    && pipenv sync --system

COPY Authenticated/Authenticated/ ./

EXPOSE 8000
CMD ["sh", "-c", "exec gunicorn Authenticated.wsgi:application --bind 0.0.0.0:${PORT}"]
