# Choose your language / Выберите ваш язык

* [English](/README.md)
* [Русский](/ru/README.md)

# Code style guide I recommend at the moment

I have been keen on forcing code styles since I started to write code using Delphi language. The reason is quite simple - undoubtedly styled code much much more readable and easy to understand. As result I tried to invent some rules which make all developers happy. It is obvious that I failed. My code style was changing while I were writing on Delphi. It also was changing when I had switched to C\# and Javascript. My code style is changing from time to time now. Each language gave me additional issues, examples and style practices.

Looking back at intention to created ideal code style I understand that it is impossible. Especially if you want to invent law-like-rules. There are always unsatisfied people. There are always people that would like to do something in different way. There are always people that think differently.

But what is achievable is to recommend some style which significantly can improve quality of your code in different aspects. Moreover my recommendations are mostly applicable to any language.

Exactly such guide with recommendations you are reading right now. Also this guide contains some examples.

One more time I would like to pay attention that I propose **recommendations** I would possible call them **strong recommendations**. The difference is that recommendation is something that up to you to follow when on opposite side strong recommendations is something that you have to follow but there can be some exclusions in particular case. And of course this guide is not a law.

One more warning. This guide easily can change if I found more useful rules or handy ways to style code.

# Primary principles

1. Code has to have good readability => Readability
2. Code has to be easy writable and easy changeable => Writability
3. Code has to look good (You should like it from visual point of view) => Visual style

When you write code you should follow to the "rules" above and what is important! in order that described above. Firstly your code has to be readable. Justification is really simple: according to some researches developers spend about 70-80% percent of time to code reading. Add to this that your code is read by your colleagues and they usually didn't see the code before. Add to this that week or month later you will forget what your code about and you need to read and understand it again.

**Conclusion**: First of all code has to be readable.

However it is worth to remember that apart from reading of code you also write code. It means that your style should give well-readable code and in the same time your style should be as simple as possible to write code in handy way. Simple style also allow you to write code faster. If there is a choice between writing of a little more code in a little less convenient way, but result is more readable, then it's worth **choosing of less conveniently, but more readable style**.
Also it is worth to remember that code writes not only first time but also supports. It means that changing should not add additional efforts to make code readable after changes. Especially, this refers to code alignment, which should be avoided in most cases (alignment will be discussed in more detail later).

**Conclusion**: Your style should allow to write and change code in handy way, but readability is preferable.

If you follow to first two point then you can adjust other aspects as you *like*. Many developers put third "rule" above other two. I really do not recommend to do so. Instead I recommend, especially if you are in charge, set common style policy for all developers in your team - code should have only one style. Additionally I strongly recommend to set up automatic style checking and formatting tools like ReSharper for C# or eslint for JavaScript. Together with this I can set up pre-commit hooks to follow style policies. However leave some abilities to switch off these checks for particular cases. You may need it if you write matrix as one-dimensional array.

If you follow all recommendation you will get really readable easy modifiable code and you will like this code visually.
You and any member of your team will be able to read your code easily, even if he won't understand it. Some developers say "It is better to have readable code and bad solution architecture than vice versa".
Also you will see that performance of your team is higher because of automatic tools and singly style.

# Readability

## Line length

I **recommend to limit maximum length of a line of code** to **120** symbols.

**Justification:**

First of all I would like to mention issues that unlimited line length gives. First of all it decrease readability of your code so violates first recommendation. Too long line stops you from reading and understanding of code and forces you to use horizontal scrolling, what is unhandy and time-consuming. Also long lines hide important parts of code abroad screen, if you do not see it you can not take it in account and possibility to introduce some issue is higher. For example you can miss some important parameters or conditions.

So conclusion is **it is bad to have too long lines**

But what line length is good? Let's think about how usual developer reads code and how we can do it in the fastest and handiest way. According to some researches the most convenient width of line to read is about 80-100 symbols. At this point we would say let's limit line width at 100 symbols. But let's also take in account that at the moment we often use wide-screen FullHD monitors with resolution at least (1920x1080). For example in our company 24" Full HD monitors are standard.
Also the most common actions with code are:Reading
    - Reading
    - Reading using one monitor but two panel editor
    - Writing / Changing
    - Writing / Changing in editor using two or more panels
    - Comparing in tool with two panels
    - Merge conflict solving in tool with three panels
    - Pull request reading using tool or browser. Also can be two panels.

Принимая во внимание, что вы или ваши коллеги могут использовать / используют две панели на одном мониторе для различных целей, стоит выбирать такую длину строки, которая позволит видеть всю строку кода код в обоих рядом стоящих панелях. Очень хорошо проверять данное правило на запросах на слияние на GitHub. Экспериментально выяснено, что в случае 120 символов:
1. Обычно всё влазит
2. Обычно всё влазит даже если у вашего коллеги плохое зрение и больше шрифт
3. Есть небольшой буфер если перенос строки не возможен или нецелесообразен.

Если у вас в команде размер мониторов и/или расширения выше, то вы определить другую длину строки и зафиксировать ее для всей команды.

Отсюда следует вывод **по умолчанию** оптимально использовать ограничение в **120** символов.

# Написание и как следствие читаемость

Написание это то, от чего сильно зависит читаемость. В первую очередь хочется продолжить тему про то, как обычно человек читает текст. В нашем случае мы рассматриваем чтение слева на право сверху вниз. Мозг человека построен так, что он оптимизирует производительность чтения. Для оптимизации у него есть отличные инструмент, который некоторыми учеными называется визуальное мышление (Visual Thinking). Суть его примерно следующая: когда наш мозг видит (через глаз естественно) что-то, что он часто обрабатывает, он пытается по внешнему виду (как будто по слепку или хэш значению) быстро получить сопоставленный результат (своеобразное кэш хранилище ключ-значение), если ассоциации нет или в процессе быстрой проверки что-то наш мозг насторожило, то задействуется логическое мышление (Logical Thinking), которое детально анализирует то, что написано и делает выводы.

Примеры такого поведения можно найти в интернете. Есть эксперимент, когда записывается какой-то цвет, например красный, но цвет текста делается, например синий. В первую очередь отрабатывает визуальное мышление синий цвет + "красный" текст == синий, потом срабатывает "проверка" и задействуется логическое мышление синий цвет + "красный" текст == ~~синий~~ красный. Особенность данного поведения мозга в том, что визуальное мышление работает на порядки быстрее логического.

Отсюда можно сделать **вывод**: лучше писать код так, чтобы максимально задействовать визуальное мышление.

Как?

Мозг задействует в первую очередь визуальное мышление если:
1. Текст выделяется размером
2. Текст выделяется посредством близости к другому тексту
3. Текст выравнен

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

    if (localVariable.IsSomething(thirdArgument,
        SOME_SHOUTY_CONSTANT))
    {
        DoSomethingWith(localVariable);
    }

    return localVariable.GetSomething();
}
```

## Выравнивание (пункт 3)

В примере выше так же использовано и выравнивание.

Если коротко, то для выравнивания должны быть использованы только новая строка + отступы. Клавиша Enter и клавиша Tab, которая трансформируется будь то в символ табуляции, 2, 4 или N пробелов. Я **настоятельно рекомендую** использовать пробелы, т.к. вы точно не будете иметь проблем с отступами, например, в случае с запросами на слияние.

**Настоятельная рекомендация**: группировка и выравнивание блоков происходит за счет переноса их на новую строку, если блок относится к предыдущей строке добавляется сдвиг вправо на один отступ.

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
        anotherArgumentOrExpression);


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

Тут хорошее место чтобы упомянуть, что хорошо читаемый код во многом является хорошо читаемым из-за осмысленных имен функций, методов, переменных... Если того будет требовать читаемость, код может стать чем-то таким:

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
- Код выглядит хотя-бы хорошо и в одном стиле.

# Что посмотреть еще?

> To answer the question "What is clean design?" most succinctly: a clean design is one that supports visual thinking so people can meet their informational needs with a minimum of conscious effort.
*Daniel Higginbotham*
*"Clean Up Your Mess — A Guide to Visual Design for Everyone"*
[Site](http://www.visualmess.com/)

[Kevlin Henney - Seven Ineffective Coding Habits of Many Programmers](https://vimeo.com/97329157)

# Примеры

**Настоятельно рекомендую** все блоки выражений **всегда** окружать скобками или другими способами языка явно указывающими на начало и конец блока. Пример if ниже.

*C\#*
```csharp
public ResultType ArbitraryMethodName(
    FirstArgumentType firstArgument,
    SecondArgumentType secondArgument,
    ThirdArgumentType thirdArgument)
{
    LocalVariableType localVariable = Method(
        firstArgument,
        secondArgument);

    if (localVariable.IsSomething(thirdArgument,
        SOME_SHOUTY_CONSTANT))
    {
        DoSomethingWith(localVariable);
    }

    return localVariable.GetSomething();
}
```

Так же **никогда** не пишите логически разные части в одну строку как ниже:

*C\#*
```csharp
public void ArbitraryMethodName(
    FirstArgumentType firstArgument,
    SecondArgumentType secondArgument,
    ThirdArgumentType thirdArgument)
{
    LocalVariableType localVariable = Method(
        firstArgument,
        secondArgument);
    if (localVariable.IsSomething()) return
    return localVariable.GetSomething();
}
```

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

Здесь использован еще один прием, который я **рекомендую**. Если у вас получается очень длинная строка кода в if, то стоит подумать о вынесении внутреннего содержимого в переменную.

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

Пример использования цепочки вызовов. Тоже самом можно применить к конкатенации строк через `+`

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

Здесь показана **рекомендация** по форматирования лямбда функций. А так же **рекомендация** писать комментарии для кода, который не возможно понять быстро даже визуальным мышлением. Комментарий прочитать быстрее :)

*C\#*
```csharp
// Processing added or updated libraries
IEnumerable<ILibrary> addedLibraries = state
    .Libraries
    .Where(libraryKeyValuePair =>
        {
            ILibrary existingLibrary = _libraries
                .GetValueOrDefault(libraryKeyValuePair.Key);

            // The library is added
            return existingLibrary == null
                // Library has been changed
                || !ReferenceEquals(libraryKeyValuePair.Value, existingLibrary);
        })
    .Select(libraryKeyValuePair => libraryKeyValuePair.Value);
```

Здесь пример как из примера выше сделать хуже - нужно использовать var. **Настоятельно рекомендую** в любом языке использовать явные объявления всего что только можно. Это позволит вам понимать с чем вы имеете дело без использования значительного количества логического мышления.

Мне могут возразить, что редакторы подсвечивают типы. Те, кто так думает, наведитесь мышкой на пример ниже, считайте что это запрос на слияние, и задумайтесь много ли вам браузер подсветил. И на сколько больше времени вы потратили на наведение, чем просто на прочтение.

*C\#*
```csharp
// Processing added or updated libraries
var addedLibraries = state
    .Libraries
    .Where(libraryKeyValuePair =>
        {
            ILibrary existingLibrary = _libraries
                .GetValueOrDefault(libraryKeyValuePair.Key);

            // The library is added
            return existingLibrary == null
                // Library has been changed
                || !ReferenceEquals(libraryKeyValuePair.Value, existingLibrary);
        })
    .Select(libraryKeyValuePair => libraryKeyValuePair.Value);
```

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

*SQL*
```sql
select
    t1.*,
    t2.Id
from Table1 t1
    inner join Table2 t2
        on t1.Id == t2.Table1Id
where t1.Filter like '%empty%'
    and t2.Filter like '%non-empty%'
order by t2.Name

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