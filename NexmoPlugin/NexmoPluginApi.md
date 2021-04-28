# NexmoPlugin

[Плагин](/documentation/plugins/), который реализует функции для отправки сообщений через Nexmo.

## Сontent

1. [Installation and setting](#Installation-and-setting)
2. [Settings](#Settings)
    1. [ApiKey](#ApiKey)
    2. [ApiSecret](#ApiSecret)
3. [Actions](#Actions)
    1. [NexmoSendMessage](#NexmoSendMessage)


## Installation and setting

Install nuget package:
- Для проектов на .Net Core: [WorkflowEngine.NETCore-NexmoPlugin](https://www.nuget.org/packages/WorkflowEngine.NETCore-NexmoPlugin/)  
- Для проектов на .Net Framework: [WorkflowEngine.NET-NexmoPlugin](https://www.nuget.org/packages/WorkflowEngine.NET-NexmoPlugin/)

*[How install nuget package in Visual studio for Windows](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)*

*[How install nuget package in Visual studio for Mac](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)*

*[How install nuget package in Rider](https://www.jetbrains.com/help/rider/Using_NuGet.html#browsing)*


Add the following namespaces to the usings section:
```C#
using OptimaJet.Workflow.Plugins;
```

Создайте обьект плагина и установите необходимые [Settings](#Settings):

```C#
var nexmoPlugin = new NexmoPlugin();

// Здесь ваши настройки

// nexmoPlugin.ApiKey = "API_KEY";
// nexmoPlugin.ApiSecret = "API_SECRET";
```

Подключите плагин к [WorkflowRuntime](/documentation/main-terms/runtime/):

```C#
var runtime = new WorkflowRuntime()...

runtime.WithPlugin(nexmoPlugin);
```

## Settings

### ApiKey

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Параметр для доступа к Nexmo(API_KEY).

 *Используется для [NexmoSendMessage](#NexmoSendMessage).*

### ApiSecret

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Параметр для доступа к Nexmo(API_SECRET).

 *Используется для [NexmoSendMessage](#NexmoSendMessage).*

## Actions

Read about [actions](/documentation/scheme/actions/).

### NexmoSendMessage

[Table of contents](#Сontent)

Отправка сообщения.

**Параметры:**

**`ApiKey`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к Nexmo(API_KEY).

*Значение будет взято из [ApiKey](#ApiKey), если оно было установлено.*

**`ApiSecret`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к Nexmo(API_SECRET).

*Значение будет взято из [ApiSecret](#ApiSecret), если оно было установлено.*

**`From`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the address of the sender of the email message.

**`To`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the addresses of the recipients of the email message

**`Message`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the message body.
