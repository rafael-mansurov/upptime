# Trace Logos Status

Мониторинг доступности сервисов [trace-logos.ru](https://trace-logos.ru) на базе [Upptime](https://upptime.js.org).

Страница статуса: **[status.trace-logos.ru](https://status.trace-logos.ru)**

## Аптайм

После первого запуска воркфлоу Upptime автоматически перепишет этот README и добавит сюда живые бейджи аптайма и времени отклика по каждому сайту. До первого запуска бейджи ниже показывают «unknown» — это нормально.

| Сервис | Статус | Аптайм |
| --- | --- | --- |
| [Главный сайт](https://trace-logos.ru) | ![Status](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Frafael-mansurov%2Fupptime%2Fmaster%2Fapi%2F-%2Fuptime.json) | ![Uptime](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Frafael-mansurov%2Fupptime%2Fmaster%2Fapi%2F-%2Fuptime-year.json) |
| [API (logos.json)](https://trace-logos.ru/logos.json) | ![Status](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Frafael-mansurov%2Fupptime%2Fmaster%2Fapi%2Fapi-logos-json%2Fuptime.json) | ![Uptime](https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Frafael-mansurov%2Fupptime%2Fmaster%2Fapi%2Fapi-logos-json%2Fuptime-year.json) |

## Как это работает

- GitHub Actions раз в час опрашивает все сайты из [`.upptimerc.yml`](.upptimerc.yml)
- История откликов коммитится в этот репозиторий
- При падении сайта автоматически открывается Issue и назначается на `rafael-mansurov`
- Статус-сайт публикуется через GitHub Pages из ветки `gh-pages`

Инструкция по развёртыванию: [DEPLOY.md](DEPLOY.md)
