# Деплой status.trace-logos.ru

Пошаговая инструкция по развёртыванию Upptime для Trace Logos.

## 1. Создать репозиторий

1. Открыть https://github.com/new (под аккаунтом `rafael-mansurov`)
2. Repository name: `upptime`
3. Visibility: **Public** (GitHub Pages и бейджи на бесплатном тарифе требуют публичный репозиторий)
4. Нажать **Create repository**

## 2. Залить файлы

Из папки `upptime/` этого проекта:

```bash
cd upptime
git init -b master
git add .upptimerc.yml .github/workflows/upptime.yml README.md DEPLOY.md
git commit -m "Initial Upptime config"
git remote add origin https://github.com/rafael-mansurov/upptime.git
git push -u origin master
```

Ветка должна называться `master` — воркфлоу триггерится на push в `master`, и Upptime по умолчанию коммитит историю туда же.

## 3. Создать Personal Access Token и добавить секрет

1. Открыть https://github.com/settings/tokens/new (classic token)
2. Note: `upptime`
3. Expiration: `No expiration` (или год — тогда поставить напоминание обновить)
4. Отметить scopes: **`repo`** (весь блок) и **`workflow`**
5. Нажать **Generate token**, скопировать значение
6. В репозитории `upptime`: **Settings → Secrets and variables → Actions → New repository secret**
   - Name: `GH_PAT`
   - Secret: вставить токен
   - Нажать **Add secret**

Обычный `GITHUB_TOKEN` не подходит: Upptime коммитит в репозиторий и обновляет воркфлоу — для этого нужен PAT со scope `workflow`.

## 4. Первый запуск воркфлоу

1. В репозитории открыть вкладку **Actions**
2. Если GitHub спросит — нажать **I understand my workflows, go ahead and enable them**
3. Слева выбрать **Upptime CI** → справа кнопка **Run workflow** → ветка `master` → **Run workflow**
4. Дождаться зелёной галочки (~2–5 минут). Upptime сам создаст ветку `gh-pages`, перепишет README бейджами и сгенерирует `api/` и `history/`

## 5. Включить GitHub Pages

После первого успешного запуска (ветка `gh-pages` должна уже существовать):

1. **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: `gh-pages`, папка `/ (root)`
4. **Save**

## 6. Настроить DNS

У DNS-провайдера домена `trace-logos.ru` добавить запись:

| Тип | Имя | Значение |
| --- | --- | --- |
| CNAME | `status` | `rafael-mansurov.github.io` |

Поле `cname: status.trace-logos.ru` в `.upptimerc.yml` уже задано — Upptime сам положит файл `CNAME` в ветку `gh-pages`.

## 7. Проверить результат

- Через несколько минут после настройки DNS открыть https://status.trace-logos.ru
- В **Settings → Pages** должна появиться галочка **Enforce HTTPS** — включить её, когда GitHub выпустит сертификат (может занять до часа после добавления CNAME)

## Когда появятся CDN и страница Figma-плагина

В `.upptimerc.yml` закомментированы два сайта (`cdn.trace-logos.ru`, `figma.trace-logos.ru`) — на 2026-06-11 эти поддомены не существуют в DNS. После их запуска раскомментировать соответствующие блоки в `sites:` и запушить в `master` — мониторинг подхватится автоматически.
