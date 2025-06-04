import os
import subprocess
from pathlib import Path
import shutil


def convert_pdf_to_epub():
    # Настройки
    source_folder = Path("E:/PDF")  # Исходная папка с PDF
    output_root = Path("E:/EPUB")  # Корневая папка для EPUB
    calibre_path = "ebook-convert"  # Путь к Calibre

    # Проверка Calibre
    try:
        subprocess.run([calibre_path, "--version"],
                       check=True,
                       stdout=subprocess.PIPE,
                       stderr=subprocess.PIPE,
                       encoding='utf-8')
    except Exception as e:
        print(f"Ошибка: Calibre не найден ({e})")
        print("Установите Calibre: https://calibre-ebook.com")
        return

    # Проверка исходной папки
    if not source_folder.exists():
        print(f"Папка '{source_folder}' не существует!")
        return

    # Создаем корневую папку для EPUB
    output_root.mkdir(exist_ok=True)

    # Рекурсивный поиск PDF
    pdf_files = list(source_folder.rglob("*.pdf"))

    if not pdf_files:
        print("PDF файлы не найдены")
        return

    print(f"Найдено PDF файлов: {len(pdf_files)}")

    # Конвертация
    success = 0
    for pdf in pdf_files:
        # Определяем относительный путь для сохранения структуры
        relative_path = pdf.relative_to(source_folder)
        epub_path = output_root / relative_path.with_suffix(".epub")

        # Создаем целевую папку если нужно
        epub_path.parent.mkdir(parents=True, exist_ok=True)

        print(f"\nКонвертация: {relative_path}")

        try:
            # Запуск Calibre с обработкой UTF-8
            result = subprocess.run(
                [calibre_path, str(pdf), str(epub_path)],
                check=True,
                stdout=subprocess.PIPE,
                stderr=subprocess.PIPE,
                encoding='utf-8',
                errors='replace'
            )

            if epub_path.exists():
                print(f"Сохранено в: {epub_path.relative_to(output_root)}")
                success += 1
            else:
                print("Ошибка: файл не создан")

        except subprocess.CalledProcessError as e:
            print(f"Ошибка конвертации: {e.stderr}")

    print(f"\nГотово! Успешно конвертировано: {success}/{len(pdf_files)}")
    print(f"EPUB файлы сохранены в: {output_root}")


if __name__ == "__main__":
    convert_pdf_to_epub()
