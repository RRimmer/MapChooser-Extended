# 🗺️ Mapchooser Extended

[![SourceMod](https://img.shields.io/badge/SourceMod-1.10+-blue.svg)](https://www.sourcemod.net/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.11.2-orange.svg)](RELEASE_NOTES.md)

**Форк модуля Mapchooser Extended для управления голосованием по выбору карт на серверах Source Engine (CS:GO, CS:S, L4D/L4D2)**

> 📌 Этот проект основан на [sourcemod-mapchooser-extended](https://github.com/Sneaks-Community/sourcemod-mapchooser-extended) от Sneaks Community

---

## ✨ Особенности

### Основной функционал
- 🗳️ **Система голосования по выбору карт** - позволяет игрокам голосовать за следующую карту
- 🎯 **Номинирование карт** - игроки могут номинировать каждую отдельную карту
- 🔄 **Чередование карт** - автоматическое переключение в конце раунда
- 🎬 **Рок-голосование** - возможность вернуться на текущую карту в начале раунда

### Улучшения в версии 1.11.2
- ✅ Обновлённый визуальный стиль сообщений в чате с префиксом `[MAP]`
- ✅ Полная поддержка русского языка (исправлены ошибки переводов)
- ✅ Добавлена библиотека `multicolors.inc` для работы с цветами
- ✅ Динамическая загрузка префикса из файла переводов
- ✅ Расширенная поддержка игр (включая Left4Dead 1 и 2)
- ✅ Звуковые эффекты отключены по умолчанию (опционально)
- 🔧 Улучшенная система определения типа игры

---

## 📋 Требования

### Для игровых серверов
- **SourceMod** версии 1.10 и выше
- **Поддерживаемые игры:**
  - Counter-Strike: Global Offensive (CS:GO)
  - Counter-Strike: Source (CSS)
  - Left 4 Dead (L4D)
  - Left 4 Dead 2 (L4D2)
  - Другие игры на Source Engine

### Для компиляции из исходников
- **SourceMod Compiler (spcomp)** версии 1.10+
- Файлы include из SourceMod SDK

---

## 🚀 Установка

### Быстрая установка (готовые плагины)

1. **Загрузите файлы** из папки `Mapchooser Extended 1.11.2 CSGO+CSS/`

2. **Скопируйте в директорию сервера:**
   ```
   Mapchooser Extended 1.11.2 CSGO+CSS/
   └── addons/sourcemod/    →  ваш_сервер/addons/sourcemod/
   └── cfg/sourcemod/       →  ваш_сервер/cfg/sourcemod/
   ```

3. **Перезагрузите сервер с помощью команды:**
   ```
   sm_plugins reload mapchooser_extended
   ```

### Установка с компиляцией

1. **Скопируйте файлы include:**
   ```
   addons/sourcemod/scripting/include/multicolors.inc  → ваш_include_folder/
   addons/sourcemod/scripting/include/multicolors/      → ваш_include_folder/
   ```

2. **Скомпилируйте плагины:**
   ```bash
   spcomp.exe mapchooser_extended.sp -o ../plugins/mapchooser_extended.smx
   spcomp.exe nominations_extended.sp -o ../plugins/nominations_extended.smx
   spcomp.exe rockthevote_extended.sp -o ../plugins/rockthevote_extended.smx
   spcomp.exe basetriggers.sp -o ../plugins/basetriggers.smx
   ```

3. **Для звуков (опционально):**
   - Переместите `mapchooser_extended_sounds.smx` из папки `disabled` в папку `plugins`

> 📖 Подробная инструкция: [INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md)

---

## 📁 Структура файлов

```
├── addons/sourcemod/
│   ├── configs/
│   │   └── mapchooser_extended/     # Конфигурационные файлы
│   │       ├── maps/                # Список карт по игре
│   │       └── sounds/              # Звуковые файлы
│   ├── plugins/
│   │   ├── mapchooser_extended.smx     # Основной плагин
│   │   ├── nominations_extended.smx    # Плагин номинирования
│   │   ├── rockthevote_extended.smx    # Плагин рок-голоса
│   │   ├── basetriggers.smx            # Базовые триггеры
│   │   └── disabled/
│   │       └── mapchooser_extended_sounds.smx  # Звуки (изолированы)
│   ├── scripting/
│   │   ├── *.sp                     # Исходные файлы плагинов
│   │   └── include/                 # Библиотеки (inc файлы)
│   └── translations/
│       └── *.phrases.txt            # Файлы переводов
└── cfg/sourcemod/
    └── mapchooser_extended.cfg      # Основная конфигурация
```

---

## ⚙️ Конфигурация

### Основной файл конфигурации
Отредактируйте `cfg/sourcemod/mapchooser_extended.cfg` для настройки:

```cfg
// Время голосования (в секундах)
sm_mapvote_time "15"

// Минимальное количество карт в списке голосования
sm_mapvote_endround_time "20"

// Показывать текущий рейтинг голосов
sm_mapvote_showrank "1"

// Процент голосов для автоматической смены карты
sm_mapvote_playerveto "1"
```

> 📖 Полная документация: [README_DOCUMENTATION.md](README_DOCUMENTATION.md)

---

## 📊 Что изменилось от оригинала

Детальное сравнение версий доступно в файлах документации:

| Функция | 1.11.1 | 1.11.2 |
|---------|--------|--------|
| Визуальный стиль | Базовый | [MAP] префикс с цветами |
| Поддержка русского | Частичная | Полная ✓ |
| Multicolors | ✗ | ✓ |
| Left4Dead | ✗ | ✓ |
| Звуки по умолчанию | Включены | Отключены |
| Динамический префикс | ✗ | ✓ |

> 📋 Подробное сравнение: [DETAILED_COMPARISON.md](DETAILED_COMPARISON.md)

---

## 📚 Документация

- **[README_DOCUMENTATION.md](README_DOCUMENTATION.md)** — Навигация по всей документации
- **[RELEASE_NOTES.md](RELEASE_NOTES.md)** — Новости версии 1.11.2
- **[INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md)** — Подробная инструкция установки
- **[CHANGELOG_1.11.2_RU.md](CHANGELOG_1.11.2_RU.md)** — Полный список изменений
- **[DETAILED_COMPARISON.md](DETAILED_COMPARISON.md)** — Техническое сравнение версий

---

## 🛠️ Разработка

### Компиляция плагинов

Используется встроенный компилятор SourceMod с поддержкой оптимизации:

```bash
spcomp.exe plugin.sp -i ./include -O2 -t4 -v2
```

**Флаги:**
- `-i` — путь к include файлам
- `-O2` — уровень оптимизации
- `-t4` — 4 потока компиляции
- `-v2` — подробный вывод

### Структура исходников

Все исходные файлы `.sp` находятся в папке `addons/sourcemod/scripting/`:

- `mapchooser_extended.sp` — ядро системы выбора карт
- `nominations_extended.sp` — система номинирования
- `rockthevote_extended.sp` — система рок-голоса
- `basetriggers.sp` — базовые системные триггеры

Include библиотеки:
- `mapchooser_extended.inc` — основной API
- `multicolors.inc` — работа с цветными сообщениями
- `nativevotes.inc` — система голосования

---

## 🤝 Благодарности

Спасибо проекту **[sourcemod-mapchooser-extended](https://github.com/Sneaks-Community/sourcemod-mapchooser-extended)** от **Sneaks Community** за отличную базу для этого форка.

---

## 📝 Лицензия

Этот проект распространяется под лицензией **MIT**. Подробнее см. файл LICENSE.

---

## 🔗 Полезные ссылки

- **Discord сервер Snapshots:** https://discord.gg/tWGJnE3DVU
- **SourceMod документация:** https://www.sourcemod.net/
- **Оригинальный проект:** https://github.com/Sneaks-Community/sourcemod-mapchooser-extended

---

## 💬 Отладка и помощь

Если у вас возникли проблемы:

1. Проверьте [INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md) раздел "Решение проблем"
2. Убедитесь что скопировали все файлы include
3. Проверьте логи сервера: `addons/sourcemod/logs/`
4. Используйте команду `sm plugins list` для проверки статуса плагинов

---

**Версия:** 1.11.2  
**Последнее обновление:** Март 2026  
**Исходная версия:** Sneaks-Community/sourcemod-mapchooser-extended
