# SlackPlugin

 —  Этот [плагин](/documentation/plugins/) реализует функции для отправки сообщений на канал Slack.

## Сontent

1. [Installation and setting](#Installation-and-setting)
2. [Settings](#Settings)
    1. [Token](#Token)
    2. [NameParameterForSaveRequestResult](#NameParameterForSaveRequestResult)
    3. [ThrowExeptionIfNotSended](#ThrowExeptionIfNotSended)
    4. [SaveRequestResult](#SaveRequestResult)
3. [Actions](#Actions)
    1. [SlackSendMessage](#SlackSendMessage)


## Installation and setting

Install nuget package:
- Для проектов на .Net Core: [WorkflowEngine.NETCore-SlackPlugin](https://www.nuget.org/packages/WorkflowEngine.NETCore-SlackPlugin/)
- Для проектов на .Net Framework: [WorkflowEngine.NET-SlackPlugin](https://www.nuget.org/packages/WorkflowEngine.NET-SlackPlugin/)

*[How install nuget package in Visual studio for Windows](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)*

*[How install nuget package in Visual studio for Mac](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)*

*[How install nuget package in Rider](https://www.jetbrains.com/help/rider/Using_NuGet.html#browsing)*


Add the following namespaces to the usings section:
```C#
using OptimaJet.Workflow.Plugins;
```

Создайте обьект плагина и установите необходимые [Settings](#Settings):

```C#
var slackPlugin = new SlackPlugin();

// Здесь ваши настройки

// slackPlugin.Token = "Token";
// slackPlugin.NameParameterForSaveRequestResult = "SlackRequestResult";
// slackPlugin.ThrowExeptionIfNotSended = true;
// slackPlugin.SaveRequestResult = true;
```

Подключите плагин к [WorkflowRuntime](/documentation/main-terms/runtime/):

```C#
var runtime = new WorkflowRuntime()...

runtime.WithPlugin(slackPlugin);
```

## Settings

### Token

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Параметр для доступа к Slack.

 *Используется для [SlackSendMessage](#SlackSendMessage).*

### NameParameterForSaveRequestResult

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Имя [parameter](/documentation/scheme/parameters/), где будет сохранен результат запроса.

 *Используется для [SlackSendMessage](#SlackSendMessage).*

### ThrowExeptionIfNotSended

[Table of contents](#Сontent)

[Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8): Флаг, выбрасывается ли исключение, в случае ошибки отправки: если `true` - исключение будет выбрашено; если `false` - ошибка будет пропущена.

Default value: true

 *Используется для [SlackSendMessage](#SlackSendMessage).*
 
### SaveRequestResult

[Table of contents](#Сontent)

[Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8): Флаг, будет ли сохранен результат запроса: если `true` - результат запроса будет сохранен в [parameter](/documentation/scheme/parameters/); `false` -  результат не будет сохранен.

Default value: true

*Используется для [SlackSendMessage](#SlackSendMessage).*

## Actions

Read about [actions](/documentation/scheme/actions/).

### SlackSendMessage

[Table of contents](#Сontent)

Отправка сообщения.

**Параметры:**

**`Token`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к Slack.

  *Значение будет взято из [Token](#Token), если оно было установлено.*

**`Channel`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Канал, в который будет отправлено сообщение.

**`Message`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the message body.

**`ThrowExeptionIfNotSended`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

флаг, выбрасывается ли исключение, в случае ошибки отправки: если `true` - исключение будет выбрашено; если `false` - ошибка будет пропущена.

Default value: true

*Значение будет взято из [ThrowExeptionIfNotSended](#ThrowExeptionIfNotSended), если оно было установлено.*

**`SaveRequestResult`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, будет ли сохранен результат запроса: если `true` - результат запроса будет сохранен в [parameter](/documentation/scheme/parameters/); если `false` -  результат не будет сохранен.

Default value: true

*Значение будет взято из [SaveRequestResult](#SaveRequestResult), если оно было установлено.*

**`NameParameterForSaveRequestResult`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), где будет сохранен результат запроса.

*Значение будет взято из [NameParameterForSaveRequestResult](#NameParameterForSaveRequestResult), если оно было установлено.*





