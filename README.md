# Greensun — статический лендинг (деплой за 2–3 минуты)

Деплой возможен **без сборки** (один файл `index.html`). Ниже четыре быстрых способа.

---

## Вариант A — GitHub Pages (самый простой)

1) Создайте репозиторий, напр. `greensun-landing`.
2) Загрузите сюда файлы из папки (`index.html`, `404.html`, `.nojekyll`, и т.д.).  
   Проще всего — загрузить ZIP (см. ниже) и распаковать на GitHub.
3) В репозитории откройте **Settings → Pages** и:
   - *Source*: **Deploy from a branch**
   - *Branch*: **main** / корень (`/`)
4) Через 1–2 мин сайт будет доступен по адресу:  
   `https://<ваш_юзернейм>.github.io/greensun-landing/`

> Альтернатива: GitHub Actions workflow `.github/workflows/pages.yml` уже добавлен.  
> Можно включить Pages в **Settings → Pages → GitHub Actions** и пушнуть в `main`.

---

## Вариант B — Netlify (drag&drop)

1) Зайдите на https://app.netlify.com/ и авторизуйтесь.
2) Нажмите **"Add new site" → "Deploy manually"**.
3) Перетащите содержимое папки (или ZIP).  
   Netlify автоматически опубликует сайт. `netlify.toml` уже настроен.

---

## Вариант C — Vercel

1) На https://vercel.com/ создайте проект **"Import Project" → "Add New..."**.
2) Укажите репозиторий с этими файлами **или** выберите "**Other**" и загрузите папку вручную.
3) Vercel определит статический проект. Конфигурация `vercel.json` уже добавлена.

---

## Вариант D — S3 + CloudFront (минимум)

1) Создайте S3 bucket (включите "Static website hosting").
2) Скопируйте файлы в корень бакета (укажите index: `index.html`, error: `404.html`).
3) Включите **Block Public Access: off** для чтения, настройте **Bucket policy** (public-read).  
   (Рекомендуется CloudFront для HTTPS/кеша.)

---

## Кастомизация

- В `index.html` можно обновить контакты, ссылки на Brandbook, Презентацию, и т.д.
- Для подключения реального endpoint формы:
  - Найдите обработчик в конце файла (по `// Lead form (mock)`), замените логику на `fetch` к вашему URL.
- Для домена на GitHub Pages создайте файл `CNAME` с доменом и настройте DNS (CNAME на `username.github.io`).

---

Дата сборки: 2025-08-27 15:57:30
