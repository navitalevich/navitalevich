# LoopsPlugin

[Плагин](/documentation/plugins/), который реализует функции для организации циклов в вашей схеме.

## Сontent

1. [Actions](#Actions)
    1. [StartLoopFor](#StartLoopFor)
    2. [StartLoopForeach](#StartLoopForeach)
    3. [StartLoopForeachFromParameter](#StartLoopForeachFromParameter)
    4. [SetLoopState](#SetLoopState)
2. [Conditions](#Conditions)
    1. [LoopIsBroken](#LoopIsBroken)
    2. [LoopIsCompleted](#LoopIsCompleted)
    3. [LoopIsCompletedOrBroken](#LoopIsCompletedOrBroken)
    4. [LoopIsNotCompletedAndBroken](#LoopIsNotCompletedAndBroken)
    5. [LoopIsDefault](#LoopIsDefault)
    6. [LoopIsNotDefault](#LoopIsNotDefault)
3. [Elements](#Elements)
    1. [DateTime format](#DateTimeFormat)
    2. [DateTime step format](#DateTimeStepFormat)

## Actions

Read about [actions](/documentation/scheme/actions/).

### StartLoopFor

[Table of contents](#Сontent)

Инициализация и запуск цикла For.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя создаваемого цикла.

Default value: Loop

**`Loop state parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в коротором хранится текущее состояние цикла [LoopStates](/documentation/plugins/loopsplugincases#LoopStates)

Default value: LoopState

**`Loop counter value parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в котором хранится значение счетчика [LoopCounter](/documentation/plugins/loopsplugincases#LoopCounter) [**\***](#* 'Required parameter')

Default value: LoopCounterValue

**`Counter type`** : [CounterType](/documentation/plugins/loopsplugincases#CounterType) [**\***](#* 'Required parameter')

Определяет тип переменной используемой в цикле.

Default value: Int

**`Start value`** [**\***](#* 'Required parameter')

Начальное значение счетчика: если [`Int`](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) - любое целое число; если [`DateTime`](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=netframework-4.8) - read about [DateTime Format](#DateTimeFormat).

**`Step`** [**\***](#* 'Required parameter')

Шаг счетчика: если [`Int`](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) - любое целое число; если [`DateTime`](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=netframework-4.8) - read about [DateTime step format](#DateTimeStepFormat).

**`Step type`** : [StepType](/documentation/plugins/loopsplugincases#StepType)

Определяет тип итератора.

Default value: Increment

**`End value`** [**\***](#* 'Required parameter')

Конечное значение счетчика: если [`Int`](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.8) - любое целое число; если [`DateTime`](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=netframework-4.8) - read about [DateTime Format](#DateTimeFormat).

**`Include last value`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, учитывается ли последнее значение: `true` эквивалентно <= или>= ; `false` эквивалентно < или >

Default value: false

### StartLoopForeach

[Table of contents](#Сontent)

Инициализация и запуск цикла Foreach.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя создаваемого цикла.

Default value: Loop

**`Loop state parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в коротором хранится текущее состояние цикла [LoopStates](/documentation/plugins/loopsplugincases#LoopStates)

Default value: LoopState

**`Loop counter value parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8)  [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в котором хранится значение счетчика [LoopCounter](/documentation/plugins/loopsplugincases#LoopCounter)

Default value: LoopCounterValue

**`Values`**  [**\***](#* 'Required parameter')

Элементы счетчика, указанные через разделитель.

Example: Value1, Value2

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между значениями.

Default value: comma

**`Reverse`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, необходимо ли сделать инверсию списка значений.

Default value: false

### StartLoopForeachFromParameter

[Table of contents](#Сontent)

Инициализация и запуск цикла Foreach.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя создаваемого цикла.

Default value: Loop

**`Loop state parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в коротором хранится текущее состояние цикла [LoopStates](/documentation/plugins/loopsplugincases#LoopStates)

Default value: LoopState

**`Loop counter value parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), в котором хранится значение счетчика [LoopCounter](/documentation/plugins/loopsplugincases#LoopCounter)

Default value: LoopCounterValue

**`Parameter name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя [parameter](/documentation/scheme/parameters/), из которого будет получен список элементов разделенных разделителем.

**`Separator`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Разделитель между значениями.

Default value: comma

**`Reverse`** : [Boolean](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.8) [**\***](#* 'Required parameter')

Флаг, необходимо ли сделать инверсию списка значений.

Default value: false

### SetLoopState

[Table of contents](#Сontent)

Выполняет Continue/Break для цикла

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла, для которого необходимо изменить состояние.

**`Loop State`** : [LoopStates](/documentation/plugins/loopsplugincases#LoopStates) [**\***](#* 'Required parameter')

Состояние, в которое будет установлен цикл: Continue/Break.

## Conditions

read about [conditions](/documentation/scheme/conditions/)

### LoopIsBroken

[Table of contents](#Сontent)

Проверяет была ли прервана работа цикла.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

### LoopIsCompleted

[Table of contents](#Сontent)

Проверяет был ли выполнен цикл.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

### LoopIsCompletedOrBroken

[Table of contents](#Сontent)

Проверяет находится ли цикл в одном из состояний: Complete, Break. Это означает, что работа цикла была завершена или прервана.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

### LoopIsNotCompletedAndBroken

[Table of contents](#Сontent)

Проверяет находится ли цикл в одном из состояний: Default, Continue. Позволяет определить будет ли выполнена ещё одна итерация цикла.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

### LoopIsDefault

[Table of contents](#Сontent)

Проверяет находится ли цикл в состоянии: Default.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

### LoopIsNotDefault

[Table of contents](#Сontent)

Проверяет находится ли цикл в одном из состояний: Complete, Continue, Break. Это означает, что цикл был выполнен или была вызвана одна из оперций Continue, Break.

**Параметры:**

**`Loop name`** : [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8) [**\***](#* 'Required parameter')

Имя цикла состояние которого будет проверяться.

## Elements

### DateTimeFormat
[Table of contents](#Сontent)

- Формат: yyyy-MM-dd HH:mm:ss.fff
- Минимальное значение: 0001-01-01 00:00:00.000

Для работы с [`DateTime`](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=netframework-4.8) вы можете использовать расширения, например:

```C#
using OptimaJet.Workflow.Core.Plugins;

//For cast DateTime to string
string dateTimeString = DateTime.Now.ToLongStringDateTime();

//For cast string to DateTime
DateTime = dateTimeString.ToLongDateTime();
```

#### DateTimeStepFormat

[Table of contents](#Сontent)

В качестве шага вы можете установить значение:

- integer followed by y, year or years, its value is interpreted as years.
- integer followed by mm, month or months, its value is interpreted as months (Количество дней определяется по календарю соотвествующего года);
- integer followed by d, day or days, its value is interpreted as days (24 hours);
- integer followed by h, hour or hours, its value is interpreted as hours;
- integer followed by m, minute or minutes, its value is interpreted as minutes;
- integer followed by s, second or seconds, its value is interpreted as seconds;
- integer followed by ms, millisecond or milliseconds, its value is interpreted as milliseconds;

*The measurement units may be combined, for example, "1y 3mm 2d 5h 24m 15s 50 ms", "2days 5hours", etc*

