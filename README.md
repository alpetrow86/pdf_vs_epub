# PDF to EPUB Converter

Автоматический конвертер PDF-файлов в формат EPUB с сохранением структуры папок. Использует движок Calibre для качественного преобразования документов.

## Особенности
- 🗂 Рекурсивная обработка вложенных папок
- 📂 Сохранение оригинальной структуры каталогов
- ✅ Автопроверка наличия Calibre
- 📊 Подробная статистика конвертации
- 💻 Поддержка путей с пробелами и спецсимволами

## Требования
1. [**Python 3.6+**](https://www.python.org/downloads/)
2. [**Calibre**](https://calibre-ebook.com) (установите и добавьте в PATH)
3. Установите зависимости:
   ```bash
   pip install pathlib shutil

Настройка

    Откройте скрипт в текстовом редакторе

    Измените пути (оригинальные настройки):
    python

    source_folder = Path("E:/PDF")    # Ваша папка с PDF
    output_root = Path("E:/EPUB")      # Папка для сохранения EPUB

    Сохраните изменения

Запуск
bash

python pdf_to_epub.py

Пример вывода

Найдено PDF файлов: 42

Конвертация: Books/Programming/Python.pdf
Сохранено в: Books/Programming/Python.epub

Конвертация: Articles/Data Science.pdf
Сохранено в: Articles/Data Science.epub

Готово! Успешно конвертировано: 40/42
EPUB файлы сохранены в: E:/EPUB

Структура проекта

E:/PDF/                          # Исходная папка
├── Category 1/
│   ├── Document1.pdf
│   └── Document2.pdf
└── Category 2/
    └── Book.pdf

E:/EPUB/                         # Результат (автосоздание)
├── Category 1/
│   ├── Document1.epub
│   └── Document2.epub
└── Category 2/
    └── Book.epub

Возможные проблемы

    Calibre не найден:

        Убедитесь, что Calibre установлен

        Добавьте путь к Calibre в системный PATH

        Или укажите полный путь в скрипте:
        python

    calibre_path = "C:/Program Files/Calibre2/ebook-convert.exe"

Ошибки кодировки:

    Скрипт автоматически обрабатывает UTF-8

    Для сложных случаев добавьте в команду:
    python

    env = os.environ.copy()
    env['PYTHONIOENCODING'] = 'utf-8'
    # и передайте в subprocess: env=env

Поврежденные PDF:

    Некоторые файлы могут не конвертироваться

    Попробуйте открыть их в Calibre вручную
