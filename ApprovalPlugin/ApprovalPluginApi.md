# ApprovalPlugin

[Плагин](/documentation/plugins/), который реализует функции для работы с [Approval history](documentation/plugins/approvalplugincases#Approval-history) вашего документа и [Inbox](documentation/plugins/approvalplugincases#Inbox)/[Outbox](documentation/plugins/approvalplugincases#Outbox) 

## Сontent

1. [Settings](#Settings)
    1. [AutoApprovalHistory](#AutoApprovalHistory)
    2. [GetUserNamesByIds](#GetUserNamesByIds)
    3. [NameParameterForComment](#NameParameterForComment)
2. [Actions](#Actions)
    1. [FillApprovalHistory](#FillApprovalHistory)
    2. [GetApprovalHistory](#GetApprovalHistory)
    3. [GetInbox](#GetInbox)
    4. [GetOutbox](#GetOutbox)
3. [Elements](#Elements)
    1. [Get parameter type](#Get-Parameter-Type)
    2. [Paging](#Paging)

## Settings

### AutoApprovalHistory

[Table of contents](#Сontent)

[Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8): Флаг автоматической записи истории согласований

``true`` - [FillApprovalHistory](#FillApprovalHistory) автоматически добавляется в [activities](/documentation/scheme/activities/) с помощью [buildstep](/documentation/execution/build-steps/). И становится не доступен из [designer](/documentation/main-terms/designer/). ``false`` - [FillApprovalHistory](#FillApprovalHistory) доступен из [designer](/documentation/main-terms/designer/) как обычный [Action](/documentation/scheme/actions/).

Default value: true

 *Используется для [FillApprovalHistory](#FillApprovalHistory).*

### GetUserNamesByIds

[Table of contents](#Сontent)

Делегат, ваша функция должна возвращать пользователей соотвутсвующих id из списка. Если нет подписки значение берется из processInstance.IdentityIds.

**Action syntax:**

```C#
List<string> GetMyUserNamesByIds(List<string> idS)
{
    //Вернуть имя для каждого пользователя из списка id. 

    //Пример:
    var names = new List<string>();
    foreach (var id in idS)
    {
        string name = myUsers[id].Name;
        names.Add(name);
    }

    return names;
}
```

 *Используется для [FillApprovalHistory](#FillApprovalHistory).*

### NameParameterForComment

[Table of contents](#Сontent)

[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8): Имя параметра, из которого берется комментарий при обновлении записи. 

Default value: Comment

*Используется для [FillApprovalHistory](#FillApprovalHistory).*

## Actions

— Read about [actions](/documentation/scheme/actions/).

### FillApprovalHistory

[Table of contents](#Сontent)

Запись и обновление этапов согласований для [approval history](documentation/plugins/approvalplugincases#Approval-history). 

*Если в настройках параметр [AutoApprovalHistory](#AutoApprovalHistory) равен `true` - этот [action](/documentation/scheme/actions/) автоматически добавляется в [activities](/documentation/scheme/activities/) с помощью [buildstep](/documentation/execution/build-steps/).* если `false` - [action](/documentation/scheme/actions/) не доступен.

### GetApprovalHistory

[Table of contents](#Сontent)

Получение записей [approval history](documentation/plugins/approvalplugincases#Approval-history).

**Параметры:**

**`Get parameter type`** : [GetParameterType](#Get-Parameter-Type) [**\***](#* 'Required parameter')

Задает фильтр для получения записей: ProcessId  or IdentityId.

**`Get parameter value`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

ProcessId  or IdentityId for selecting record. Depending on [GetParameterType](#GetParameterType).

**`Parameter purpose`** : [ParameterPurpose](documentation/plugins/filepluginapi#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

Default value: Temporary

**`Parameter name`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/) для сохранения полученных записей.

**`PageIndex`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

**Нумерация страниц начинается с 1.** Задает текущий номер страницы для [paging](#Paging).  

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

**`PageSize`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

Задает количество записей на одной странице для [paging](#Paging). 

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

### GetInbox

[Table of contents](#Сontent)

Получение записей [inbox](documentation/plugins/approvalplugincases#Inbox).

**Параметры:**

**`Get parameter type`** : [GetParameterType](#Get-Parameter-Type) [**\***](#* 'Required parameter')

Задает фильтр для получения записей: ProcessId  or IdentityId.

**`Get parameter value`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

ProcessId  or IdentityId for selecting record. Depending on [GetParameterType](#GetParameterType).

**`Parameter purpose`** : [ParameterPurpose](documentation/plugins/filepluginapi#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

Default value: Temporary

**`Parameter name`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/) для сохранения полученных записей.

**`PageIndex`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

**Нумерация страниц начинается с 1.** Задает текущий номер страницы для [paging](#Paging).  

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

**`PageSize`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

Задает количество записей на одной странице для [paging](#Paging). 

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

### GetOutbox

[Table of contents](#Сontent)

Получение записей [outbox](documentation/plugins/approvalplugincases#Outbox).

**Параметры:**

**`Get parameter type`** : [GetParameterType](#Get-Parameter-Type) [**\***](#* 'Required parameter')

Задает фильтр для получения записей: ProcessId  or IdentityId.

**`Get parameter value`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

ProcessId  or IdentityId for selecting record. Depending on [GetParameterType](#GetParameterType).

**`Parameter purpose`** : [ParameterPurpose](documentation/plugins/filepluginapi#ParameterPurpose) [**\***](#* 'Required parameter')

ParameterPurpose определяет поведение при сохранении параметра.

Default value: Temporary

**`Parameter name`**  : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/) для сохранения полученных записей.

**`PageIndex`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

**Нумерация страниц начинается с 1.** Задает текущий номер страницы для [paging](#Paging). 

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

**`PageSize`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

Задает количество записей на одной странице для [paging](#Paging). 

Default value: -1

*Если указанное значение < 1 - [paging](#Paging) выполнен не будет.*

## Elements

### Get parameter type

[Table of contents](#Сontent)

|Значение| Описание |
|----------------|----------------|
|IdentityId |Получить записи, где IdentityId имеет указанное значение|
|ProcessId |Получить записи, где ProcessId имеет указанное значение|

### Paging

[Table of contents](#Сontent)

Разбиение данных на страницы и их последующее получение частями с целью оптимизации работы.

**Параметры**

**`PageIndex`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

**Нумерация страниц начинается с 1.** Задает текущий номер страницы для разделения записи на страницы.  

Нумерация страниц начинается с 1.

**`PageSize`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

Задает количество записей на одной странице для разделения записи на страницы.

**`SkipCount`** : [Int32](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8)

**Рассчитывается автоматически**. Задает количество записей, которое будет пропущено и рассчитывается как: **(PageIndex - 1) \* PageSize**
