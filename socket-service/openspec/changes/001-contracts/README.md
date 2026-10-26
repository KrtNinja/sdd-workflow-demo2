# socket-service — Change 001-contracts (заглушка)

Статус: не начато.
Slice: [001 Контракты](../../../../docs/task-transfer/slices/001-contracts.md)
ADR: [0001 Доставка событий](../../../../docs/adr/0001-task-transfer-event-delivery.md)
Закрывает: AC-001-1, AC-001-B1

Это место, где появится Change в репозитории socket-service. Настоящие proposal.md, specs/ и tasks.md
создаются just-in-time по реальному коду сервиса и удаляются перед мержем PR.

## Что должно появиться в коде socket-service
- contracts/socket/task-transferred.message.json — сообщение клиенту (задача, прежний и новый исполнитель с именем, `transferSeq`)
- подписка на contracts/events/task-transferred.realtime.schema.json из tasks-core

Владелец сообщения сокета; схему события берёт у tasks-core, своей копии не заводит.

## Как создать
```
/opsx:propose 001-contracts по <slice 001>
/opsx:apply
```
Откуда взять `<slice 001>` — см. подсказку в [changes.md](../../../../docs/task-transfer/changes.md#подсказка-откуда-агент-берёт-slice).
