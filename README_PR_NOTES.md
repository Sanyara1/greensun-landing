# Greensun landing — PR notes

This PR adds:
- **Кейсы** section (Сочи, п. Лазаревское: Павлова 2, Калараша 131)
- **Радиус: совокупная генерация** card with:
  - выбор центра (селектор объектов),
  - радиус (км),
  - чекбокс "Брать центр с карты" (Leaflet/Mapbox/Yandex/Google — при наличии),
  - чекбокс "Исключить свой объект",
  - кнопка "Синхронизировать",
  - счётчики: объектов, сумма МВт·ч/мес, доля Pro 10%, ₽/мес по текущему тарифу (#tariff).
- **api/objects.json** — статический источник данных для счётчика.

## How to switch to live monitoring later
Deploy a tiny backend (e.g., Cloudflare Worker) that authenticates to your monitoring provider and returns a simplified JSON list:
```json
[ { "id":"...", "name":"...", "lat": 0, "lon": 0, "kw": 0, "mwh": 0 } ]
```
Then set the endpoint in HTML prior to the radius script:
```html
<script>window.GSUN_OBJECTS_ENDPOINT='https://your-backend/objects';</script>
```
