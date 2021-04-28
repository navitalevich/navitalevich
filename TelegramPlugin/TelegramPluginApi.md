# TelegramPlugin

 —  Этот [плагин](/documentation/plugins/) реализует функции для отправки сообщений через Telegram.

## Сontent

1. [Installation and setting](#Installation-and-setting)
2. [Settings](#Settings)
    1. [ApiId](#ApiId)
    2. [ApiHash](#ApiHash)
    3. [CodeRequest](#CodeRequest)
    4. [SessionUserId](#SessionUserId)
    5. [Number](#Number)
    6. [LimitMessageForRead](#LimitMessageForRead)
    7. [MarkAsRead](#MarkAsRead)
3. [Actions](#Actions)
    1. [TelegramAuthentication](#TelegramAuthentication)
    2. [TelegramSendMessage](#TelegramSendMessage)
    3. [TelegramListenMessages](#TelegramListenMessages)
4. [Elements](#Elements) 
    1. [Authentication](#Authentication)
    2. [GetterType](#GetterType)
    3. [SenderType](#SenderType)


## Installation and setting

Install nuget package:
- Для проектов на .Net Core: [WorkflowEngine.NETCore-TelegramPlugin](https://www.nuget.org/packages/WorkflowEngine.NETCore-TelegramPlugin/)  
- Для проектов на .Net Framework: [WorkflowEngine.NET-TelegramPlugin](https://www.nuget.org/packages/WorkflowEngine.NET-TelegramPlugin/)

*[How install nuget package in Visual studio for Windows](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)*

*[How install nuget package in Visual studio for Mac](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)*

*[How install nuget package in Rider](https://www.jetbrains.com/help/rider/Using_NuGet.html#browsing)*


Add the following namespaces to the usings section:
```C#
using OptimaJet.Workflow.Plugins;
```

Создайте обьект плагина и установите необходимые [Settings](#Settings):

```C#
var telegramPlugin = new TelegramPlugin();

// Здесь ваши настройки

// telegramPlugin.ApiId = "AccountSid";
// telegramPlugin.ApiHash = "AuthToken";
// telegramPlugin.CodeRequest += MyCodeRequest;
// telegramPlugin.SessionUserId = "AuthToken";
// telegramPlugin.Number = "AuthToken";
// telegramPlugin.LimitMessageForRead = 100;
// telegramPlugin.MarkAsRead = true;
```

Подключите плагин к [WorkflowRuntime](/documentation/main-terms/runtime/):

```C#
var runtime = new WorkflowRuntime()...

runtime.WithPlugin(telegramPlugin);
```

## Settings

### ApiId

[Table of contents](#Сontent)

[Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8): Параметр для доступа к  Telegram. Для получения: [зарегистрируйте свое приложение как Telegram клиент](https://core.telegram.org/api/obtaining_api_id#obtaining-api-id).

*Используется для [TelegramAuthentication](#TelegramAuthentication).*

### ApiHash

[Table of contents](#Сontent)

Параметр для доступа к  Telegram. Для получения: [зарегистрируйте свое приложение как Telegram клиент](https://core.telegram.org/api/obtaining_api_id#obtaining-api-id).

 *Используется для [TelegramAuthentication](#TelegramAuthentication).*

### CodeRequest

 [Table of contents](#Сontent)

Делегат, ваша функция должна вернуть код, отправленный вам в смс.

When user is authenticated, будет создан special file called session.dat. In this file store all information needed for user session. So you need to authenticate user every time the session.dat file is corrupted or removed.

**Action syntax:**

```C#
string MyCodeRequest()
{
    string code = "myCode"; // you can change code in debugger

    return code;
}
```

**Read about [Authentication](#Authentication)**

### SessionUserId

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): The name of the session that tracks login info about this TelegramClient connection.

 *Используется для [TelegramAuthentication](#TelegramAuthentication).*

### Number

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Номер текущего пользователя.

*Используется для [TelegramAuthentication](#TelegramAuthentication).*

### LimitMessageForRead

[Table of contents](#Сontent)

[Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8): Максимальное количество сообщений, которое может быть прочитано за раз. 

Default value: 100

*Используется для [TwilioSendMessage](#TwilioSendMessage), [LimitMessageForRead](#LimitMessageForRead).*

### MarkAsRead

[Table of contents](#Сontent)

[Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8): Флаг, помечать ли полученные сообщения как прочитанные: если `true` - сообщения будут помечаны как прочитанные; если `false` - сообщения останутся не прочитанными.

Default value: true

*Используется для [TwilioSendMessage](#TwilioSendMessage), [LimitMessageForRead](#LimitMessageForRead).*

## Actions

Read about [actions](/documentation/scheme/actions/).

### TelegramAuthentication

[Table of contents](#Сontent)

Аунтефикация текущего пользователя.

**Read about [Authentication](#Authentication)**

**Параметры:**

**`ApiId`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к  Telegram. Для получения: [зарегистрируйте свое приложение как Telegram клиент](https://core.telegram.org/api/obtaining_api_id#obtaining-api-id).

*Значение будет взято из [AuthToken](#AuthToken), если оно было установлено.*

**`ApiHash`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter') 

Параметр для доступа к  Telegram. Для получения: [зарегистрируйте свое приложение как Telegram клиент](https://core.telegram.org/api/obtaining_api_id#obtaining-api-id).

*Значение будет взято из [ApiHash](#ApiHash), если оно было установлено.*

**`Number`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter') 

Номер текущего пользователя.

*Значение будет взято из [Number](#Number), если оно было установлено.*

**`SessionUserId`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

The name of the session that tracks login info about this TelegramClient connection.

*Значение будет взято из [SessionUserId](#SessionUserId), если оно было установлено.*

### TelegramSendMessage

[Table of contents](#Сontent)

Отправка сообщения пользователю/чат/канал.

**Параметры:**

**`GetterType`** : [GetterType](#GetterType) [**\***](#* 'Required parameter')

Задает тип идентификатора получателя.

Default value: UserPhone

**`Getter`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Идентификатор получателя выбраннго в GetterType типа.

**`Message`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the message body.

### TelegramListenMessages

[Table of contents](#Сontent)

Получение новых сообщений от пользователя/чата/канала.

**Параметры:**

**`SenderType`** : [SenderType](#SenderType) [**\***](#* 'Required parameter')

Тип идентификатора отправителя, сообщения от которого будут прослушиваться.

Default value: UserPhone

**`Sender`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Идентификатор отправителя, сообщения от которого будут прослушиваться, выбранного в SenderType типа.

**`ParameterName`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в который будут записаны новые сообщения.

**`LimitMessageForRead`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) [**\***](#* 'Required parameter')

Максимальное количество сообщений, которое может быть прочитано за раз.

Default value: 100

*Значение будет взято из [LimitMessageForRead](#LimitMessageForRead), если оно было установлено.*

**`MarkAsRead`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, помечать ли полученные сообщения как прочитанные: если `true` - сообщения будут помечаны как прочитанные; если `false` - сообщения останутся не прочитанными.

Default value: true

*Значение будет взято из [MarkAsRead](#MarkAsRead), если оно было установлено.*

## Elements

### Authentication

[Table of contents](#Сontent)

Для работы плагина, при первом запуске необходимо:

1. Получить [ApiId](#ApiId) и [ApiHash](#ApiHash), для этого [зарегистрируйте свое приложение как Telegram клиент](https://core.telegram.org/api/obtaining_api_id#obtaining-api-id).
2. Свяжите вашу функцию с делегатом [CodeRequest](#CodeRequest).
3. В режиме отладчика введите код, отправленный вам в смс.


**When user is authenticated, будет создан special file called session.dat. In this file store all information needed for user session. So you need to authenticate user every time the session.dat file is corrupted or removed.**

### GetterType

[Table of contents](#Сontent)

Тип идентификатора получателя сообщения:

|Значение| Описание |
|----------------|----------------|
|UserPhone | Номер телефона. |
|UserName | Имя пользователя. |
|ChatTitle | Название чата. |
|ChannelTitle | Название канала. |

### SenderType

[Table of contents](#Сontent)

Тип идентификатора отправителя сообщений:

|Значение| Описание |
|----------------|----------------|
|UserPhone | Номер телефона. |
|UserName | Имя пользователя. |
|ChatTitle | Название чата. |
|ChannelTitle | Название канала. |
