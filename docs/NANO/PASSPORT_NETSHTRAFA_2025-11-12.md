# PASSPORT — SaaS NetShtrafa (2025-11-12)

## Суть
Лендинг + опрос для селлеров (риск штрафов/блокировок). Уведомления в TG админу. Интеграция с Дениской (STATE/metrics).

## Пути/Порты/Юнит
- Код (runtime): /opt/netshtrafa
- Репозиторий (git): /root/projects/netshtrafa  → origin: git@github.com:Alexandr123456098/NetShtrafa.git (main)
- Сервис: netshtrafa.service
- Flask порт: 18085 (local)
- nginx публикация: 8085 → 127.0.0.1:18085
- Ping: /ping (JSON)

## ENV
- /opt/netshtrafa/netshtrafa.env
  - PROJECT_NAME=netshtrafa
  - HOST=0.0.0.0
  - FLASK_PORT=18085
  - DB_PATH=/opt/netshtrafa/netshtrafa.db
  - BOT_TOKEN=8154085903:AAHrUfemsr4GhYmVe5JfcbIPnzgHTLeHuYg
  - ADMIN_ID=1079011202
  - DENISKA_STATE_PATH=/root/secrets/persobi_global_state.json

## Команды сервиса
- systemctl status netshtrafa.service
- systemctl restart netshtrafa.service
- journalctl -u netshtrafa.service -f -n 50

## Снапшоты
- /root/snapshots/netshtrafa_*.tgz
- Рекомендация: включено ручное создание после правок.

## Проверки
- curl -s http://127.0.0.1:18085/ping | jq .
- curl -s http://127.0.0.1:8085/ping | jq .   (через nginx)

## Дениска
- /api/services показывает: name=netshtrafa, status=Active, origin=.../NetShtrafa.git
- /root/bin/deniska-status.sh отдаёт netshtrafa с Active/clean.
