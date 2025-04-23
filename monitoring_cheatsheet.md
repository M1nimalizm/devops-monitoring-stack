
# 🐳 Шпаргалка по Docker-мониторингу (Prometheus + Grafana + Alertmanager)

## 📁 Навигация в терминале

```bash
pwd                        # показать текущую папку
ls                         # показать список файлов и папок
cd monitoring-demo         # перейти в папку проекта
cd ..                      # выйти на уровень выше
clear                      # очистить терминал
```

## 🐳 Docker Compose — управление сервисами

```bash
docker compose up -d                       # запустить все контейнеры
docker compose down                        # остановить и удалить все контейнеры
docker compose restart                     # перезапустить все сервисы
docker compose restart prometheus          # перезапуск только Prometheus
docker compose restart alertmanager        # перезапуск только Alertmanager
docker compose stop node_exporter          # остановить Node Exporter (тест алерта)
docker compose start node_exporter         # запустить Node Exporter обратно
```

## 🧾 Логи контейнеров

```bash
docker compose logs                        # все логи
docker compose logs alertmanager           # логи Alertmanager
docker compose logs prometheus             # логи Prometheus
```

## 🌐 Ссылки на интерфейсы

| Сервис        | Ссылка                     |
|---------------|----------------------------|
| Grafana       | http://localhost:3000      |
| Prometheus    | http://localhost:9090      |
| Alertmanager  | http://localhost:9093      |

## 📂 Структура проекта

```
monitoring-demo/
│
├── docker-compose.yml        # главный конфиг
├── prometheus.yml            # настройки Prometheus
├── alert_rules.yml           # правила алертов
├── alertmanager.yml          # конфиг Telegram
└── cpu_stress.py             # скрипт для нагрузки CPU
```

## ⚠️ Работа с нагрузкой

```bash
python3 cpu_stress.py         # искусственная нагрузка CPU
killall yes                   # остановить yes-нагрузку
```

## 🔔 Telegram вручную (тест)

Заменить `<TOKEN>` и `<CHAT_ID>`:

```
https://api.telegram.org/bot<TOKEN>/sendMessage?chat_id=<CHAT_ID>&text=Привет+от+бота
```
