# FilePlugin

 Этот [плагин](/documentation/plugins/) реализует функции для работы с файлами.

## Сontent

1. [Actions](#Actions)
    1. [FileRead](#FileRead)
    2. [FileWrite](#FileWrite)
    3. [FileDelete](#FileDelete)
    4. [FileDownload](#FileDownload)  
    5. [FileUpload](#FileUpload)
    6. [FileMove](#FileMove)
    7. [FileCopy](#FileCopy)
    8. [FileRename](#FileRename)
    9. [FilesListRead](#FilesListRead)
    10. [FilesListDelete](#FilesListDelete)
    11. [FilesListMove](#FilesListMove)
    12. [FilesListCopy](#FilesListCopy)
    13. [FilesListRename](#FilesListRename)
    14. [DirectoryCreate](#DirectoryCreate)
    15. [DirectoryDelete](#DirectoryDelete)
    16. [DirectoryMove](#DirectoryMove)
    17. [DirectoryDownload](#DirectoryDownload)
    18. [DirectoryUpload](#DirectoryUpload)
    19. [DirectoryCopy](#DirectoryCopy)
    20. [DirectoryRename](#DirectoryRename)
    21. [DirectoryGetFiles](#DirectoryGetFiles)
    22. [DirectoryGetDirectories](#DirectoryGetDirectories)
    23. [DirectoryCompress](#DirectoryCompress)
    24. [FilesCompress](#FilesCompress)
    25. [FileUnсompress](#FileUnсompress)
3. [Conditions](#Conditions)
    1. [FileExists](#FileExists)
    2. [FilesListExists](#FilesListExists)
    3. [DirectoryExists](#DirectoryExists)
4. [Elements](#Elements)
    1. [ParameterPurpose](#ParameterPurpose)
    2. [Protocol](#Protocol)
    3. [ParameterType](#ParameterType)
    4. [Masks](#Masks)
    5. [ArchiveType](#ArchiveType)

## Actions

Read about [actions](/documentation/scheme/actions/).

### FileRead

[Table of contents](#Сontent)

Чтение данных из файла в заданный [parameter](/documentation/scheme/parameters/).

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу

**`Parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в который будет считано содержимое файла.

**`Parameter purpose`** : [ParameterPurpose](#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

**`Parameter type`** : [ParameterType](#ParameterType) [**\***](#* 'Required parameter')

Задает тип в который происходит чтение. 

**`File mode`** : [FileMode](https://docs.microsoft.com/en-us/dotnet/api/system.io.filemode?view=netframework-4.8) [**\***](#* 'Required parameter')

Specifies how the operating system should open a file.

**`File access`** : [FileAccess](https://docs.microsoft.com/en-us/dotnet/api/system.io.fileaccess?view=netframework-4.8) [**\***](#* 'Required parameter')

Defines constants for read, write, or read/write access to a file.

**`File share`** : [FileShare](https://docs.microsoft.com/ru-ru/dotnet/api/system.io.fileshare?view=netframework-4.8) [**\***](#* 'Required parameter')

Contains constants for controlling the kind of access other [FileStream](https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream?view=netframework-4.8) objects can have to the same file.

**`Buffer size`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) [**\***](#* 'Required parameter')

Размер буфера при чтении данных.

Default value: 4096

### FileWrite

[Table of contents](#Сontent)

Запись данных в файл.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу

**`Text`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Текст для записи в файл.

**`File mode`** : [FileMode](https://docs.microsoft.com/en-us/dotnet/api/system.io.filemode?view=netframework-4.8) [**\***](#* 'Required parameter')

Specifies how the operating system should open a file.

**`File access`** : [FileAccess](https://docs.microsoft.com/en-us/dotnet/api/system.io.fileaccess?view=netframework-4.8) [**\***](#* 'Required parameter')

Defines constants for read, write, or read/write access to a file.

**`File share`** : [FileShare](https://docs.microsoft.com/ru-ru/dotnet/api/system.io.fileshare?view=netframework-4.8) [**\***](#* 'Required parameter')

Contains constants for controlling the kind of access other [FileStream](https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream?view=netframework-4.8) objects can have to the same file.

### FileDelete

[Table of contents](#Сontent)

Удаление файла по указанному пути.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу, который будет удален.

### FileDownload

[Table of contents](#Сontent)

Скачивание файла с указанного адреса на компьютер, используя выбранный [protocol](#Protocol).

**Параметры:**

**`Protocol`** : [Protocol](#Protocol) [**\***](#* 'Required parameter')

Задает протокол, который будет использован при скачивании файлов.

Default value: FTP

**`User name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Port`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

An int32 greater than zero that contains the port to be used on host.

*Если не установлен - будет установлен автоматически.*

**`URL`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

The Uri the request is sent to. Ипользуется для HTTP/HTTPS протоколов

**`Host`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Only for FTP/FTPS [protocols](#Protocol). Адрес сервера, куда будет отправлен запрос.

**`Remote path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Only for FTP/FTPS [protocols](#Protocol). Путь к файлу на сервере.

**`Local path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь на компьютере куда будет скачен файл.

### FileUpload

[Table of contents](#Сontent)

Загрузка файла с компьютера на указанный адрес, используя выбранный [protocol](#Protocol).

**Параметры:**

**`Protocol`** : [Protocol](#Protocol) [**\***](#* 'Required parameter')

Задает протокол, который будет использован при скачивании файлов.

**`User name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Port`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

An int32 greater than zero that contains the port to be used on host.

*Если не установлен - будет установлен автоматически.*

**`Host`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Адрес сервера, куда будет отправлен запрос.

**`Remote path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу на сервере.

**`Local path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь на компьютере куда будет скачен файл.

### FileMove

[Table of contents](#Сontent)

Перемещение файла.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу.

**`Path for move`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь куда будет перемещен файл (включая имя и расширение).

### FileCopy

[Table of contents](#Сontent)

Копирование файла по указанному пути.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу.

**`Path for copy`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь куда будет скопирован файл (включая имя и расширение).

### FileRename

[Table of contents](#Сontent)

Переименовывание файла.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу.

**`New path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу с новым именем(включая имя и расширение).

### FilesListRead

[Table of contents](#Сontent)

Чтение списка файлов в один или несколько [parameter](/documentation/scheme/parameters/).

**Параметры:**

**`Files list read`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список файлов, содержимое которых нужно скопировать в указанные параметры.

  Example:  file path 1 => parameter name 1; file path 2, file path 3, file path 4 => parameter name 2

  Содержимое файла «file path 1» будет скопировано в параметр «parameter name 1»

  Содержимое файлов «file path 2», «file path 3», «file path 4» будет скопировано в параметр «parameter name 2»

  Данные записываются в [parameter](/documentation/scheme/parameters/) в виде словаря:

  ```C#
  //синхронная работа с параметром
    var data1 = processInstance.GetParameter<Dictionary<string, string>("parameter name 1");

  //асинхронная работа с параметром
  var data2 = await processInstance.GetParameterAsync<Dictionary<string, string>("parameter name 2").ConfigureAwait(false);
  ```

**`Parameter purpose`** : [ParameterPurpose](#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

**`Identify by full name`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter') 

Флаг наименования путей: если `true` - в качестве ключа в словаре будет использоваться полное имя файла и путь к нему; если `false` -  в качестве ключа в словаре будет использоваться только имя файла без расширения

*Добавление в словарь файлов с одинаковым именем вызовет исключение.*

Default value: true

**`Parameter type`** : [ParameterType](#ParameterType) [**\***](#* 'Required parameter')

Задает тип в который происходит чтение. 

**`List files mode`** : [FileMode](https://docs.microsoft.com/en-us/dotnet/api/system.io.filemode?view=netframework-4.8) [**\***](#* 'Required parameter')

Specifies how the operating system should open a files.

**`List files access`** : [FileAccess](https://docs.microsoft.com/en-us/dotnet/api/system.io.fileaccess?view=netframework-4.8) [**\***](#* 'Required parameter')

Defines constants for read, write, or read/write access to files.

**`List files share`** : [FileShare](https://docs.microsoft.com/ru-ru/dotnet/api/system.io.fileshare?view=netframework-4.8) [**\***](#* 'Required parameter')

Contains constants for controlling the kind of access other [FileStream](https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream?view=netframework-4.8) objects can have to the same file.

**`Buffer size`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) [**\***](#* 'Required parameter')

Размер буфера при чтении данных.

Default value: 4096

### FilesListDelete

[Table of contents](#Сontent)

Удаление списка файлов.

**Параметры:**

**`Files list delete`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей к файлам для удаления, разделенных запятыми.

  Example:  file path 1, file path 2

  Файлы «file path 1», «file path 2» будут удалены.

### FilesListMove

[Table of contents](#Сontent)

Перемещение списка файлов.

**Параметры:**

**`Files list move`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей файлов и новых путей.
 Example: file path 1 => path for move 1, file path 2 => path for move 2

  Файл «file path 1», будет перемещен в «path for move 1»,
  файл «file path 2», будет перемещен в «path for move 2».

### FilesListCopy

[Table of contents](#Сontent)

Копирование списка файлов.

**Параметры:**

**`Files list copy`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей файлов и путей для копирования путей.

 Example: file path 1 => path for copy 1, filePath2 => path for copy 2.

  Копия файла «file path 1» будет создана по пути «path for copy 1»,
  копия файла «file path 2», будет перемещен в «path for copy 2».

### FilesListRename

[Table of contents](#Сontent)

Переименовывание списка файлов.

**Параметры:**

**`Files list rename`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей файлов и путей с новыми именами.

Example: file path 1 => file new path 1, file path 2 => file new path 2.

  Файл «file path 1», будет переименован и перемещен в «file new path»,
  файл «file path 2», будет переименован и перемещен в «file new path 2».

### DirectoryCreate

[Table of contents](#Сontent)

Создание папки.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь создаваемой папки.

### DirectoryDelete

[Table of contents](#Сontent)

Удаление папки.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь удаляемой папки.

**`With files and sub directory`**

Флаг, удалять ли вложенные папки и файлы:

  - true - папка будет удалена с вложенными элементами.
  - false -  если папки содержит вложенные элементы - она не будет удалена.

### DirectoryDownload

[Table of contents](#Сontent)

— Скачивание директории с указанного адреса на компьютер, используя выбранный [protocol](#Protocol).

**Параметры:**

**`Protocol`** : [Protocol](#Protocol) [**\***](#* 'Required parameter')

Задает протокол, который будет использован при скачивании файлов.

**`User name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Port`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

An int32 greater than zero that contains the port to be used on host.

*Если не установлен - будет установлен автоматически.*

**`Host`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Адрес сервера, куда будет отправлен запрос.

**`Remote path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к директории на сервере.

**`Local path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь на компьютере куда будет скачена директория.

### DirectoryUpload

[Table of contents](#Сontent)

— Загрузка директории с компьютера на указанный адрес, используя выбранный [protocol](#Protocol).

**Параметры:**

**`Protocol`** : [Protocol](#Protocol) [**\***](#* 'Required parameter')

Задает протокол, который будет использован при скачивании файлов.

**`User name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Port`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

An int32 greater than zero that contains the port to be used on host.

*Если не установлен - будет установлен автоматически.*

**`Host`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Адрес сервера, куда будет отправлен запрос.

**`Remote path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к директории на сервере.

**`Local path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь на компьютере куда будет скачена директории.

### DirectoryCopy

[Table of contents](#Сontent)

Копирование папки.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь копируемой папки.

**`Copy path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Новый путь папки.

**`Sub directory`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, копировать ли вложенные папки: если `true` - вложенные папки тоже будут скопированы; если `false` -  вложенные папки не будут скопированы.

Default value: true

**`Mask sub directories`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для вложенных папок. Будут скопированы только те папки, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

**`Mask files`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для файлов. Будут скопированы только те файлы, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

### DirectoryRename

[Table of contents](#Сontent)

Переименовывание папки.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к папке.

**`New path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к папке с новым именем.

### DirectoryGetFiles

[Table of contents](#Сontent)

Получение списка файлов папки в заданный [parameter](/documentation/scheme/parameters/).

**Параметры:**

**`Directory get files`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список папок, список файлов которых нужно получить в указанные параметры.

  Example: path 1 => parameter name 1; path 2, path 3, path 4 => parameter name 2.

  Файлы папки «path 1» будут добавлены в параметр «parameter name 1».

  Файлы папки «path 2», «path 3», «path 4» будут добавлены в параметр «parameter name 2».

  Данные записываются в [parameter](/documentation/scheme/parameters/) в виде словаря:

  ```C#
  //синхронная работа с параметром
    var data1 = processInstance.GetParameter<Dictionary<string, string>("parameter name 1");

  //асинхронная работа с параметром
  var data2 = await processInstance.GetParameterAsync<Dictionary<string, string>("parameter name 2").ConfigureAwait(false);
  ```

**`Parameter purpose`** : [ParameterPurpose](#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

**`Identify by full name`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг наименования путей: если `true` - в качестве ключа в словаре будет использоваться полное имя файла и путь к нему; если `false` -  в качестве ключа в словаре будет использоваться только имя файла без расширения

Default value: true

*Добавление в словарь файлов с одинаковым именем вызовет исключение.*

**`Sub directory`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, копировать ли вложенные папки: если `true` - вложенные папки тоже будут скопированы; `false` -  вложенные папки не будут скопированы.

**`Mask sub directories`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для вложенных папок. Будут получены файлы только тех папок, имена которых соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

**`Mask files`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для файлов. Будут получены только те файлы, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

### DirectoryGetDirectories

[Table of contents](#Сontent)

Получение списк вложенных папок.

**Параметры:**

**`Directory get directories`**   - Список папок, список вложенных папок которых нужно получить в указанные [parameter](/documentation/scheme/parameters/).

  Example: path 1 => parameter name 1; path 2, path 3, path 4 => parameter name 2.

  Вложенные папки для папки «path 1» будут добавлены в [parameter](/documentation/scheme/parameters/) «parameter name 1».

  Вложенные папки для папки «path 2», «path 3», «path 4» будут добавлены в [parameter](/documentation/scheme/parameters/) «parameter name 2».

  Данные записываются в параметр в виде словаря:

  ```C#
  //синхронная работа с параметром
    var data1 = processInstance.GetParameter<Dictionary<string, string>("parameter name 1");

  //асинхронная работа с параметром
  var data2 = await processInstance.GetParameterAsync<Dictionary<string, string>("parameter name 2").ConfigureAwait(false);
  ```

**`Parameter purpose`** : [ParameterPurpose](#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

**`Identify by full name`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг наименования путей: если `true` - в качестве ключа в словаре будет использоваться полное имя файла и путь к нему; если `false` -  в качестве ключа в словаре будет использоваться только имя файла без расширения

Default value: true

*Добавление в словарь файлов с одинаковым именем вызовет исключение.*

**`Sub directory`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, копировать ли вложенные папки: если `true` - вложенные папки тоже будут скопированы; если `false` -  вложенные папки не будут скопированы.

Default value: true

**`Mask sub directories`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для вложенных папок. Будут получены только те папки, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

### DirectoryCompress

[Table of contents](#Сontent)

Архивация папки.

**Параметры:**

**`Archive path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к архиву.

**`Directory path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь архивируемой папки.

**`Sub directory`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, копировать ли вложенные папки: если `true` - вложенные папки тоже будут скопированы; если `false` -  вложенные папки не будут скопированы.

Default value: true

**`Mask sub directories`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для вложенных папок. Будут архивированы только те папки, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

**`Mask files`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

[Маска](#Masks) для файлов. Будут архивированы только те файлы, которые соотвествуют этой маске. Read about [masks](#Masks).

Default value: \*

**`Archive type`** : [ArchiveType](#ArchiveType) [**\***](#* 'Required parameter')

Формат архива, в который будетт сжата папка.

Default value: ZIP

### FilesCompress

[Table of contents](#Сontent)

Архивация списка файлов.

**Параметры:**

**`Archive path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к архиву.

**`Files paths`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей файлов, которые необходимо добавить в архив.

Example: file path 1, file path 2.

Будет создан архив с файлами «file path 1», «file path 2».

**`Mask files`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Маска для файлов. Будут архивированы только те файлы, которые соотвествуют этой маске . Read about [masks](#Masks).

**`Archive type`** : [ArchiveType](#ArchiveType) [**\***](#* 'Required parameter')

Формат архива, в который будут сжаты файлы.

Default value: ZIP

### FileUnсompress

[Table of contents](#Сontent)

Разархивация.

**Параметры:**

**`Archive`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к архиву.

**`Directory path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь, куда будут извлечены файлы.

**`Archive type`** : [ArchiveType](#ArchiveType) [**\***](#* 'Required parameter')

Формат архива, из которого будут извлечены файлы.

Default value: ZIP

## Conditions

### FileExists

[Table of contents](#Сontent)

Проверяет существует ли файл.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к файлу, существование которого нужно проверить.

### FilesListExists

[Table of contents](#Сontent)

Проверка существования файлов, указанных в списке.

**Параметры:**

**`Files list exists`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список путей файлов, существование которых нужно проверить.

Example: file path 1, file path 2.

Будет проверено существование файлов «file path 1» и «file path 2»

**`Concatenation`** - Способ объединения результатов. Read about [concatenation](#Concatenation).

### DirectoryExists

[Table of contents](#Сontent)

Проверяет существует ли папка.

**Параметры:**

**`Path`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Путь к папке, существование которой нужно проверить.

## Elements

### ParameterPurpose

[Table of contents](#Сontent)

Задание поведение при сохранении параметра.

|Значение| Описание |
|----------------|----------------|
|Temporary |  *Temporary Parameter exists from the time of its conveying to a process, or its setting within a process, till the end of the transition process. In other words, if you convey Parameter with Purpose = Temporary to the process through Command, it will be possible to obtain its Value only until the process stops and begins waiting for another Command.*|
|Purpose | *Persistence Parameter is stored in a database in the WorkflowProcessInstancePersistence table (or object). Its Value may be accessed at any time after it has been set. The third type of Purpose is a system one.*|
|System | *System Parameters cannot be created; they are used by Workflow Engine for its proper operation. You may access them trough the ProcessInstance object. These Parameters will be discussed in detail further on.*|


### Protocol

Протокол передачи данных

|Значение| Описание |
|----------------|----------------|
|FTP | File Transfer Protocol|
|SFTP | SSH File Transfer Protocol|
|HTTP/HTTPS | HyperText Transfer Protocol|


[Table of contents](#Сontent)

### ParameterType

[Table of contents](#Сontent)

Формат чтения данных из файла.

|Значение| Описание |
|----------------|----------------|
|String |Данные будут сохранены в формате строки. *Этот формат стоит использовать при работе с текстовым файлом.*|
|Byte | Данные будут сохранены в виде массива Byte. *Этот формат стоит использовать при работе с не текстовыми файлами.*|

### Masks

[Table of contents](#Сontent)

Маска для поиска файла и папок.

#### Parameters

[Table of contents](#Сontent)

File masks can consist of any combination of the following:

- Fixed characters

 Letters, numbers and other characters allowed in file names.

- Question mark (?)

 Represents any single character.

- Asterisk (\*)

  Represents any sequence of characters (including no characters at all).

**Examples**

| File Mask | Description & Examples |
|----------------|----------------|
| \* | Matches all files containing any amount of characters, with or without extensions (e.g., entering A* would match any file or folder starting with the letter A followed by any amount of characters). |
| \*.\* | Matches all files containing any amount of characters and with any extension. Even matches files that don't have an extension (e.g., entering A\*.\* would match any file starting with the letter A followed by any amount of characters along with any extension). |
| ? | Matches any single character (e.g., entering A? would match any file starting with the letter A followed by any single character). |
| \*.png | Matches all files with names containing any amount of characters with a .png extension (e.g., image_name.png, cool_pic.png, 1.png). |
| \*.p\* | Matches all files with names containing any amount of characters with an extension starting with the letter p (e.g., document.pdf, image_name.png, business.project, 1.ppt) |
| pic\*.\* | Matches all files with names that start with pic (e.g., picture_name.png, pictogram.ico, picker.html, pic). |
| \*mat?.html | Matches all .html files with names starting with any sequence of characters, followed by the string mat, and ending with a single character (e.g., automate.html, mate.html, tomato.html). |
| ?????? | Matches all files with names containing six characters and without an extension (e.g., 123456, myFile, my_pic, images)|
| doc?????.pdf | Matches all .pdf files with names that start with doc followed by any five characters (e.g., document.pdf, doctrine.pdf, doc_1234.pdf).|
| file1.txt   file2.jpg   file3.png | Matches specific filenames or wildcard masks that reside in the same directory (e.g., c:\temp\file1.txt|file2.jpg|file3.png).|
| c:\temp1\*.txt  c:\temp2\*.png| Matches specific filenames or wildcard masks that reside in different directories (e.g., c:\photos\*.jpg; \c:\music\*.mp3).|

### ArchiveType

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|ZIP | Формат архивации файлов, наиболее часто используемый на операционных системах Windows|
|TarGZ | Формат архивации файлов, наиболее часто используемый на операционных системах Linux и Mac OS|

### Concatenation

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|And | Объединение с использованием операции коньюнкции|
|Or | Объединение с использованием операции дизъюнкции|
