# Regions & Scopes в MeshCore

## Что такое Regions и Scopes

**Regions (регионы)** и **Scopes (зоны)** — это система организации mesh-сети MeshCore по географическим областям.

**Зачем это нужно:**

- Оптимизация трафика — сообщения не распространяются туда, где их никто не ждёт
- Снижение нагрузки на эфир — репитеры пересылают только релевантные пакеты
- Возможность создавать локальные сети по городам

**Иерархия:** Регионы можно организовать в дерево:
```
by (Беларусь)
└── minsk (Минск)
```

---

## Настройки для сети MeshNetBY

Для подключения к сети MeshCore в Минске используйте следующие настройки:

### Региональная схема

```
Беларусь (by)
└── Минск (minsk)
```

---

## Настройка Repeater (ретранслятор)

### CLI команды для репитера

Подключитесь к устройству через serial-консоль и выполните:

```bash
region allowf *
region def by minsk
region allowf by
region allowf minsk
region save
```

### Что делают команды

| Команда | Описание |
|---------|----------|
| `region allowf *` | Сохраняет совместимость со старыми сообщениями без scope |
| `region def by minsk` | Задаёт дерево regions одной строкой (для прошивки 1.16+) |
| `region allowf by` | Разрешает пересылать flood-пакеты с region `by` (Беларусь) |
| `region allowf minsk` | Разрешает пересылать flood-пакеты с region `minsk` (Минск) |
| `region save` | Сохраняет изменения после перезагрузки устройства |

!!! warning "Важно"
    Команда `region allowf *` не ломает regions, а сохраняет совместимость со старыми сообщениями без scope на период миграции сети.

### Альтернативный вариант через `region put`

То же дерево regions, но через отдельные команды. Полезно для совместимости и ручной проверки:

```bash
region allowf *
region put by
region put minsk by
region allowf by
region allowf minsk
region save
```

---

## Настройка Companion (клиент)

### Общий принцип

Companion нужно настроить на работу с regions вашего города. Добавьте два scope:

- **by** — общий scope для всей Беларуси
- **[код_города]** — scope вашего города (см. список ниже)

Установите scope вашего города как **default scope**.

### Пример для Минска

Если вы в **Минске**, добавьте следующие scopes:

- **by** — Беларусь
- **minsk** — Минск

**Default scope:** `minsk`

### Настройки для других областных городов

**Брест:**
- Scopes: `by`, `brest`
- Default scope: `brest`

**Гомель:**
- Scopes: `by`, `gomel`
- Default scope: `gomel`

**Гродно:**
- Scopes: `by`, `grodno`
- Default scope: `grodno`

**Витебск:**
- Scopes: `by`, `vitebsk`
- Default scope: `vitebsk`

**Могилёв:**
- Scopes: `by`, `mogilev`
- Default scope: `mogilev`

### Как настроить в приложении

1. Откройте приложение MeshCore
2. Зайдите в настройки устройства
3. Найдите раздел **Regions / Scopes**
4. Добавьте scopes: `by` и код вашего города (см. выше)
5. Установите **Default scope** — код вашего города
6. Для каждого группового чата можно отдельно выбрать scope в настройках чата

### Что такое Default scope

Default scope работает как запасной вариант, если у группового чата не выбран свой scope.

!!! tip "Рекомендация"
    Scope задаётся отдельно для каждого группового чата. **Scope группы важнее default scope.**
    
    Для важных групп в Companion лучше явно задать scope самой группы, а не полагаться только на default scope.

---

## Мастер настройки

Для автоматического подбора команд в зависимости от вашего устройства, региона и прошивки используйте:

**[Мастер настройки Regions & Scopes](https://script.google.com/macros/s/AKfycbzkfVERjCyLByiAKpyLwbyxAnIPMJkYJ7vIUeZ9_cPUMQx9Y_9WHDqCDy6YM8a_8eQP9w/exec)**

Мастер поможет:
- Выбрать тип устройства (Companion, Repeater, Room server)
- Указать вашу региональную схему
- Выбрать версию прошивки
- Получить готовые CLI-команды для копирования

---

## Структура regions для областных городов Беларуси

Для сети MeshCore в Беларуси используется простая двухуровневая структура:

```
by (Беларусь)
├── minsk (Минск)
├── brest (Брест)
├── gomel (Гомель)
├── grodno (Гродно)
├── vitebsk (Витебск)
└── mogilev (Могилёв)
```

### Настройки для других областных центров

Если вы создаёте сеть в другом областном городе, используйте команды по аналогии с Минском:

**Брест:**
```bash
region allowf *
region def by brest
region allowf by
region allowf brest
region save
```

**Гомель:**
```bash
region allowf *
region def by gomel
region allowf by
region allowf gomel
region save
```

**Гродно:**
```bash
region allowf *
region def by grodno
region allowf by
region allowf grodno
region save
```

**Витебск:**
```bash
region allowf *
region def by vitebsk
region allowf by
region allowf vitebsk
region save
```

**Могилёв:**
```bash
region allowf *
region def by mogilev
region allowf by
region allowf mogilev
region save
```

!!! tip "Рекомендация"
    Используйте название областного центра как scope. Это обеспечивает простую и понятную структуру сети по всей Беларуси.

---

## Проверка настроек

После настройки regions можно проверить конфигурацию:

```bash
region list        # Показать все настроенные regions
region info        # Показать текущую конфигурацию
```

---

## Дополнительные ресурсы

- [Основное руководство MeshCore](/meshcore/meshcore)
- [FAQ по MeshCore](/meshcore/faq)
- [Мастер настройки Regions & Scopes](https://script.google.com/macros/s/AKfycbzkfVERjCyLByiAKpyLwbyxAnIPMJkYJ7vIUeZ9_cPUMQx9Y_9WHDqCDy6YM8a_8eQP9w/exec)
- [Документация MeshCore](https://docs.meshcore.io/)
