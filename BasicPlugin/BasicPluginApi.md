# BasicPlugin

[Плагин](/documentation/plugins/), который реализует наиболее востребованные функции для работы с процессами, параметрами и т.д.

## Сontent

1. [Settings](#Settings)
    1. [Setting_Mailserver](#Setting_Mailserver)
    2. [Setting_MailserverPort](#Setting_MailserverPort)
    3. [Setting_MailserverFrom](#Setting_MailserverFrom)
    4. [Setting_MailserverLogin](#Setting_MailserverLogin)
    5. [Setting_MailserverPassword](#Setting_MailserverPassword)
    6. [Setting_MailserverSsl](#Setting_MailserverSsl)
    7. [RequestHeaders](#RequestHeaders)
    8. [ApproversInStageAsync](#ApproversInStageAsync)
    9. [UsersInRoleAsync](#UsersInRoleAsync)
    10. [CheckPredefinedActorAsync](#CheckPredefinedActorAsync)
    11. [GetPredefinedIdentitiesAsync](#GetPredefinedIdentitiesAsync)
    12. [UpdateDocumentStateAsync](#UpdateDocumentStateAsync)
2. [Actions](#Actions)
    1. [SetActivity](#SetActivity)
    2. [SetState](#SetState)
    3. [SetParameter](#SetParameter)
    4. [RemoveParameter](#RemoveParameter)
    5. [HTTPRequest](#HTTPRequest)
    6. [CreateProcess](#CreateProcess)
    7. [SendEmail](#SendEmail)
    8. [FillApproversUsers](#FillApproversUsers)
    9. [FillApproversRoles](#FillApproversRoles)
3. [Conditions](#Conditions)
    1. [CheckParameter](#CheckParameter)
    2. [CheckAllSubprocessesCompleted](#CheckAllSubprocessesCompleted)
    3. [IsProcessFinish](#IsProcessFinish)
    4. [IsApprovedByUsers](#IsApprovedByUsers)
    5. [IsApprovedByRoles](#IsApprovedByRoles)
    6. [CheckHTTPRequest](#CheckHTTPRequest)
    7. [IsApproveComplete](#IsApproveComplete)
4. [Rules](#Rules)
    1. [CheckRole](#CheckRole)
    2. [Approver](#Approver)
    3. [Predefined](#Predefined)
5. [Elements](#Elements)
    1. [SetAfter](#SetAfter)
    2. [ContentType](#ContentType)
    3. [CompareType](#CompareType)
    4. [Mode](#Mode)

## Settings

### Setting_Mailserver

[Table of contents](#Сontent)

A [string](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) that contains the name or IP address of the host used for 
 SMTP transactions.
 
*Используется для [SendEmail](#SendEmail).*

### Setting_MailserverPort

[Table of contents](#Сontent)

An [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) greater than zero that contains the port to be used on host.

### Setting_MailserverFrom

[Table of contents](#Сontent)

A [string](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) that contains the address of the sender of the email 
 message.

 *Используется для [SendEmail](#SendEmail).*

### Setting_MailserverLogin

[Table of contents](#Сontent)

The user name associated with the [credentials](https://docs.microsoft.com/en-us/dotnet/api/system.net.networkcredential?view=netframework-4.8).

 *Используется для [SendEmail](#SendEmail).*

### Setting_MailserverPassword

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) которая содержит password for the user name associated with the [credentials](https://docs.microsoft.com/en-us/dotnet/api/system.net.networkcredential?view=netframework-4.8).

 *Используется для [SendEmail](#SendEmail).*

### Setting_MailserverSsl

[Table of contents](#Сontent)

[Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8): ``true`` - sll is enabled; ``false`` - sll is disabled. Read about it [here](https://docs.microsoft.com/en-us/dotnet/api/system.net.mail.smtpclient.enablessl?f1url=https%3A%2F%2Fmsdn.microsoft.com%2Fquery%2Fdev16.query%3FappId%3DDev16IDEF1%26l%3DEN-US%26k%3Dk(System.Net.Mail.SmtpClient.EnableSsl);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)%26rd%3Dtrue&view=netcore-3.1)

 *Используется для [SendEmail](#SendEmail).*

### RequestHeaders

[Table of contents](#Сontent)

Словарь заголовков, которые будут добавлены в [DefaultRequestHeaders](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient.defaultrequestheaders?f1url=https%3A%2F%2Fmsdn.microsoft.com%2Fquery%2Fdev16.query%3FappId%3DDev16IDEF1%26l%3DEN-US%26k%3Dk(System.Net.Http.HttpClient.DefaultRequestHeaders);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)%26rd%3Dtrue%26f%3D255%26MSPPError%3D-2147217396&view=netcore-3.1) для каждого запроса.

*Используется для [HTTPRequest](#HTTPRequest)  и [CheckHTTPRequest](#CheckHTTPRequest).*

### ApproversInStageAsync

[Table of contents](#Сontent)

Делегат, ваша функция должна возвращать всех пользователей текущего этапа.

```C#
Task<IEnumerable<string>> MyApproversInStageAsync(string stageName, ProcessInstance processInstance)
{
  //Example вернуть id всех участников процесса подписания
  if (stageName == "Signing")
  {
      return new List<string>() {myManagerId, myBossId};
  }

  return new List<string>();
}
```

 *Используется для [FillApproversUsers](#FillApproversUsers).*

### UsersInRoleAsync

[Table of contents](#Сontent)

Делегат, ваша функция должна возвращать всех пользователей с конкретным [rule](/documentation/scheme/rules/).  С помощью этой функции вы можете реализовать как [rule](/documentation/scheme/rules/) в рамках системы безопасности, так и в рамках отдельного документа. Такие как: автор документа, менеджер документа, контроллер.

**Action syntax:**

```C#
async Task<IEnumerable<string>> MyUsersInRoleAsync(string roleName, ProcessInstance processInstance)
{
  //Example: вернуть id всех пользователей являющимися менеджерами
  if (parameter == "Manager")
  {
      return new List<string>() {myManagerId1, myManagerId2};
  }

  return new List<string>();
}
```

 *Используется для [FillApproversRoles](#FillApproversRoles), [IsApprovedByRoles](#IsApprovedByRoles) и  [CheckRole](#CheckRole)*

### CheckPredefinedActorAsync

[Table of contents](#Сontent)

Делегат, ваша функция должна возвращать: ``true`` - если пользователь соотвутствует указанной [rule](/documentation/scheme/rules/); ``false`` -  если пользователь не соотвутствует указанной [rule](/documentation/scheme/rules/).

**Handler syntax:**

```C#
async Task<bool> CheckMyPredefinedActorAsync(ProcessInstance processInstance, WorkflowRuntime runtime, string parameter, string identityId)
{

  //Example: проверка что пользователь с указанными Id является менеджером
  if (parameter == "Manager")
  {
      if (identityId == myManagerId)
          return true;
      else
          return false;
  }

  return false;
}
```

 *Используется для [FillApproversRoles](#FillApproversRoles), [IsApprovedByRoles](#IsApprovedByRoles) и  [CheckRole](#CheckRole)*

### GetPredefinedIdentitiesAsync

[Table of contents](#Сontent)

Делегат, ваша функция должна возвращать всех пользователей с конкретным [rule](/documentation/scheme/rules/).  С помощью этой функции вы можете реализовать как [rules](/documentation/scheme/rules/) в рамках системы безопасности, так и в рамках отдельного документа. Такие как: автор документа, менеджер документа, контроллер.

**Handler syntax:**

```C#
async Task<IEnumerable<string>> GetMyPredefinedIdentitiesAsync(ProcessInstance processInstance, WorkflowRuntime runtime, string parameter)
{
  //Example: вернуть id всех пользователей являющимися менеджерами
  if (parameter == "Manager")
  {
      return new List<string>() {myManagerId1, myManagerId2};
  }

  return new List<string>();
}
```

### UpdateDocumentStateAsync

[Table of contents](#Сontent)

Делегат, который срабатывает на ProcessStatusChanged event in [WorkflowRuntime](/documentation/main-terms/runtime/).

**Handler syntax:**

```C#
public static async Task UpdateMyDocumentStateAsync(ProcessInstance processInstance, string stateName, string  localizedStateName)
{
   //here you can update document state
  myDoc.State = stateName;
}
```

## Actions

Read about [actions](/documentation/scheme/actions/).

### SetActivity

[Table of contents](#Сontent)

Переводит текущий [process](/documentation/execution/regular-process/) в указанный [activity](/documentation/scheme/activities/).

**Параметры**

**`Activity name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [activity](/documentation/scheme/activities/), в которое будет установлен [process](/documentation/execution/regular-process/).

**`Set after`** : [SetAfter](#SetAfter) [**\***](#* 'Required parameter')

Определеяет в какой момент выполнения будет установлен [activity](/documentation/scheme/activities/). 

Default value: AfterAction

### SetState

[Table of contents](#Сontent)

Переводит указанный [process](/documentation/execution/regular-process/) в указанный [state](/documentation/workflowengine/#elements).

**Параметры**

**`State name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [state](/documentation/workflowengine/#elements), в которое будет установлен [process](/documentation/execution/regular-process/)

**`Set after`** : [SetAfter](#SetAfter) [**\***](#* 'Required parameter')

Определеяет в какой момент выполнения будет установлен [state](/documentation/workflowengine/#elements). 

Default value: AfterAction

**`Process id`** : [Guid](https://docs.microsoft.com/en-us/dotnet/api/system.guid?view=netframework-4.8)

Указывает, какой [process](/documentation/execution/regular-process/) должен перейти в указанный [state](/documentation/workflowengine/#elements), по умолчанию используется текущий [process](/documentation/execution/regular-process/).


### SetParameter

[Table of contents](#Сontent)

Устанавливает значение [parameter](/documentation/scheme/parameters/) для текущего или родительского [process](/documentation/execution/regular-process/). **Поддерживаются только строковые значения.**

**Параметры**

**`Parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), для которого будет установлено значение.

**`Value`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Устанавливаемое значение.

**`For root process`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

``true`` - [parameter](/documentation/scheme/parameters/) будет установлен для основного [process](/documentation/execution/regular-process/); ``false`` -  [parameter](/documentation/scheme/parameters/) будет установлен для текущего [process](/documentation/execution/regular-process/).

  Default value: false

  *Read about [subprocesses](/documentation/execution/subprocesses/).*

### ExecuteCommand

[Table of contents](#Сontent)

Выполняет [command](/documentation/scheme/commands/) из указанного [process](/documentation/execution/regular-process/).

**Параметры**

**`Command name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [command](/documentation/scheme/commands/), которая будет выполняться.

**`Process id`** : [Guid](https://docs.microsoft.com/en-us/dotnet/api/system.guid?view=netframework-4.8)

Указывает, из какого [process](/documentation/execution/regular-process/) будет выполнена указанная [command](/documentation/scheme/commands/), по умолчанию используется текущий [process](/documentation/execution/regular-process/).

### RemoveParameter

[Table of contents](#Сontent)

Удаление [parameter](/documentation/scheme/parameters/) для текущего или родительского [process](/documentation/execution/regular-process/).

**Параметры:**

**`Parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), который будет удален.

**`For root process`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

``true`` - [Parameter](/documentation/scheme/parameters/) будет удален у основного [process](/documentation/execution/regular-process/); ``false`` -  [Parameter](/documentation/scheme/parameters/) будет удален у текущего [process](/documentation/execution/regular-process/).
  
  Default value: false
  
  *Read about [subprocesses](/documentation/execution/subprocesses/).*

### HTTPRequest

[Table of contents](#Сontent)

отправляет HTTP(s) запрос по указанному Url(GET/POST).

**Параметры:**

**`Url`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

The Url the request is sent to.

**`UserName`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Post`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8)

``true`` - post request; ``false`` - get request.

**`Store response`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8)

``true`` -  Результат сохраняется в [parameter](/documentation/scheme/parameters/) с указанными в параметрах именем, который имеет тип [temporary](documentation/plugins/filepluginapi#ParameterPurpose); ``false`` -  Результат не будет сохранен в переменную.

**`Parameter Name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя [parameter](/documentation/scheme/parameters/) для сохранения результата.

Default value: HTTPRequest_Result

**`Parameter purpose`** : [ParameterPurpose](documentation/plugins/filepluginapi#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

Default value: Temporary

**`Add process Id and scheme in parameters`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Only for post request. ``true`` - process id будет добавлен в параметры запроса; ``false`` -  process id не будет добавлен в параметры запроса.

**`Content type`** : [content type](#ContentType) [**\***](#* 'Required parameter')

Only for post request. Формат полученного ответа.

Default value: Json

**`Headers`**

Строка, которая представляет из себя набор пар ключ - значение. Которые затем будут добавлены в [DefaultRequestHeaders](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient.defaultrequestheaders?f1url=https%3A%2F%2Fmsdn.microsoft.com%2Fquery%2Fdev16.query%3FappId%3DDev16IDEF1%26l%3DEN-US%26k%3Dk(System.Net.Http.HttpClient.DefaultRequestHeaders);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)%26rd%3Dtrue%26f%3D255%26MSPPError%3D-2147217396&view=netcore-3.1) для указанного запроса.

**Example:**

```
Name 1 = Value 1;
Name 2 = Value 2;
Name 3 = Value 3;
```

**`Parameters`**

Only for post request. Параметры запроса типа, указанного в [content type](#ContentType).

### CreateProcess 

[Table of contents](#Сontent)

Создает новый [process](/documentation/execution/regular-process/) по схеме.

**Параметры:**

**`Scheme`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя схемы.

### SendEmail

[Table of contents](#Сontent)

Отправляет письмо на заданный e-mail.

**Параметры:**

**`Mail server`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the name or IP address of the host used for SMTP transactions.

  *Значение будет взято из [Setting_Mailserver](#Setting_Mailserver), если оно было установлено.*

**`Mail server port`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) [**\***](#* 'Required parameter')

An [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) greater than zero that contains the port to be used on host.

   *Значение будет взято из [Setting_MailserverPort](#Setting_MailserverPort), если оно было установлено.*

**`Mail server from`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the address of the sender of the email message.

   *Значение будет взято из [Setting_MailserverFrom](#Setting_MailserverFrom), если оно было установлено.*

**`Mail server login`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

The user name associated with the [credentials](https://docs.microsoft.com/en-us/dotnet/api/system.net.networkcredential?view=netframework-4.8).

  *Значение будет взято из [Setting_MailserverLogin](#Setting_MailserverLogin), если оно было установлено.*

**`Mail server pass`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

The password for the user name associated with the [credentials](https://docs.microsoft.com/en-us/dotnet/api/system.net.networkcredential?view=netframework-4.8).

  *Значение будет взято из [Setting_MailserverPassword](#Setting_MailserverPassword), если оно было установлено.*

**`Mail server ssl`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

``true`` - sll is enabled; ``false`` - sll is disabled. Read about it [here](https://docs.microsoft.com/en-us/dotnet/api/system.net.mail.smtpclient.enablessl?f1url=https%3A%2F%2Fmsdn.microsoft.com%2Fquery%2Fdev16.query%3FappId%3DDev16IDEF1%26l%3DEN-US%26k%3Dk(System.Net.Mail.SmtpClient.EnableSsl);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)%26rd%3Dtrue&view=netcore-3.1)

 *Значение будет взято из [Setting_MailserverSsl](#Setting_MailserverSsl), если оно было установлено.*

**`To`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

A string that contains the addresses of the recipients of the email message. Multiple email addresses must be separated with a comma character (",").

**`Subject`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

A string that contains the subject text.

**`Is HTML`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8)

``true`` - if the message body is in HTML; ``false`` - if the message body is not HTML.
  
**`Body`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

A string that contains the message body.

### FillApproversUsers

[Table of contents](#Сontent)

Заполнение списка пользователей, согласование с которыми необходимо.

**Параметры:**

**`Users`** [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список пользователей, указанных через разделитель.

Example: User1, User2

**`Separator`** [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между указываемым списком пользователей.

Default value: comma

**`Get users from`** : [GetUsersFrom](#GetUsersFrom) [**\***](#* 'Required parameter')

Задает поведения для выбора источника получаемого списка пользователей.

Default value: FromParameters

**`Stage name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя этапа, для которого необходимо получить список пользователей. *Передается в [ApproversInStageAsync](#ApproversInStageAsync)*

### FillApproversRoles

[Table of contents](#Сontent)

Заполнение списка [rules](/documentation/scheme/rules/), согласование с которыми необходимо.

*Доступен, если есть подписка на делегат [ApproversInStageAsync](#ApproversInStageAsync).*

**Параметры:**

**`Roles`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список [rules](/documentation/scheme/rules/), указанных через разделитель.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между указанными [rules](/documentation/scheme/rules/). 

Default value: comma

## Conditions

read about [conditions](/documentation/scheme/conditions/)

### CheckParameter

[Table of contents](#Сontent)

Сравнивает значение [parameter](/documentation/scheme/parameters/) текущего или родительского [process](/documentation/execution/regular-process/) с указанным.

 *Поддерживаются только строковые значения. Если вам нужно писать сложные условия используйте [conditions](/documentation/scheme/conditions/) or [expressions](/documentation/scheme/conditions/#expressions).*

**Параметры:**

**`Parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя параметра, значение которого будет сравниваться с ожидаемым.

**`Compare type`** : [CompareType](#CompareType) [**\***](#* 'Required parameter')

CompareType определяет поведение при сравнении значений.

**`Value`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Одно значение или список значений, указанных через разделитель.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

*Only for In/NotIn type compare*. Разделитель между указанными значениями.

Default value: comma

**`For root process`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

``true`` - Будут получены [parameters](/documentation/scheme/parameters/) основного [process](/documentation/execution/regular-process/); ``false`` -  Будут получены [parameters](/documentation/scheme/parameters/) текущего [process](/documentation/execution/regular-process/).

  Default value: false

  *Read about [subprocesses](/documentation/execution/subprocesses/).*

### CheckAllSubprocessesCompleted

[Table of contents](#Сontent)

Проверяет все ли [subprocesses](/documentation/execution/subprocesses/), созданные в заданом [process](/documentation/execution/regular-process/), завершены.

**Параметры:**

**`Mode`** : [Mode](#Mode) [**\***](#* 'Required parameter')

Mode определяет поведение сравнения.

### IsProcessFinish

[Table of contents](#Сontent)

Проверяет завершен ли [process](/documentation/execution/regular-process/). Если в параметре указан ProcessId, то проверяется [process](/documentation/execution/regular-process/) с этим Id. Если нет, то проверка идет по текущему [process](/documentation/execution/regular-process/).

**Параметры:**

**`Process id`** : [Guid](https://docs.microsoft.com/en-us/dotnet/api/system.guid?view=netframework-4.8) [**\***](#* 'Required parameter')

Id [process](/documentation/execution/regular-process/), завершение которого проверяется.

*If not set will be use id for current [process](/documentation/execution/regular-process/).*

### IsApprovedByUsers

[Table of contents](#Сontent)

Проверяет, есть ли среди согласовавших пользователи с таким идентификаторам.

**Параметры:**

**`Users`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список пользователей, указанных через разделитель.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между пользователями в списке.

Default value: comma

### IsApprovedByRoles

[Table of contents](#Сontent)

Проверяет, есть ли среди согласовавших пользователи [rules](/documentation/scheme/rules/).

*Доступен, если есть подписка на делегат [UsersInRoleAsync](#UsersInRoleAsync).*

**Параметры:**

**`Roles`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Список [rules](/documentation/scheme/rules/), указанных через разделитель.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между ролями в списке.

Default value: comma

### CheckHTTPRequest

[Table of contents](#Сontent)

Отправляет HTTP(s) запрос по указанному Url и сравнивает результат с контрольным значением.

**Параметры:**

**`Url`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

The Uri the request is sent to.

**`UserName`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Имя пользователя, которое будет использовано в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Password`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Пароль, который будет использован в [NetworkCredential](https://docs.microsoft.com/ru-ru/dotnet/api/system.net.networkcredential?view=netframework-4.8) при создании запроса.

**`Post`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8)

``true`` - post request; ``false`` -  get request.

**`Store response`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8)

``true`` -  Результат сохраняется в [parameter](/documentation/scheme/parameters/) с указанными в параметрах именем, который имеет тип [temporary](documentation/plugins/filepluginapi#ParameterPurpose); ``false`` -  Результат не будет сохранен в переменную.
  
**`Result field name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)

Поле в ответе, которое необходимо сравнить.

  *Если этот параметр не указан - будет сраниваться весь результат.*

**`Compare type`** : [compare type](#CompareType) [**\***](#* 'Required parameter')

read about [compare type](#CompareType).

**`Result field value`**

Одно значение или список значений, указанных через разделитель.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

*Only for In/NotIn type compare.* Разделитель между значениями.

Default value: comma

**`Add process Id and scheme in parameters`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

``true`` - process id будет добавлен в параметры запроса; ``false`` -  process id не будет добавлен в параметры запроса.
  
**`Content type`** : [content type](#ContentType) [**\***](#* 'Required parameter')

Only for post request. Формат полученного ответа.

**`Headers`**

Строка, которая представляет из себя набор пар ключ - значение. Которые затем будут добавлены в [DefaultRequestHeaders](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient.defaultrequestheaders?f1url=https%3A%2F%2Fmsdn.microsoft.com%2Fquery%2Fdev16.query%3FappId%3DDev16IDEF1%26l%3DEN-US%26k%3Dk(System.Net.Http.HttpClient.DefaultRequestHeaders);k(TargetFrameworkMoniker-.NETFramework,Version%3Dv4.5);k(DevLang-csharp)%26rd%3Dtrue%26f%3D255%26MSPPError%3D-2147217396&view=netcore-3.1) для указанного запроса.

**`Parameters`**

Only for post request. Параметры запроса типа, указанного в [content type](#ContentType).

### IsApproveComplete

[Table of contents](#Сontent)

Проверяет были ли получены все необходимые согласования.**

## Rules

read about [rules](/documentation/scheme/rules/).

### CheckRole

[Table of contents](#Сontent)

Определяет соответствие текущего пользователя и [rule](/documentation/scheme/rules/), указанной в параметре.

В качестве [CheckAsync](/documentation/scheme/rules/#provider) и [GetIdentitiesAsync](/documentation/scheme/rules/#provider) методов используется делегат [settings](#Settings) [GetPredefinedIdentitiesAsync](#GetPredefinedIdentitiesAsync). 

*Доступен из интерфейса [designer](/documentation/main-terms/designer/), если есть подписка на делегат [UsersInRoleAsync](#UsersInRoleAsync).* 

*Пример использования [здесь](/documentation/faq/workflow-engine/manage-roles/).*

 *Используется для [FillApproversRoles](#FillApproversRoles), [IsApprovedByRoles](#IsApprovedByRoles).*

### Approver

[Table of contents](#Сontent)

Определяет наличие текущего пользователя в списке, заданном методом [FillApproversUsers](#FillApproversUsers).

В качестве [CheckAsync](/documentation/scheme/rules/#provider) и [GetIdentitiesAsync](/documentation/scheme/rules/#provider) методов используется список пользователей, заданный методом [FillApproversRoles](#FillApproversRoles).

 *Используется для [FillApproversRoles](#FillApproversRoles).*

### Predefined

[Table of contents](#Сontent)

Определяет [преодопеделенных пользователей](/documentation/plugins/basicpluginapicases#PredefinedActors).

В качестве [CheckAsync](/documentation/scheme/rules/#provider) метода используется делегат [settings](#Settings) [CheckPredefinedActorAsync](#CheckPredefinedActorAsync). 

В качестве [GetIdentitiesAsync](/documentation/scheme/rules/#provider) метода используется делегат [settings](#Settings) [GetPredefinedIdentitiesAsync](#GetPredefinedIdentitiesAsync).

 *Используется для [PredefinedActors](/documentation/plugins/basicpluginapicases#PredefinedActors) .*

## Elements

### SetAfter

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|AfterAction | Выполнить действие после [action](/documentation/scheme/actions/). [Actions](/documentation/scheme/actions/) указанные после текущего **выполнены не будут**|
|AfterActivity | Выполнить действие после [activity](/documentation/scheme/activities/). Все [actions](/documentation/scheme/actions/) указанные в [activity](/documentation/scheme/activities/) будут выполнены и только затем будет произведен переход.|

### GetUsersFrom

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|FromParameters | Значение будет получено из параметров, переданных из формы|
|FromApproversInStage | Значение будет получено из делегата [ApproversInStageAsync](#ApproversInStageAsync)|

### ContentType

[Table of contents](#Сontent)

- application/x-www-form-urlencoded

  Form ~~data~~ is encoded as name/value pairs.

**Example:**

``` name/value
Name 1 = Value 1;
Name 2 = Value 2;
Name 3 = Value 3;
```

- application/json

  Form data is encoded as json.

**Example:**

``` json
{
 "Name 1": "Value 1",
 "Name 2": "Value 2",
 "Name 3": "Value 3",
}
```

### CompareType

[Table of contents](#Сontent)

| CompareType | Description & Examples |
|----------------|----------------|
| Equal(n, v) | n = y|
| NotEqual(n, v) | n <> y|
| Contains | "yummy" contains "umm"|
| StartWith | "yummy" start with "yu"|
| EndWith| "yummy" end with "my"|
| NotContains| "yummy" not contains "yy"|
| StartAndEndWith |"yummy" start and end with "y" |
| NotStartWith | "yummy" not start with "my"|
| NotEndWith | "yummy" end with "yu"|
| NotStartAndEndWith | "yummy" not start and end with "mm" |
| Greater(n, y) | n > y|
| Less(n, y) | n < y|
| GreaterOrEqual(n, y) |  n >= y|
| LessOrEqual(n, y) | n <= y|
| In | 5 in (1,2,3,4,5)|
| NotIn | 6 not in (1,2,3,4,5)|

### Mode

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|AllSubprocesses | all the [subprocesses](/documentation/execution/subprocesses/)|
|AllSubprocessesAndParent | all the [subprocesses](/documentation/execution/subprocesses/) and parent|

