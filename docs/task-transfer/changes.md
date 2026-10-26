# Передача задачи — OpenSpec Changes (заглушка)

Статус: не начато.

Здесь Changes нет и не будет. По процессу команды Change — строительные леса: он создаётся
just-in-time в репозитории сервиса, когда зависимости slice влиты, и удаляется перед мержем.
Постоянными остаются Dev Spec, slices, ADR, контракты и тесты с AC-ID.

## Следующий шаг: slice 001 «Контракты»

Четыре Change, по одному в каждом репозитории. Каждый делает тот, кто берёт эту половину slice:
вход у всех один (файл slice), содержимое разное — его пишут по коду своего репозитория.
Сценарии ссылаются на AC-ID slice, нового поведения не добавляют. PR ревьюят все стороны вместе.

В этом демо-репозитории папки сервисов изображают их репозитории:

| Репозиторий | Заглушка Change |
|---|---|
| tasks-core | [tasks-core/openspec/changes/001-contracts](../../tasks-core/openspec/changes/001-contracts/README.md) |
| socket-service | [socket-service/openspec/changes/001-contracts](../../socket-service/openspec/changes/001-contracts/README.md) |
| audit | [audit/openspec/changes/001-contracts](../../audit/openspec/changes/001-contracts/README.md) |
| frontend | [frontend/openspec/changes/001-contracts](../../frontend/openspec/changes/001-contracts/README.md) |

В каждом: `/opsx:propose 001-contracts по <slice 001>`, затем `/opsx:apply`.

## Пример: этап 7 на slice 003

Две половины — два Change. Оба остановились на JIT-вопросе: при чтении кода всплыло то,
чего нет в Dev Spec. Агент не решает сам, а спрашивает человека.

| Репозиторий | Change | JIT-вопрос |
|---|---|---|
| tasks-core | [003-transfer](../../tasks-core/openspec/changes/003-transfer/README.md) | пробелы по краям причины: обрезать или хранить как есть |
| frontend | [003-transfer](../../frontend/openspec/changes/003-transfer/README.md) | несохранённые правки в текущей вкладке при передаче |

## Подсказка: откуда агент берёт slice

Slice лежит в репозитории с доками, а Change создаётся в репозитории сервиса — там этого файла
нет. Команде нужно выбрать один способ и записать его в AGENTS.md каждого сервиса:

- **ссылка на файл в репозитории с доками** — `KrtNinja/sdd-workflow-demo2/docs/task-transfer/slices/001-contracts.md`;
- **копия slice в репозиторий сервиса** на время работы — удаляется вместе с Change;
- **общая папка docs**, подключённая ко всем репозиториям (submodule или монорепозиторий документации).

## Что вернётся сюда после мержа

- Решения, принятые в Changes, — в новые ADR (`docs/adr/`) или в описание PR.
- Грабли кодовой базы — в AGENTS.md соответствующего сервиса.
- Продуктовые вопросы, всплывшие при чтении кода, — в Dev Spec и новую строку AC в slice
  с пометкой «добавлен после JIT-вопроса».
- Отметка в [slices/README.md](slices/README.md), какие slices приняты.
