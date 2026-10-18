# spinlid-uptime-monitor

Внешний uptime-монитор [SpinLid](https://spinlid.ru) — GitHub Actions каждые
5 минут проверяет:

- `https://spinlid.ru/api/v1/health` (ожидаем 200)
- `https://spinlid.ru/`

**Алерты**: падение → issue с меткой `uptime-alert` (владелец репозитория
получает GitHub push/e-mail); восстановление → issue закрывается
автоматически. Канал живёт на инфраструктуре GitHub — видит полное падение
хоста spinlid-prod (внутренний сторож `check_api_liveness` — нет).

Почему публичный репозиторий: scheduled-минуты для public-репо бесплатны
(uptime.yml в основном приватном репо выключен именно из-за платных минут).

Дублирование: на рабочей станции владельца дополнительно стоит «SpinLid
Watchdog» (TG через SSH-релей + GitHub) — см. COORDINATION основного репо.
