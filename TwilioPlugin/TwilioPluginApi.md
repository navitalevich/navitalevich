# TwilioPlugin

[Плагин](/documentation/plugins/), который реализует функции для отправки сообщений через Twilio.

## Сontent

1. [Installation and setting](#Installation-and-setting)
2. [Settings](#Settings)
    1. [AccountSid](#AccountSid)
    2. [AuthToken](#AuthToken)
3. [Actions](#Actions)
    1. [TwilioSendMessage](#TwilioSendMessage)


## Installation and setting

Install nuget package:
- Для проектов на .Net Core: [WorkflowEngine.NETCore-TwilioPlugin](https://www.nuget.org/packages/WorkflowEngine.NETCore-TwilioPlugin/)  
- Для проектов на .Net Framework: [WorkflowEngine.NET-TwilioPlugin](https://www.nuget.org/packages/WorkflowEngine.NET-TwilioPlugin/)

*[How install nuget package in Visual studio for Windows](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)*

*[How install nuget package in Visual studio for Mac](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)*

*[How install nuget package in Rider](https://www.jetbrains.com/help/rider/Using_NuGet.html#browsing)*


Add the following namespaces to the usings section:
```C#
using OptimaJet.Workflow.Plugins;
```

Создайте обьект плагина и установите необходимые [Settings](#Settings):

```C#
var twilioPlugin = new TwilioPlugin();

// Здесь ваши настройки

// twilioPlugin.AccountSid = "AccountSid";
// twilioPlugin.AuthToken = "AuthToken";
```

Подключите плагин к [WorkflowRuntime](/documentation/main-terms/runtime/):

```C#
var runtime = new WorkflowRuntime()...

runtime.WithPlugin(twilioPlugin);
```

## Settings

### AccountSid

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Параметр для доступа к Twilio.

 *Используется для [TwilioSendMessage](#TwilioSendMessage).*

### AuthToken

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Параметр для доступа к Twilio.

 *Используется для [TwilioSendMessage](#TwilioSendMessage).*

## Actions

Read about [actions](/documentation/scheme/actions/).

### TwilioSendMessage

[Table of contents](#Сontent)

Отправка сообщения

**Параметры:**

**`AccountSid`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к Slack.

*Значение будет взято из [AccountSid](#AccountSid), если оно было установлено.*

**`AuthToken`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Параметр для доступа к Slack.

*Значение будет взято из [AuthToken](#AuthToken), если оно было установлено.*

**`From`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the address of the sender of the email message.

**`To`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the addresses of the recipients of the email message

**`Message`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the message body.
