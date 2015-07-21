#Синхронизация хранилища 1С с репозиторием git

## Введение
Проект является глубоким рефакторингом утилиты v83unpack ([https://github.com/xDrivenDevelopment/v83unpack](https://github.com/xDrivenDevelopment/v83unpack)).

Изначально данный механизм представляет собой внешнюю обработку 1С:Предприятия, которая впоследствии была портирована на OneScript. [Исходные коды порта](https://github.com/xDrivenDevelopment/v83unpack/tree/develop/src/oscript) доступны в том же репозитории v83unpack.

Приложение *gitsync* представляет собой отдельное (standalone) приложение на 1Script, и предназначено для синхронизации хранилища конфигураций 1С с репозитарием git.

## Установка


1. Скопировать каталог **gitsync/src** на жесткий диск
2. Запустить приложение командой ```oscript.exe <каталог gitsync>\gitsync.os```

# Использование

## Подготовка нового репозитария

Запустить gitsync с параметрами ```gitsync init <каталог или файл хранилища> <локальный каталог git> [-email домен почты пользователей]```

Буден инициализирован новый репо и созданы необходимые файлы для синхронизации.

## Клонирование существующего пустого репо

Часто бывает, что удаленный репо уже создан и нужно наполнить его служебными файлами синхронизатора.

Запустить gitsync с параметрами ```gitsync clone <каталог или файл хранилища> <url-git> [локальный каталог git] [-email домен почты пользователей]```

Буден клонирован удаленный репо и созданы необходимые файлы для синхронизации, если их там еще нет.

## Синхронизация
Основной режим работы. Аргументы командной строки для запуска:

* <каталог или файл хранилища>
* <url-git> 
* [локальный каталог git]
* [-email домен почты пользователей]
* [-v8version маска версии 1С] - маска версии в стиле стартера (8.3 или 8.3.5 или 8.2.19.109)

Пример:

    cd local-git-repo
    gitsync c:\storage\zup http://github.com/myAccount/zup.git -v8version 8.3.6

  