# SDD workflow demo 2: передача задачи

Второй живой пример Spec-Driven Development для команды — фича на несколько сервисов.
Фраза **«Передача задачи на другого пользователя»** превращается в Dev Spec, вертикальные slices
с разбивкой по сервисам (frontend, tasks-core, audit, socket-service), ADR о доставке событий
и заглушки OpenSpec Change.

Первый пример — поиск по интернет-магазину (фронт + один бэкенд): [sdd-workflow-demo](https://github.com/KrtNinja/sdd-workflow-demo).

**Кликабельная схема:** откройте `index.html` (или GitHub Pages этого репозитория).
По клику на блок открывается соответствующий файл.

## Чем отличается от первого примера

- **Несколько сервисов.** Половина slice — это сервис: на каждый свой Change и PR, slice принят, когда влиты все.
- **Стыки сервисов в brainstorming.** Отдельный блок вопросов: синхронно или через брокер, что при сбое, порядок, дубли.
- **ADR до кода.** Гарантированная и упорядоченная доставка событий (outbox, Kafka, `transferSeq`) решена до старта slices, которые от неё зависят.
- **Контракты у владельцев.** У каждого сервиса свои; событие принадлежит тому, кто его публикует.

## Процесс

1. **Brainstorming** — продукт, сервер и стыки сервисов. Решает человек.
2. **Dev Spec** — только поведение, FR/NFR с примерами. *Checkpoint 1.*
3. **Slices** — вертикальная нарезка, AC в блоках WHEN/THEN, review-slices. *Checkpoint 2.*
4. **ADR** — технические решения, без которых нельзя начать slices.
5. **Slice 001 — контракты в коде** каждого сервиса. Ревьюят все стороны вместе.
6. **Реализация** — по сервису: slice → свой Change → PR.
7. **Проверка фичи** — e2e на собранном приложении со всеми сервисами.
8. **Мерж** — Change удаляются, остаются спека, slices, ADR, контракты и тесты с AC-ID.

## Где что лежит

| Что | Где | Живёт |
|---|---|---|
| Правила процесса | [AGENTS.md](AGENTS.md) | постоянно |
| Протокол решений | [docs/task-transfer/brainstorming.md](docs/task-transfer/brainstorming.md) | постоянно |
| Бизнес-поведение | [docs/task-transfer/spec.md](docs/task-transfer/spec.md) | постоянно |
| Технические решения | [docs/adr/](docs/adr/0001-task-transfer-event-delivery.md) | постоянно |
| План и приёмка | [docs/task-transfer/slices/](docs/task-transfer/slices/README.md) | постоянно |
| Change | репозиторий сервиса → здесь [заглушки](docs/task-transfer/changes.md) в папках `tasks-core/`, `audit/`, `socket-service/`, `frontend/` | удаляется перед мержем |

## Как обновить страницу

После правки любого `.md`:

```bash
node scripts/build.mjs   # пересобирает assets/content.js
```

Страница работает и как локальный файл, и на GitHub Pages
(Settings → Pages → Deploy from branch → `main` / root).
