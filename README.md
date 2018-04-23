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

Taking in account that you or your colleagues can use something with two panels for different purposes we have to choose line length which allows to see full line in both panels. The best place to check this is two panel comparison on GitHub when pull request is reviewed. I experimentally found out that 120 symbol line length is optimal for Full HD monitors:
1. Usually you see all text in both panels
2. Usually you see all text in both panels even if you colleague has poor eyesight and enlarged font size
3. You have small buffer to add a few more symbols above 120 limit if you do not have possibility to put something on new line.

If your team has different monitor sizes or different screen resolutions you can determine your own limit using two panels editor or GitHub pull request.

Summarizing all mentioned above **by default** it is optimal to limit line length by **120** symbols.

# Writability and as result readability

Code writing is something what readability depends on. First of all I would like to continue the topic about how usual man reads text. In case of code it is from left to right top down. Mans brain usually optimizes reading by mechanism that some scientists call Visual Thinking. The essence of it is about the following when our brain process information from eyes it makes assumptions about content basing on often seen staff and its visual characteristics. It could be said that brain uses some kind of hash in key-value store for quick access to result. If a brain does not have associated result or result looks weird or invalid to our brain then Logical Thinking mechanism is run. Logical thinking is a complete analysis of available information (full understanding of a code in our case).

Example of such brain's behavior can be found in the Internet. There is an experiment when some color is written down, red for example, but font color for this text is blue. At first step our brain sees blue color + "red" text and assumes that result is blue but after that validation fails and brain runs Logical Thinking blue color + "red" text == ~~blue~~ red - precise result is red. The main issue with Logical Thinking mechanism that it is much slower than Visual Thinking.

**Conclusion**: it is worth to write code in a way when Visual Thinking is used as often as possible.

How?

Brain uses Visual Thinking as primary instrument if:
1. Size of a text differs
2. There is some proximity between text elements
3. Text is aligned

We can achieve the first one by using symbols' case like below:
```csharp
public const string SOME_SHOUTY_CONSTANT = "My const";
```

We can achive the second one by grouping code in logic blocks like following:

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

## Alignment (third point)

Examples above also contain alignment.

If speak short then to use alignment New Line + Indent should be used. That means Enter and Tab. Tab can be set up to tabulation, 2, 4 or N spaces. I **strongly recommend** to use spaces because you always will be precise in your formatting and do not depend on editor. For example it is important for GitHub pull request.

**Strong recommendation**: group and align your blocks by New Line. If some block refers to previous line add one Indent to it.

**Justification:**

The goals is allow to brain to use Visual Thinking.
So why only New Lines and Indents? If you check my second initial recommendation - the code should be easily modifiable and supportable. Often developers like to align code in following way:

```Java
int doNotFormat = likeThis(someArgumentOrExpression,
                           anotherArgumentOrExpression);
```

From one point of view the brain will use Visual Thinking and it is true but from other point of view supportability is broken. For example we used refactoring and renamed function. After that alignment and as result Visual Thinking is broken.

**Conclusion**: code has to be sustainable to changes. It is much better to write:

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

Personally I recommend the last one because it has more explicit parameters block, adding or swapping parameters is easier.

Why following is bad:

```Java
int insteadFormat = somethingLikeThis(someArgumentOrExpression,
    anotherArgumentOrExpression);
```

It is worth to mention that well readable code is often such because of good-named functions, methods and variables (self-descriptive code). If you decide to improve readability and renamed something you can get following:

```Java
int longNameBecauseINeedItForBetterReadability = somethingLongNamedFunctionForBetterReadability(someArgumentOrExpression,
    anotherArgumentOrExpression);
```

As you see in this case parameters are separated. Someone renamed function in other place bad readability is broken here. So example above is not sustainable.

# Summary

**What we do:**
- Consider Readability > Writability > Visual Style
- Consider Visual Thinking > Logical thinking. For that use:
    - Line limit <= 120 (by default)
    - Group logic blocks by adding New Lines between
    - Use alignment by New Line and Indent
    - Keep in mind code has to be sustainable

**How we do:**
- Use Enter for New Line
- Use Tab for indention

As simple as possible!

**What we get for it:**
- Really quick reading from left to right top down with using only vertical scroll
- Our brains processes only really important part and does not check unimportant by filtering them out all by using Visual Thinking. As result your productivity and performance is improved as well as productivity of your team
- Code modifications do not require addition efforts
- Code looks at least good and has one style.

# More to read about?

> To answer the question "What is clean design?" most succinctly: a clean design is one that supports visual thinking so people can meet their informational needs with a minimum of conscious effort.
*Daniel Higginbotham*
*"Clean Up Your Mess — A Guide to Visual Design for Everyone"*
[Site](http://www.visualmess.com/)

[Kevlin Henney - Seven Ineffective Coding Habits of Many Programmers](https://vimeo.com/97329157)

# Examples

I **strongly recommed** all expression blocks **always** wrap out with bracers or other ways of explicit block declarations like below:

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

Also **never** never write different logical parts in one line like below:

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

Much better:

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

    if (!localVariable.IsSomething())
    {
        return
    }

    if (localVariable.IsSomething(
        thirdArgument,
        SOME_SHOUTY_CONSTANT))
    {
        doSomethingWith(localVariable);
    }

    return localVariable.getSomething();
}
```

Here one more practise I **recommend** If you have really long condition in if-statement then consider to extract it to local variable with meaningful name.

*JavaScript*
```javascript
function arbitraryMethodName(
    firstArgument,
    secondArgument,
    thirdArgument
) {
    doSomethingWith(localVariable);

    var isSomething = method(
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

Example of style together with chaining. The same principal can be used for string concatenation by `+`

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

Following example shows **recommendation** for lambda function formatting. Also I **recommend** to write comments for code that is impossible to quicly understand. It is much fater to read comment.

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

Following example shows how to make much worse - just use a bit of implicitness by introducing var. I **strongly recommend** in any language to use explicit declaration always where it is possible. That will allow to read and understand code much quicker with using much of Logic Thinking.

Usually here Holy War begins. Usual objection is "you can hover your mouse over variable". Consider that you are reading pull request in a browser hover your mouse over variable and think how much information your browser shows. Also how much more time did you spend to hovering mouse over instead of just reading?

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