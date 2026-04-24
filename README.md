# claude-humanizer-ru-skill

Skill для Claude Code: чистит русские тексты от типичных AI-штампов и опционально подгоняет под голос автора по образцам.

Адаптация [blader/humanizer](https://github.com/blader/humanizer) под русский.

## Что делает

Прогоняет текст через каталог из ~30 паттернов AI-стиля в русском (канцелярит, кальки с английского, раздутая значимость, чатбот-артефакты, hedging) и переписывает с учётом контекста.

### Контекстные режимы

- `tg-post` — пост в Telegram / соцсети
- `letter` — деловое письмо
- `personal` — личная переписка (заодно меняет тире `—` на дефис `-`)
- `copywriting` — текст для сайта
- `audit` — анализ чужого текста на признаки AI-генерации

### Не использовать для

КП, договоры, ТЗ, техдока — там структура и формальность важнее «человечности», и попытка «оживить» сделает только хуже.

## Установка

Linux / macOS:
```bash
git clone https://github.com/KondrashovDenis/claude-humanizer-ru-skill ~/.claude/skills/humanizer-ru
```

Windows (cmd):
```cmd
git clone https://github.com/KondrashovDenis/claude-humanizer-ru-skill %USERPROFILE%\.claude\skills\humanizer-ru
```

Windows (PowerShell):
```powershell
git clone https://github.com/KondrashovDenis/claude-humanizer-ru-skill $env:USERPROFILE\.claude\skills\humanizer-ru
```

## Использование

В Claude Code просто скажи что нужно — skill подхватится автоматически:

- «причеши этот текст»
- «убери AI-стиль»
- «прогони через humanizer»
- «проверь, не сгенерён ли этот текст AI»

Опционально укажи режим: «причеши как пост в ТГ», «как письмо клиенту», «это личная переписка».

## Voice calibration (опционально)

Положи 5–10 своих текстов в `voice-samples/` — посты, переписку, статьи, что не жалко. Skill сначала профилирует твой голос (длину фраз, любимые обороты, пунктуационные привычки), потом перепишет в твоей манере, а не в обобщённо-«человеческой».

Подробности — в `voice-samples/README.md`.

Файлы из этой папки в репозиторий не пушатся (`.gitignore` режет всё, кроме README).

## Структура

```
claude-humanizer-ru-skill/
├── SKILL.md           # основной файл skill (читается Claude Code)
├── patterns-ru.md     # каталог паттернов с примерами «было / стало»
├── voice-samples/     # сюда складывать свои образцы (опционально)
│   └── README.md
├── README.md
└── LICENSE
```

## Кредиты

Адаптация [blader/humanizer](https://github.com/blader/humanizer) (MIT).

Оригинал: 4-фазная методика (паттерны → переписка → калибровка под голос → самоаудит) и общая структура skill'а.

В русской версии: каталог паттернов переписан под русский (канцелярит, англицизмы, кальки, специфика чатбот-артефактов в RU), добавлены контекстные режимы и режим аудита.

## Лицензия

MIT
