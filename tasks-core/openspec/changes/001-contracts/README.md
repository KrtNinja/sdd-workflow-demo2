# tasks-core — Change 001-contracts (заглушка)

Статус: не начато.
Slice: [001 Контракты](../../../../docs/task-transfer/slices/001-contracts.md)
ADR: [0001 Доставка событий](../../../../docs/adr/0001-task-transfer-event-delivery.md)
Закрывает: AC-001-1, AC-001-B1

Это место, где появится Change в репозитории tasks-core. Настоящие proposal.md, specs/ и tasks.md
создаются just-in-time по реальному коду сервиса и удаляются перед мержем PR.

## Что должно появиться в коде tasks-core
- contracts/tasks-core.openapi.yaml — поиск получателя, передача задачи, ошибки
- contracts/events/task-transferred.audit.schema.json — событие для audit (с `transferSeq`)
- contracts/events/task-transferred.realtime.schema.json — событие для socket-service (с `transferSeq`)
- application/ports/ProjectMembers.ts — порт к user-core
- domain/errors/TaskTransferErrors.ts — NOT_ASSIGNEE, TASK_CLOSED, RECIPIENT_NOT_ELIGIBLE, SELF_TRANSFER, INVALID_REASON, MEMBERS_UNAVAILABLE, TASK_TRANSFERRED
- tests/fixtures/task-transfer.ts — fixtures из slice

Владелец openapi и обеих схем событий; формат `transferSeq` и ключа Kafka — по ADR-0001.

## Как создать
```
/opsx:propose 001-contracts по <slice 001>
/opsx:apply
```
Откуда взять `<slice 001>` — см. подсказку в [changes.md](../../../../docs/task-transfer/changes.md#подсказка-откуда-агент-берёт-slice).
