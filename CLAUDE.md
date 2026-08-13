# MeshNetBY Documentation - Context for Claude

## Общая информация о проекте

**MeshNetBY** — сообщество mesh-сети на базе Meshtastic и MeshCore в Минске и Беларуси.

- Сайт: https://mesh-net.by
- Статический сайт на Zensical (аналог MkDocs)
- Язык: русский
- Google Analytics: G-56FX0Y0S5B

## Структура проекта

```
web/
├── docs/                       # Контент сайта (Markdown)
│   ├── index.md               # Главная страница
│   ├── meshtastic/            # Раздел Meshtastic (6 страниц)
│   ├── meshcore/              # Раздел MeshCore (2 страницы)
│   ├── reference/             # Справочник (2 страницы)
│   ├── diy/                   # DIY (4 страницы)
│   ├── faq.md                 # Общий FAQ
│   └── map.md                 # Страница с картами
├── zensical.toml              # Конфигурация сайта и навигации
├── overrides/                 # Кастомные шаблоны
└── site/                      # Собранный сайт (не трогать)
```

## Навигация сайта

1. **Главная** (`index.md`)
2. **Meshtastic** (раздел)
   - start.md, channels.md, mqtt.md, backups.md, firmware.md, ringtones.md
3. **MeshCore** (раздел)
   - meshcore.md (основное руководство)
   - faq.md (FAQ специфичный для MeshCore)
4. **DIY** (раздел)
   - start.md, boards.md, antennas.md, power.md
5. **Справочник** (раздел)
   - comparison.md (сравнение Meshtastic vs MeshCore)
   - lora-metrics.md (общая информация про LoRa)
6. **Вопрос Ответ** (`faq.md`) - общий FAQ
7. **Карта** (`map.md`) - карты обеих платформ
8. **Telegram группа** (внешняя ссылка)

## Две платформы в сети

### Meshtastic
- Частота: **869.525 МГц**
- Preset: **MEDIUM_FAST**
- Region: **EU_868**
- Карта: https://map.mesh-net.by

### MeshCore
- Частота: **869.618 МГц**
- Preset: **EU/UK (Narrow)**
- Bandwidth: **62.5 кГц**
- SF: **8**, CR: **8**, TX Power: **22 дБм**
- Карта: https://meshcoretel.io/en/MSQ/map

**Важно:** Платформы несовместимы между собой!

## Стиль написания контента

### Форматирование
- Используй обычные заголовки `###` для вопросов в FAQ (НЕ `??? question`)
- Блоки `!!! tip`, `!!! warning`, `!!! info` для важных заметок
- Таблицы для сравнений и параметров
- Списки (нумерованные и маркированные) для инструкций

### Тон
- Дружелюбный, но профессиональный
- "Вы" (не "ты")
- Простым языком, избегай жаргона где можно
- Давай конкретные инструкции

### Ссылки
- Внутренние: `/meshtastic/start`, `/meshcore/meshcore`, `/reference/comparison`
- Внешние в Markdown: `[текст](url)`
- Для файлов используй относительные пути

## Важные ссылки и ресурсы

### Meshtastic
- Официальный сайт: https://meshtastic.org/

### MeshCore
- Flasher: https://flasher.meshcore.co.uk/
- Config: https://config.meshcore.io/
- Docs: https://docs.meshcore.io/
- GitHub: https://github.com/meshcore-dev/MeshCore
- Мастер настройки: https://script.google.com/macros/s/AKfycbzkfVERjCyLByiAKpyLwbyxAnIPMJkYJ7vIUeZ9_cPUMQx9Y_9WHDqCDy6YM8a_8eQP9w/exec

### Сообщество
- Telegram Минск: https://t.me/+urWsU1L2NDk2YzIy
- Telegram Брест: https://t.me/meshtastic_brest_868
- Telegram Гомель: https://t.me/meshtastic_gomel
- Telegram Витебск: https://t.me/meshtastic_vitebsk

## Правила SEO

### Обязательно
- ✅ H1 один на страницу (# в Markdown)
- ✅ Уникальный контент (не копировать с других сайтов)
- ✅ Внутренние ссылки между разделами
- ✅ Ключевые слова естественно в тексте
- ✅ Мета-описания где возможно

### Избегать
- ❌ Дублирование контента
- ❌ Переименование существующих URL
- ❌ Страницы без внутренних ссылок
- ❌ Копипаст с официальных сайтов

## Изменение навигации

Редактируй `zensical.toml`, секция `nav`:

```toml
nav = [
   { "Название" = "file.md" },           # Одна страница
   { "Раздел" = [                        # Раздел с подстраницами
        "folder/page1.md",
        "folder/page2.md"
    ]},
]
```

## Что НЕ делать

- ❌ НЕ упоминай meshcore-beacon.xyz (просили убрать)
- ❌ НЕ дублируй вопросы между общим FAQ и FAQ MeshCore
- ❌ НЕ используй collapsible блоки `??? question` в FAQ
- ❌ НЕ создавай файлы в `site/` (генерируется автоматически)

## Частые задачи

### Добавить новую страницу
1. Создай `.md` файл в нужной директории (`docs/meshtastic/`, `docs/meshcore/` и т.д.)
2. Добавь в навигацию в `zensical.toml`
3. Добавь ссылки на новую страницу с других релевантных страниц

### Обновить параметры сети
1. Главная страница: `docs/index.md` (секция "Платформы и настройки")
2. MeshCore: `docs/meshcore/meshcore.md` (секция "Радиопараметры")
3. Meshtastic: `docs/meshtastic/start.md`

### Изменить структуру разделов
1. Переместить файлы: `mv docs/old/file.md docs/new/`
2. Обновить навигацию в `zensical.toml`
3. Найти и обновить все ссылки: `grep -r "/old/" docs/`

## SEO: Редиректы старых URL

**Проблема:** Изменили структуру `/guides/*` → `/meshtastic/*`, `/meshcore/*`, `/reference/*`

**Решение:** Созданы HTML-редиректы в `docs/guides/*.html` с:
- Meta refresh (мгновенный редирект)
- JavaScript fallback
- Canonical URL
- Текстовая ссылка для пользователей

**Редиректы:**
- `/guides/start` → `/meshtastic/start`
- `/guides/channels` → `/meshtastic/channels`
- `/guides/mqtt` → `/meshtastic/mqtt`
- `/guides/backups` → `/meshtastic/backups`
- `/guides/firmware` → `/meshtastic/firmware`
- `/guides/ringtones` → `/meshtastic/ringtones`
- `/guides/lora-metrics` → `/reference/lora-metrics`
- `/guides/meshcore` → `/meshcore/meshcore`

## Текущая работа (последнее обновление)

**Дата:** 2026-08-13

**Что сделано:**
- Создан раздел MeshCore с основным руководством и FAQ
- Создан раздел "Справочник" со сравнением платформ и LoRa метриками
- Реорганизована навигация на верхнеуровневые разделы
- Убраны упоминания meshcore-beacon.xyz
- Добавлена информация про карту MeshCore на странице /map
- FAQ по MeshCore содержит только специфичные вопросы
- **Созданы HTML-редиректы для старых URL (SEO)**

**Структура установилась и готова к использованию.**
