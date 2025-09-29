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



