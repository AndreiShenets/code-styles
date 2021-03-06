﻿# Выберите ваш язык / Choose your language

* [English](/README.md)
* [Русский](/ru/README.md)

# Стиль кода, который я рекомендую на данный момент

Еще со времен, когда я писал на Delphi, я люблю настаивать на соблюдении правил по стилизации кода. Причина была и есть довольно простая - без сомнения, код в едином стиле намного более легкий для чтения, а, как следствие, и понимания. В результате я пытался раз и навсегда выработать такие правила, которые будут подходить любому разработчику. Естественно, у меня это не получилось. Мой стиль кодирования менялся, когда я писал на Delphi, мой стиль кодирования менялся, когда я переключился на C\# и Javascript. Мой стиль кодирования эволюционирует даже сейчас, хоть и реже. Каждый язык программирования, который я изучал, показывал мне дополнительные проблемы с чтением и написанием кода, которые связаны с моим стилем, но также давал новые примеры и широко используемые приемы, которые формировали мой стиль.

Сейчас, смотря на эти попытки создать идеальный стиль, я понимаю, что это невозможно. Всегда найдутся недовольные, всегда люди будут думать по-разному и делать по-разному, где из-за лени, где из-за нежелания выходить из зоны комфорта, где по другим причинам. Особенно сильно это проявляется, если ты хочешь настаивать на безоговорочном соблюдении какого-то стиля как закона.

Однако, на мой взгляд, является достижимым выработать определенные рекомендации по стилю, которые позволят значительно увеличить качество кода, а также сделают код более читаемым и легче модифицируемым. Более того, такие рекомендации могут быть применимы к любому языку программирования.

Именно таким списком рекомендаций данный репозиторий и является. Так же он содержит некоторые примеры кода с соблюдением моих рекомендаций.

Еще раз хочу заострить внимание, что я предлагаю **рекомендации**. Хотя я бы лучше назвал их **строгими / настоятельными рекомендациями**. В моем понимании рекомендациям можно следовать, а можно нет, с другой стороны, если рекомендации строгие, то следовать им нужно, однако они не являются законом, и от них можно отступиться, если это даст какой-то более существенный бонус.

И небольшое **предупреждение**: мои рекомендации могут измениться со временем, если я найду что-то более стоящее и более удобное.

# Основные принципы

1. Код должен быть хорошо читаемым => Читаемость
2. Код должен быть удобен для написания и изменения => Написание
3. Код должен хорошо выглядеть, нравиться => Внешний вид / Стиль

При написании кода стоит руководствоваться "правилами" выше. И, что очень важно!, именно в том порядке, в котором они записаны. В первую очередь код должен быть читаемым. Обоснование крайне простое: по разным оценкам, которые могут от проекта к проекту варьироваться, программисты тратят где-то 70-80% времени на чтения кода. Добавьте к этому тот факт, что ваш код будут читать ваши коллеги, и им его читать будет сложнее. Добавьте к этому, что через неделю или две вы забудете, что происходит у вас в коде и будете сами читать свой код.

**Вывод**: в первую очередь код должен быть читаемым.

Однако стоит помнить, что вы еще и пишете код, поэтому ваш стиль должен давать хорошо читаемый код и быть чем проще, тем лучше, чтобы писать код было удобно. Простота стиля также позволит писать код быстрее. Если стоит выбор между написать немного больше и/или чуть менее удобно, но более читаемо, то стоит выбрать **написать менее удобно, но более читаемо**.
Еще стоит хорошо помнить, что код не только пишется в первый раз, но и поддерживается. Это значит, что при изменении вашего кода вы не должны тратить дополнительных усилий для приведения его в читаемый вид. В первую очередь это относится к выравниванию кода, которого стоит избегать в большинстве случаев (выравнивание будет рассмотрено подробнее позже).

**Вывод**: Код должно быть удобно писать и модифицировать, но читаемость всё же важнее.

При соблюдении первых двух пунктов вы можете менять свой стиль как вам *нравится*. Многие разработчики ставят пункт 3 во главу списка. Я крайней не рекомендую так делать. Вместо это я настоятельно рекомендую, особенно если вы уполномоченное лицо на проекте, прописать для всех членов команды стиль, который вы будете использовать на проекте, дабы код был одинаковым. К этому я настоятельно рекомендую настроить проверку стиля автоматическими инструментами, например ReSharper для C# или eslint в JavaScript. Можно добавить инструменты для автоматического форматирования, если есть желание. Также можно настроить pre-commit hooks в вашей системе контроля версий для отсечения "плохих" коммитов. Однако оставьте возможность отменить автоформатирование, иногда определенное исключение действительно важно. Например если вы описываете одномерный массив как матрицу.

При соблюдении всех правил вы получите хорошо читаемый, легко модифицируемый код, который вам будет нравится визуально.
Вы и любой член вашей команды сможет легко прочитать код, пускай, возможно, и не понять его. Как говориться: "Лучше хорошо читаемый код и плохая архитектура, чем наоборот".
Ваша производительность, а также производительность вашей команды вырастет за счет автоматических инструментов и единого стиля.

# Читаемость

## Длина строки

Я **рекомендую ограничиться максимальную длину строки** кода **120** символами.

**Обоснование:**

В обосновании хочу рассказать о проблемах со слишком длинными строками. В первую очередь они ухудшают читаемость, т.е. нарушают основополагающее правило 1. Слишком длинная строка заставляет вас отвлекаться от чтения и понимания и переключаться на горизонтальную прокрутку, что крайне неудобно и затратно по времени. Кроме того, если что-то скрыто за границей экрана, может быть потеряно из вида и не принято во внимание, что приведет к ошибкам в коде или другим проблемам. Например, вы не заметили важные параметры функции или пропустили важное условие.

Отсюда следует вывод **слишком длинные строки - плохо**

Но какая же длина строки приемлемая? Давайте рассмотрим, как обычному человеку удобно читать код и как можно делать это наиболее быстро и продуктивно. Согласно некоторым исследования, удобная полоса чтения для среднестатистического человека порядка 80-100 символов. Тут можно было бы сказать: "Давайте ограничим длину 100 символами". Однако стоит принять во внимание, что на данный момент для работы используются широкоформатные мониторы, чаще всего FullHD (1920x1080) (например, у нас стандарт 22-24 дюйма). Возможно там, где вы работаете другой стандарт, опишу это ниже.
Самые частые операции с кодом, исходя из практики, следующие:
    - Чтение
    - Чтение на одном мониторе в редакторе с двумя панелями
    - Написание / Изменение
    - Написание / Изменение в редакторе с двумя панелями
    - Сравнение в инструменте с двумя панелями
    - Решение конфликтов при слиянии в инструменте с тремя панелями
    - Чтение запроса на слияние (Pull request) в инструменте или на сайте. Две панели.

Принимая во внимание, что вы или ваши коллеги могут использовать / используют две панели на одном мониторе для различных целей, стоит выбирать такую длину строки, которая позволит видеть всю строку кода в обоих рядом стоящих панелях. Очень хорошо проверять данное правило на запросах на слияние на GitHub. Экспериментально выяснено, что в случае 120 символов:
1. Обычно всё влезает
2. Обычно всё влезает, даже если у вашего коллеги плохое зрение и больше шрифт
3. Есть небольшой буфер, если перенос строки невозможен или нецелесообразен.

Если у вас в команде размер мониторов и/или расширения выше, то вы можете определить другую длину строки и зафиксировать ее для всей команды.

Отсюда следует вывод: **по умолчанию** оптимально использовать ограничение в **120** символов.

# Написание и, как следствие, читаемость

Написание — это то, от чего сильно зависит читаемость. В первую очередь хочется продолжить тему про то, как обычно человек читает текст. В нашем случае мы рассматриваем чтение слева направо сверху вниз. Мозг человека построен так, что он оптимизирует производительность чтения. Для оптимизации у него есть отличный инструмент, который некоторыми учеными называется визуальное мышление (Visual Thinking). Суть его примерно следующая: когда наш мозг видит (через глаз естественно) что-то, что он часто обрабатывает, он пытается по внешнему виду (как будто по слепку или хэш значению) быстро получить сопоставленный результат (своеобразное кэш хранилище ключ-значение). Если ассоциации нет или в процессе быстрой проверки что-то наш мозг насторожило, то задействуется логическое мышление (Logical Thinking), которое детально анализирует то, что написано и делает выводы.

Примеры такого поведения можно найти в интернете. Есть эксперимент, когда записывается какой-то цвет, например красный, но цвет текста делается, например синий. В первую очередь отрабатывает визуальное мышление синий цвет + "красный" текст == синий, потом срабатывает "проверка" и задействуется логическое мышление синий цвет + "красный" текст == ~~синий~~ красный. Особенность данного поведения мозга в том, что визуальное мышление работает на порядки быстрее логического.

Отсюда можно сделать **вывод**: лучше писать код так, чтобы максимально задействовать визуальное мышление.

Как?

Мозг задействует в первую очередь визуальное мышление если:
1. Текст выделяется размером
2. Текст выделяется посредством близости к другому тексту
3. Текст выровнен

Пункт 1 это регистр символов. Например константы могут выглядеть вот так:
```csharp
public const string SOME_SHOUTY_CONSTANT = "My const";
```

Пункт 2 это фактически группировка кода в маленькие логически связанные блоки. Блоки разделаются пустой строкой. Например:

```csharp
public ResultType ArbitraryMethodName(
    FirstArgumentType firstArgument,
    SecondArgumentType secondArgument,
    ThirdArgumentType thirdArgument
)
{
    LocalVariableType localVariable = Method(
        firstArgument,
        secondArgument
    );

    if (
        localVariable.IsSomething(
            thirdArgument,
            SOME_SHOUTY_CONSTANT
        )
    )
    {
        DoSomethingWith(localVariable);
    }

    return localVariable.GetSomething();
}
```

## Выравнивание (пункт 3)

В примере выше также использовано и выравнивание.

Если коротко, то для выравнивания должны быть использованы только новая строка + отступы. Клавиша Enter и клавиша Tab, которая трансформируется будь то в символ табуляции, 2, 4 или N пробелов. Я **настоятельно рекомендую** использовать пробелы, т.к. вы точно не будете иметь проблем с отступами, например, в случае с запросами на слияние.

**Настоятельная рекомендация**: группировка и выравнивание блоков происходит за счет переноса их на новую строку. Если блок относится к предыдущей строке, добавляется сдвиг вправо на один отступ.

**Обоснование:**

Цель задействовать визуальное мышление.
Почему только отступы и новые строки? Как следует из правила 2 - код должен быть легко модифицируемым. Часто разработчики любят делать вот так:

```Java
int doNotFormat = likeThis(someArgumentOrExpression,
                           anotherArgumentOrExpression);
```

С одной стороны всё круто, задействовано визуальное мышление, с другой сломано удобство редактирования. Например, при переименовании функции выравнивание сломается.

**Вывод**: код должен быть устойчивым к изменениям. Намного лучше написать:

```Java
int insteadFormat =
    somethingLikeThis(
        someArgumentOrExpression,
        anotherArgumentOrExpression
    );


int orFormat = somethingLikeThis(
    someArgumentOrExpression,
    anotherArgumentOrExpression);


int orFormat = somethingLikeThis(
    someArgumentOrExpression,
    anotherArgumentOrExpression
);
```

Рекомендую самый последний вариант, так как он позволяет более четко отделить параметры, параметры проще добавлять, менять местами и так далее.

Почему плохо вот так:

```Java
int insteadFormat = somethingLikeThis(someArgumentOrExpression,
    anotherArgumentOrExpression);
```

Тут хорошее место чтобы упомянуть, что хорошо читаемый код во многом является хорошо читаемым из-за осмысленных имен функций, методов, переменных (так называемый самоописывающийся код). Если того будет требовать читаемость, код может стать чем-то таким:

```Java
int longNameBecauseINeedItForBetterReadability = somethingLongNamedFunctionForBetterReadability(someArgumentOrExpression,
    anotherArgumentOrExpression);
```

В этом случае параметры разделены большим расстоянием, получилось так потому, что мы использовали переименование где-то в другом месте, а "плохо" стало тут - "отломано" визуальное мышление. Т.е. код не является устойчивым к изменениям.

# Краткие итоги

**Что делаем:**
- Считаем что Читаемость > Написание > Внешний вид
- Считаем что Визуальное мышление > Логическое мышление и используем:
    - Длина строки <= 120 (по умолчанию)
    - Логические блоки с помощью новой строки
    - Выравнивание новой строкой и отступами
    - "Устойчивый" код

**Что используем:**
- Клавишу Enter для новой строки
- Клавишу Tab для отступа

Проще некуда!

**Что получаем:**
- Быстрое чтение сверху вниз с использованием только вертикальной прокрутки
- Осмысление только важных в данный момент вещей за счет быстрого визуального мышления / увеличение своей производительности и производительности команды
- Редактирование кода без дополнительных усилий
- Код выглядит хотя бы хорошо и в одном стиле.

# Что посмотреть еще?

> To answer the question "What is clean design?" most succinctly: a clean design is one that supports visual thinking so people can meet their informational needs with a minimum of conscious effort.
*Daniel Higginbotham*
*"Clean Up Your Mess — A Guide to Visual Design for Everyone"*
[Site](http://www.visualmess.com/)

[Kevlin Henney - Seven Ineffective Coding Habits of Many Programmers](https://vimeo.com/97329157)

# Примеры

**Настоятельно рекомендую** все блоки выражений **всегда** окружать скобками или другими способами языка, явно указывающими на начало и конец блока. Пример if ниже.

*C\#*
```csharp
public ResultType ArbitraryMethodName(
    FirstArgumentType firstArgument,
    SecondArgumentType secondArgument,
    ThirdArgumentType thirdArgument)
{
    LocalVariableType localVariable = Method(
        firstArgument,
        secondArgument
    );

    if (
        localVariable.IsSomething(
            thirdArgument,
            SOME_SHOUTY_CONSTANT
        )
    )
    {
        DoSomethingWith(localVariable);
    }

    return localVariable.GetSomething();
}
```

Так же **никогда** не пишите логически разные части в одну строку как ниже:

*C\#*
```csharp
public ResultType ArbitraryMethodName(
    FirstArgumentType firstArgument,
    SecondArgumentType secondArgument,
    ThirdArgumentType thirdArgument)
{
    LocalVariableType localVariable = Method(firstArgument, secondArgument);
    if (localVariable.IsSomething()) return default(ResultType);
    return localVariable.GetSomething();
}
```

Намного лучше:

*JavaScript*
```javascript
function arbitraryMethodName(
    firstArgument,
    secondArgument,
    thirdArgument
) {
    doSomethingWith(localVariable);

    var localVariable = method(
        firstArgument,
        secondArgument
    );

    if (localVariable.IsSomething(
        thirdArgument,
        SOME_SHOUTY_CONSTANT))
    {
        doSomethingWith(localVariable);
    }

    return localVariable.getSomething();
}
```

Здесь использован еще один прием, который я **рекомендую**. Если у вас получается очень сложное условие в if, то стоит подумать о вынесении внутреннего содержимого в локальную переменную с осмысленным названием.

*JavaScript*
```javascript
function arbitraryMethodName(
    firstArgument,
    secondArgument,
    thirdArgument
) {
    doSomethingWith(localVariable);

    var localVariable = method(
        firstArgument,
        secondArgument
    );

    var isSomething = localVariable.IsSomething(
        thirdArgument,
        SOME_SHOUTY_CONSTANT
    );

    if (isSomething)
    {
        doSomethingWith(localVariable);
    }

    return localVariable.getSomething();
}
```

Пример использования цепочки вызовов. Тоже самое можно применить к конкатенации строк через `+`

*C\#*
```csharp
public IEnumerable<TrackViewModel> Sort(IEnumerable<TrackViewModel> viewModels)
{
    return viewModels
        .OrderBy(item => item.LoweredAlbumArtist)
        .ThenBy(item => item.AlbumNameForSorting)
        .ThenBy(item => item.Year)
        .ThenBy(item => item.DiskNumber)
        .ThenBy(item => item.TrackNumber)
        .ThenBy(item => item.Title);
}
```

```csharp
public override string ToString()
{
    return $"{ArtistName};"
        + $"{AlbumName};"
        + $"{Title};"
        + $"{Year};"
        + $"{DiskNumber};"
        + $"{TrackNumber};"
    ;
}
```

Здесь показана **рекомендация** по форматированию лямбда функций. А также **рекомендация** писать комментарии для кода, который невозможно быстро понять. Комментарий прочитать быстрее :)

*C\#*
```csharp
// Processing added or updated libraries
IEnumerable<ILibrary> addedLibraries = state
    .Libraries
    .Where(
        libraryKeyValuePair =>
        {
            ILibrary existingLibrary = _libraries
                .GetValueOrDefault(libraryKeyValuePair.Key);

            // The library is added
            return existingLibrary == null
                // Library has been changed
                || !ReferenceEquals(libraryKeyValuePair.Value, existingLibrary);
        }
    )
    .Select(libraryKeyValuePair => libraryKeyValuePair.Value);
```

Здесь пример как из примера выше сделать хуже - нужно использовать var. **Настоятельно рекомендую** в любом языке использовать явные объявления всего что только можно. Это позволит вам понимать с чем вы имеете дело без использования значительного количества логического мышления.

Мне могут возразить, что редакторы подсвечивают типы. Те, кто так думает, наведитесь мышкой на пример ниже, считайте, что это запрос на слияние, и задумайтесь, много ли вам браузер подсветил. И на сколько больше времени вы потратили на наведение, чем просто на прочтение.

*C\#*
```csharp
// Processing added or updated libraries
var addedLibraries = state
    .Libraries
    .Where(
        libraryKeyValuePair =>
        {
            var existingLibrary = _libraries
                .GetValueOrDefault(libraryKeyValuePair.Key);

            // The library is added
            return existingLibrary == null
                // Library has been changed
                || !ReferenceEquals(libraryKeyValuePair.Value, existingLibrary);
        }
    )
    .Select(libraryKeyValuePair => libraryKeyValuePair.Value);
```

Пример сложного конструктора:

*C\#*
```csharp
ImageFilteringDrawerPool<ArtistViewModel> imageFilteringDrawerPool =
    new ImageFilteringDrawerPool<ArtistViewModel>(
        imageDrawerOptions,
        new AllPassFilter<ArtistViewModel>(),
        new ExactYShift(
            TrackDrawingHelper.GROUP_INFO_MARGIN,
            new ExactXShift(TrackDrawingHelper.GROUP_INFO_MARGIN)
        ),
        new ResultHeightLogic(
            new ExactYShift(
                -TrackDrawingHelper.GROUP_INFO_MARGIN,
                new ExactXShift(
                    -TrackDrawingHelper.GROUP_INFO_MARGIN,
                    new TopRightShift(TrackDrawingHelper.NARROW_SPACE_SIZE)
                )
            )
        )
    );
```

Пример сложного if. Возможно в этом случае стоит присвоить результат условия локальной переменной с значащим названием, чтобы было понятно что там происходит, либо написать комментарий.

*C\#*
```csharp
if (range.TryGetValue("Group", out groupName)
    && range.TryGetValue("RIC", out ric)
    && (range.TryGetValue("ProcessedAt", out processedAtStr)
        || range.TryGetValue("Start", out startStr))
    && TimeSpan.TryParse(startStr, out start)
    && range.TryGetValue("End", out endStr)
    && TimeSpan.TryParse(endStr, out end)
    && DateTime.TryParse(processedAtStr, out processedAt))
{
```

*C\#*
```csharp
if (
    range.TryGetValue("Group", out groupName)
    && range.TryGetValue("RIC", out ric)
    && (range.TryGetValue("ProcessedAt", out processedAtStr)
        || range.TryGetValue("Start", out startStr)
    )
    && TimeSpan.TryParse(startStr, out start)
    && range.TryGetValue("End", out endStr)
    && TimeSpan.TryParse(endStr, out end)
    && DateTime.TryParse(processedAtStr, out processedAt)
)
{
```

*SQL*
```sql
select
    t1.*,
    t2.Id
from
    Table1 t1
    inner join Table2 t2
        on t1.Id == t2.Table1Id
where
    t1.Filter like '%empty%'
    and t2.Filter like '%non-empty%'
order by
    t2.Name
```

*JSX*
```jsx
<div className='top-menu' >
  <Link
    to='/settings'
    className='top-menu__setting-link'
  >
    {user.name || user.email}
  </Link>
  <button
    onClick={logOut}
    className='top-menu__logout-button'
  >
    Log out
  </button>
</div>
```

*Xaml*
```xml
<Page
    x:Class="MusicPlayer.Views.ArtistsPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    xmlns:mvvm="using:Prism.Windows.Mvvm"
    mvvm:ViewModelLocator.AutoWireViewModel="True"
>
    <Grid>
        <ScrollBar
            x:Name="VerticalScrollBar"
            Grid.Column="1"
            Orientation="Vertical"
            Visibility="Collapsed"
            IndicatorMode="MouseIndicator"
            LargeChange="128"
            SmallChange="32"
        />
    </Grid>
</Page>
```