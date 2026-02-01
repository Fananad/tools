# Мониторинг сетевых запросов браузера и авторизация в Plaud.ai

Инструменты на Python для:
- Мониторинга всех HTTP/HTTPS запросов браузера с помощью Playwright
- Автоматической авторизации в Plaud.ai через Google SSO

## Установка

1. Убедитесь, что виртуальное окружение активировано:
```bash
source browser_monitor/venv/bin/activate
```

2. Установите зависимости:
```bash
pip install -r requirements.txt
```

3. Установите браузеры для Playwright:
```bash
playwright install chromium
```

## Структура проекта

```
plaud/
├── browser_monitor/      # Мониторинг сетевых запросов браузера
│   ├── browser_monitor.py
│   ├── logs/             # Логи (не коммитятся в git)
│   │   ├── network_monitor_*.log
│   │   └── network_logs_*.json
│   └── README.md
├── plaud_api_service/    # Работа с Plaud API (директории и записи)
│   ├── client.py
│   ├── requirements.txt
│   └── README.md
├── plaud_cookie_service/ # Получение куки из Chrome и запросы к Plaud API
│   ├── client.py
│   └── requirements.txt
├── start.sh              # Запуск виртуалки и browser_monitor по абсолютному пути
└── README.md
```

## Быстрый старт

### Авторизация в Plaud.ai через Google SSO

Самый простой способ получить токен для работы с API Plaud.ai:

```bash
python google_sso_auth/google_sso_auth.py your.email@gmail.com your_password
```

После успешной авторизации токен будет сохранен в файл `google_sso_auth/plaud_token.json`.

Подробная документация: [google_sso_auth/GOOGLE_SSO_README.md](google_sso_auth/GOOGLE_SSO_README.md)

### Мониторинг сетевых запросов

```bash
python browser_monitor/browser_monitor.py https://example.com
# или
./start.sh https://example.com
```

Все логи сохраняются в папку `browser_monitor/logs/`.
