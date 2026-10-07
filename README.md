# SCL — игровой хаб для Telegram (frontend)

![Vue](https://img.shields.io/badge/Vue_3-4FC08D?logo=vuedotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)
![Pinia](https://img.shields.io/badge/Pinia-FFD859?logo=pinia&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)

Клиентская часть Telegram Mini App, в котором пользователи соревнуются в установке рекордов в классических играх: «Змейка», «Тетрис» и «Ну, погоди!». Все игры написаны с нуля на TypeScript, без игровых движков.

Серверная часть: [scl-backend](https://github.com/plrtp68217/scl-backend)

<!-- Cкриншоты или GIF, например: ![Меню](docs/menu.png) -->

## Возможности

- **Три игры, написанные с нуля** — игровая логика реализована на TypeScript в объектно-ориентированном стиле (классы `Board`, `Snake`, `Shape`, `Wolf`, `Egg` и др.), отрисовка и управление встроены в Vue-компоненты
- **Рекорды и рейтинг** — сохранение личных рекордов и таблица лучших игроков по каждой игре
- **Ежедневная активность** — награды за ежедневный вход в приложение
- **Задания** — вознаграждение за подписку на Telegram-каналы
- **Админ-панель** — статистика активности игроков по играм и за выбранный период, управление каналами
- **Интеграция с Telegram WebApp** — авторизация пользователя через данные Telegram
- Звуковое сопровождение, пауза, интерфейс под мобильные устройства
- Логирование действий пользователя для сбора статистики

## Стек

| Категория | Технологии |
|---|---|
| Фреймворк | Vue 3, Vue Router, Pinia |
| Язык | TypeScript |
| Сборка | Vite |
| HTTP | Axios |
| UI | Swiper, собственные компоненты и CSS-анимации |
| Деплой | Docker, Nginx |

## Структура проекта

```
src/
├── api/            # API-клиент (Axios), запросы к backend, типы и обработка ошибок
├── components/
│   ├── games/      # Игры: snake, tetris, wolf + общие утилиты
│   ├── views/      # Страницы: меню, игры, рейтинг, задания, админка
│   ├── UI/         # Переиспользуемые компоненты: модалки, кнопки, уведомления
│   └── ...
├── stores/         # Pinia-хранилища
├── telegram/       # Работа с Telegram WebApp API
├── logging/        # Логирование действий пользователя
└── common/         # Звук, форматирование и общие хелперы
router/             # Маршрутизация
```

## Запуск локально

Требуется Node.js 18+.

```bash
git clone https://github.com/plrtp68217/scl-frontend.git
cd scl-frontend
npm install
```

Создайте файл `.env` в корне проекта:

```env
VITE_API_URL=http://localhost:3000
```

Запуск в режиме разработки:

```bash
npm run dev
```

## Сборка и запуск в Docker

```bash
npm run build
docker build -t scl-frontend .
docker run -p 8080:80 scl-frontend
```

Приложение будет доступно на `http://localhost:8080`. Nginx настроен на отдачу SPA (все маршруты перенаправляются на `index.html`).

## Автор

Сергей Морозов — [Telegram](https://t.me/poleartop)
