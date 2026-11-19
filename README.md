# Escape from Solonytsivka

A horror web game about me and my friends, stranded one night in Solonytsivka.

Уся гра — один файл `index.html`. Збірки немає: відкрив, поправив, задеплоїв.

Важливо: перші рядки index.html (`<!DOCTYPE html>`, `<meta charset>`, стиль `[hidden]{display:none!important}`) не видаляй — без них меню перекривають одне одного і кнопки не натискаються.

## Стек
- **Three.js r128** з CDN (cdnjs + `GLTFLoader` з jsdelivr) — 3D, звичайні скрипти, без модулів.
- **Vanilla JS + CSS**, без фреймворків.
- **Web Audio API** — музика, шипіння рації, звуки (синтезуються в коді) + записані голоси.
- **Ассети вшиті в файл як base64**: персонажі (GLB, авторіг), ніж, голоси (mp3), маска очей Роми. Через це в файлі є дуже довгі рядки — редактор може пригальмовувати на них.
- Налаштування й вивіски зберігаються в `localStorage` браузера.

## Вивіски
Свої картинки для вивісок клади в папку `signs/` з назвами зі списку в `signs/README.md` (наприклад `market_square.png`). Гра сама їх підхопить у всіх, хто відкриє сайт.

## Запуск локально
Через будь-який статичний сервер, наприклад: `npx serve .` і відкрити `http://localhost:3000`.

## Деплой на Vercel
- `npx vercel` у цій папці (Framework: Other, без build command, Output — корінь), або
- закинути папку в GitHub-репозиторій і підключити його у Vercel.

## Де що в index.html (шукай ці коментарі)
- `title screen v2`, `character select v2` — стилі меню
- `world` / `roads` / `the long 9-storey with the market` / `built at real coordinates` — карта
- `people` — персонажі (`makeGLBChar`, `animHuman`), `CHAR_GLB` / `CHAR_META` — моделі
- `SD (old blocky) characters` — квадратні персонажі
- `audio`, `main-menu theme`, `dread score`, `ambience`, `scares` — звук і страшилки
- `dialog`, `Roma's phone`, `recorded voice lines` (`VO`, `VOSEG`, `VOTEXT`) — діалоги й голоси
- `game state` — предмети, `stalkerReveal` (поява Роми), `caught` / `deathTick` (вбивство)
- `escapeDrive` — посадка в машину й фінал, `after the credits roll` — сцена в сараї
- `language` — тексти UA/EN, `settings`, `menu face`, `loop`
