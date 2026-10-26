# frontend — Change 001-contracts (заглушка)

Статус: не начато.
Slice: [001 Контракты](../../../../docs/task-transfer/slices/001-contracts.md)
ADR: [0001 Доставка событий](../../../../docs/adr/0001-task-transfer-event-delivery.md)
Закрывает: AC-001-1, AC-001-F1

Это место, где появится Change в репозитории frontend. Настоящие proposal.md, specs/ и tasks.md
создаются just-in-time по реальному коду сервиса и удаляются перед мержем PR.

## Что должно появиться в коде frontend
- типы клиента из tasks-core.openapi.yaml (tasks-core)
- типы сообщения из task-transferred.message.json (socket-service)

Контракты не владеет, только выводит из них типы.

## Как создать
```
/opsx:propose 001-contracts по <slice 001>
/opsx:apply
```
Откуда взять `<slice 001>` — см. подсказку в [changes.md](../../../../docs/task-transfer/changes.md#подсказка-откуда-агент-берёт-slice).
