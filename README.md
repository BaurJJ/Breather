# 🌬 Дыхание — PWA для Android

## Структура папки

```
breathing-app/
├── index.html        ← основное приложение
├── manifest.json     ← PWA манифест
└── README.md         ← эта инструкция
```

---

## Как добавить ВИДЕО-фон

1. Поместите ваш видеофайл в папку `breathing-app/`, например `bg.mp4`
2. В `index.html` найдите тег:
   ```html
   <video id="bg-video" ...>
     <!-- User: place your video file here as src="your-video.mp4" -->
   ```
3. Замените на:
   ```html
   <video id="bg-video" autoplay muted loop playsinline src="bg.mp4">
   ```
4. Рекомендуется видео: природа, морские волны, облака, лес. Длина 30-60 сек, зацикленное.

---

## Как добавить МУЗЫКУ

### Вариант 1 — прямо в приложении
- В приложении нажмите кнопку `+ Своя` и выберите MP3/OGG файл.

### Вариант 2 — встроить файлы заранее
1. Поместите MP3 файлы в папку, например:
   ```
   breathing-app/music/nature.mp3
   breathing-app/music/space.mp3
   breathing-app/music/rain.mp3
   breathing-app/music/bowl.mp3
   ```
2. В `index.html` найдите функцию `setMusicTrack()` и замените строку:
   ```js
   musicAudio.src = '';
   ```
   на:
   ```js
   const files = { nature: 'music/nature.mp3', space: 'music/space.mp3', rain: 'music/rain.mp3', bowl: 'music/bowl.mp3' };
   if (files[track]) { musicAudio.src = files[track]; musicAudio.play(); return; }
   ```

---

## Как установить на Android (как приложение)

### Способ 1 — через локальный сервер (USB-кабель)

1. Установите [Android Studio](https://developer.android.com/studio) или Python.
2. На компьютере запустите сервер в папке `breathing-app/`:
   ```bash
   python3 -m http.server 8080
   ```
3. Подключите телефон по USB, включите USB-отладку.
4. В браузере телефона перейдите на `localhost:8080`.
5. В Chrome — кнопка "три точки" → "Добавить на главный экран".

### Способ 2 — через файловый хостинг (GitHub Pages, Netlify)

1. Загрузите папку `breathing-app/` на [Netlify Drop](https://app.netlify.com/drop) (просто перетащите).
2. Получите URL типа `https://xyz.netlify.app`
3. Откройте в Chrome на Android → три точки → "Установить приложение".

### Способ 3 — через PWA Builder (APK/AAB файл)

1. Разместите приложение на Netlify или GitHub Pages.
2. Перейдите на [pwabuilder.com](https://pwabuilder.com)
3. Вставьте URL → "Build" → скачайте APK
4. Установите APK на Android (включите "Неизвестные источники")

---

## Звуковые сигналы

Встроены 4 тона (Web Audio API, не требует файлов):
- **Вдох** — 528 Гц (тон исцеления)
- **Задержка** — 396 Гц (освобождение)
- **Выдох** — 285 Гц (восстановление)
- **Пауза** — 174 Гц (основа)

---

## Практики по возрасту

| Практика | Возраст | Описание |
|----------|---------|----------|
| Детское спокойствие | 5–12 | Мягкое дыхание 3с/5с |
| Квадратное дыхание | 8+ | 4-4-4-4, армейская техника |
| 4-7-8 Расслабление | 12+ | Снятие тревоги, сон |
| Баланс для подростков | 13–20 | Стресс перед экзаменами |
| Когерентное дыхание | 14+ | 5 вдохов/мин |
| Активация (Вим Хоф) | 18–65 | Энергия, иммунитет |
| Мягкое восстановление | 55+ | Давление, сердечный ритм |
