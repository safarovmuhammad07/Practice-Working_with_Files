# Практическое задание: Консольный проект для работы с файловой системой

## Цель

Создать консольное приложение, которое предоставляет пользователю возможность выполнять различные операции с дисками, каталогами и файлами.

---

## Описание функциональности

### Главное меню

При запуске программы пользователь видит меню с доступными операциями:

1. Показать информацию о дисках
2. Управление каталогами
3. Управление файлами
4. Выход

### 1. Информация о дисках

При выборе этого пункта программа:

- Выводит список всех доступных дисков.
- Для каждого диска отображает:
  - Метку тома
  - Тип файловой системы
  - Общий размер диска
  - Доступное место
  - Состояние диска (готов/не готов)

### 2. Управление каталогами

При выборе этого пункта пользователь может:

- Создать новый каталог
- Удалить каталог (с проверкой существования)
- Показать содержимое каталога (файлы и подкаталоги)
- Показать свойства каталога:
  - Полный путь
  - Дата создания
  - Время последнего изменения

### 3. Управление файлами

При выборе этого пункта пользователь может:

- Создать новый файл и записать в него текст
- Прочитать содержимое файла
- Переименовать файл
- Удалить файл
- Показать свойства файла:
  - Имя
  - Полный путь
  - Размер
  - Дата создания

### 0. Выход

Завершает выполнение программы.

---

## Технические требования

1. Использовать классы:
   - `DriveInfo` для работы с дисками
   - `Directory` и `DirectoryInfo` для работы с каталогами
   - `File` и `FileInfo` для работы с файлами
2. Для операций ввода/вывода использовать `Console.ReadLine` и `Console.WriteLine`

---

## Пример структуры программы

```csharp
using System;
using System.IO;

while (true)
{
    Console.Clear();
    Console.WriteLine("Выберите действие:");
    Console.WriteLine("1. Показать информацию о дисках");
    Console.WriteLine("2. Управление каталогами");
    Console.WriteLine("3. Управление файлами");
    Console.WriteLine("0. Выход");
    Console.Write("Ваш выбор: ")
    string choice = Console.ReadLine();
    switch (choice)
    {
        case "1":
            ShowDriveInfo();
            break;
        case "2":
            ManageDirectories();
            break;
        case "3":
            ManageFiles();
            break;
        case "0":
            return;
        default:
            Console.WriteLine("Неверный выбор. Нажмите любую клавишу, чтобы продолжить.");
            Console.ReadKey();
            break;
    }
}

void ShowDriveInfo()
{
    Console.Clear();
    DriveInfo[] drives = DriveInfo.GetDrives();
    foreach (var drive in drives)
    {
        Console.WriteLine($"Диск: {drive.Name}");
        if (drive.IsReady)
        {
            Console.WriteLine($"  Метка тома: {drive.VolumeLabel}");
            Console.WriteLine($"  Тип файловой системы: {drive.DriveFormat}");
            Console.WriteLine($"  Общий размер: {drive.TotalSize} байт");
            Console.WriteLine($"  Доступное место: {drive.AvailableFreeSpace} байт");
        }
        else
        {
            Console.WriteLine("  Диск не готов.");
        }
    }
    Console.WriteLine("Нажмите любую клавишу, чтобы вернуться в меню.");
    Console.ReadKey();
}

void ManageDirectories()
{
    Console.Clear();
    Console.WriteLine("Управление каталогами:");
    Console.WriteLine("1. Создать каталог");
    Console.WriteLine("2. Удалить каталог");
    Console.WriteLine("3. Показать содержимое каталога");
    Console.WriteLine("4. Показать свойства каталога");
    Console.WriteLine("0. Назад");
    Console.Write("Ваш выбор: ");
    string choice = Console.ReadLine();
    // Реализуйте соответствующие операции
}

void ManageFiles()
{
    Console.Clear();
    Console.WriteLine("Управление файлами:");
    Console.WriteLine("1. Создать файл и записать текст");
    Console.WriteLine("2. Прочитать содержимое файла");
    Console.WriteLine("3. Переименовать файл");
    Console.WriteLine("4. Удалить файл");
    Console.WriteLine("5. Показать свойства файла");
    Console.WriteLine("0. Назад");
    Console.Write("Ваш выбор: ");
    string choice = Console.ReadLine();
    // Реализуйте соответствующие операции
}
```
