Library Management System — Система управления библиотекой

Кроссплатформенное веб‑приложение для управления книгами, читателями и выдачами. Репозиторий организован как монорепозиторий с отдельными каталогами для backend и frontend, тестов и документации.

Содержимое:
- краткий обзор,
- структура проекта,
- запуск и разработка на Windows PowerShell,
- тестирование,
- переменные окружения,
- документация,
- рекомендации по развитию.

## Обзор

- **Backend**: Node.js/TypeScript (например, Express) — модульная архитектура по доменам: книги, читатели, выдачи. Работа с БД вынесена в `src/db/`.
- **Frontend**: React/TypeScript — точка входа `src/index.tsx`, разделение на `components/` и `pages/`.
- **Тесты**: разнесены по частям (`backend/tests/`, `frontend/tests/`).
- **Документация**: `docs/` с API, архитектурой и инструкциями.

## Структура проекта

```text
library-app/
  backend/
    src/
      app.ts
      db/
        index.ts
        models/
          book.model.ts
          loan.model.ts
          reader.model.ts
      modules/
        books/
          book.controller.ts
          book.routes.ts
          book.service.ts
        loans/
          loan.controller.ts
          loan.routes.ts
          loan.service.ts
        readers/
          reader.controller.ts
          reader.routes.ts
          reader.service.ts
    tests/
      books.test.ts
      loans.test.ts
      readers.test.ts
  docs/
    API.md
    ARCHITECTURE.md
    README.md
  frontend/
    public/
      index.html
    src/
      components/
      index.tsx
      pages/
    tests/
      app.test.ts
  README.md
  scripts/
```

Ключевые места:
- Модули работы с БД: `backend/src/db/` (+ модели в `backend/src/db/models/`).
- Интерфейс: `frontend/` (React, статика — `frontend/public/`).
- Тесты: `backend/tests/`, `frontend/tests/`.
- Документация: `docs/`.

## Быстрый старт (Windows PowerShell)

Требования:
- Node.js LTS и npm (`node -v`, `npm -v`).

Установка зависимостей (если в под‑проектах есть `package.json`):

```powershell
# Установка backend
cd backend
npm install
cd ..

# Установка frontend
cd frontend
npm install
cd ..
```

Запуск в режиме разработки (типичные скрипты — при наличии в `package.json`):

```powershell
# Backend (например, с nodemon)
cd backend
npm run dev

# В новой вкладке терминала — Frontend (React)
cd ../frontend
npm start
```

По умолчанию:
- Frontend: `http://localhost:3000` (если create‑react‑app/Vite).
- Backend: `http://localhost:4000` или `http://localhost:5000` (смотрите `backend/src/app.ts` и конфиги).

## Тестирование

Запуск unit‑тестов (пример для Jest/Vitest):

```powershell
# Backend
cd backend
npm test

# Frontend
cd ../frontend
npm test
```

Рекомендуется разделять unit и e2e. При добавлении e2e‑тестов — вынесите их в отдельный каталог `e2e/`.

## Переменные окружения

Создайте файлы `.env` в соответствующих каталогах. Пример для backend:

```env
# backend/.env
NODE_ENV=development
PORT=4000
DATABASE_URL=postgresql://user:password@localhost:5432/library
```

Для frontend можно использовать `.env`/`.env.local` (например, префикс `VITE_` или `REACT_APP_` в зависимости от сборщика):

```env
# frontend/.env
VITE_API_BASE_URL=http://localhost:4000
```

## Документация

- Описание API: `docs/API.md`
- Архитектура: `docs/ARCHITECTURE.md`
- Дополнительные материалы и гайды: `docs/README.md`

При наличии макетов интерфейса (например, Figma) добавьте ссылку в `docs/README.md`:

```text
Макет в Figma: https://www.figma.com/file/XXXXXXXX/Library-App
```

## Рекомендации по развитию

- Добавить каталоги: `backend/src/config/`, `backend/src/utils/`, `frontend/src/styles/`, `frontend/src/utils/`, `frontend/src/types/`.
- Настроить единые инструменты качества кода: ESLint, Prettier, EditorConfig.
- Добавить `.gitignore` и `LICENSE` в корне.
- Рассмотреть единый менеджмент зависимостей на корне (workspaces) при росте проекта.

## Лицензия

Добавьте выбранную лицензию в файл `LICENSE` в корне.


