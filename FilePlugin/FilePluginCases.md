# FilePlugin

 Этот [плагин](/documentation/plugins/) реализует функции для работы с файлами.

## Сontent
1. [Terms](#Terms)
    1. [Work with single file](#Work-with-single-file)
    2. [Work with files list](#Work-with-files-list)
    3. [Work with directory](#Work-with-directory)
    4. [Work with archive](#Work-with-archive)
    5. [Download and upload](#Download-and-upload)
2. [Installation and setting](#Installation-and-setting)

## Terms

### Work with single file

Используя плагин для работы с файлом вы можете выполнить операции: 

1. [Чтение](/documentation/plugins/filepluginapi#FileRead)
2. [Запись](/documentation/plugins/filepluginapi#FileWrite)
3. [Удаление](/documentation/plugins/filepluginapi#FileDelete)
4. [Перемещение](/documentation/plugins/filepluginapi#FileMove)
5. [Копирование](/documentation/plugins/filepluginapi#FileCopy)
6. [Переименовывание](/documentation/plugins/filepluginapi#FileRename)

### Work with files list

Используя плагин для работы с несколькими файлами вы можете выполнить операции: 

1. [Чтение](/documentation/plugins/filepluginapi#FilesListRead)
2. [Удаление](/documentation/plugins/filepluginapi#FilesListDelete)
3. [Перемещение](/documentation/plugins/filepluginapi#FilesListMove)
4. [Копирование](/documentation/plugins/filepluginapi#FilesListCopy)
5. [Переименовывание](/documentation/plugins/filepluginapi#FilesListRename)

### Work with directory

Используя плагин для работы с папками вы можете выполнить операции: 

1. [Создание](/documentation/plugins/filepluginapi#DirectoryCreate)
2. [Удаление](/documentation/plugins/filepluginapi#DirectoryDelete)
3. [Перемещение](/documentation/plugins/filepluginapi#DirectoryMove)
4. [Копирование](/documentation/plugins/filepluginapi#DirectoryCopy)
5. [Переименовывание](/documentation/plugins/filepluginapi#DirectoryRename)
6. [Получение списка файлов](/documentation/plugins/filepluginapi#DirectoryGetFiles)
7. [Получение списка директорий](/documentation/plugins/filepluginapi#DirectoryGetDirectories)

### Work with archive

Используя плагин для работы с архивами вы можете выполнить операции: 

1. [Архивация папки](/documentation/plugins/filepluginapi#DirectoryCompress)
2. [Архивация файлов](/documentation/plugins/filepluginapi#FilesCompress)
3. [Разархивация](/documentation/plugins/filepluginapi#FileUnсompress)

### Download and upload

Используя плагин для загрузки и скачивания файлов вы можете выполнить операции: 

1. [Скачивание файла](/documentation/plugins/filepluginapi#FileDownload)  
2. [Загрузка файла](/documentation/plugins/filepluginapi#FileUpload)

Используя плагин для загрузки и скачивания папок вы можете выполнить операции: 

1. [Скачивание папки](/documentation/plugins/filepluginapi#DirectoryDownload)
2. [Загрузка папки](/documentation/plugins/filepluginapi#DirectoryUpload)

## Installation and setting

Install nuget package:
- Для проектов на .Net Core: [WorkflowEngine.NETCore-FilesPlugin](https://www.nuget.org/packages/WorkflowEngine.NETCore-FilesPlugin/)  
- Для проектов на .Net Framework: [WorkflowEngine.NET-FilesPlugin](https://www.nuget.org/packages/WorkflowEngine.NET-FilesPlugin/)

*[How install nuget package in Visual studio for Windows](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)*

*[How install nuget package in Visual studio for Mac](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)*

*[How install nuget package in Rider](https://www.jetbrains.com/help/rider/Using_NuGet.html#browsing)*


Add the following namespaces to the usings section:
```C#
using OptimaJet.Workflow.Plugins;
```

Создайте обьект плагина:

```C#
 var filePlugin = new FilePlugin();
 ```
Подключите плагин к [WorkflowRuntime](/documentation/main-terms/runtime/)
```C#
var runtime = new WorkflowRuntime()...

runtime.WithPlugin(filePlugin);
```
