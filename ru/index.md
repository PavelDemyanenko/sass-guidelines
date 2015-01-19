---
layout: default
---

# Об авторе

Меня зовут [Hugo Giraudel](http://hugogiraudel.com), Я frontend-разработчик из Франции, собираюсь переехать в Германию, в Берлин. Я пишу на Sass больше двух лет и теперь являюсь автором таких Sass-проектов, как [SassDoc](http://sassdoc.com) и [Sass-Compatibility](http://sass-compatibility.github.io).

Я также написал несколько библиотек, в основном ради интереса: [SassyJSON](https://github.com/HugoGiraudel/SassyJSON), [SassyLists](http://sassylists.com), [SassySort](https://github.com/HugoGiraudel/SassySort), [SassyCast](https://github.com/HugoGiraudel/SassyCast), [SassyMatrix](https://github.com/HugoGiraudel/SassyMatrix), [SassyBitwise](https://github.com/HugoGiraudel/SassyBitwise), [SassyIteratorsGenerators](https://github.com/HugoGiraudel/SassyIteratorsGenerators), [SassyLogger](https://github.com/HugoGiraudel/SassyLogger), [SassyStrings](https://github.com/HugoGiraudel/SassyStrings) и [SassyGradients](https://github.com/HugoGiraudel/SassyGradients).

<div class="button-wrapper">
  <a href="https://twitter.com/{{ site.twitter_username }}" target="_blank" class="button">Лови меня в Твиттере</a>
</div>











# Сотрудничество

Руководство Sass – открытый проект, которым я руковожу в свободное время. Излишне говорить, что это довольно большой объем работы, чтобы держать всё задокументированным в последней версии. Знать, что вам понравилось это руководство – уже ценно!

Теперь, если вы чувтствуете, что готовы к сотрудничеству, пожалуйста, знайте, уже будет очень здорово просто твитнуть, рассказав или открыв Pull Request с исправлением ошибок в [репозитории на GitHub](https://github.com/HugoGiraudel/sass-guidelines)!

Прежде, чем мы начнём: если вам понравился этот документ, или он оказался полезен вам или вашей команде, пожалуйста, подумайте о го поддержке!

<div class="button-wrapper">
  <a href="https://gum.co/sass-guildelines" target="_blank" class="button">Поддержите руководство Sass</a>
  {% capture tweet %}{{ site.title }}, {{ site.description }} от @{{ site.twitter_username }} –{% endcapture %}
  <a href="https://twitter.com/share?text={{ tweet | cgi_escape }}&url={{ site.url }}" target="_blank" class="button">Расскажите</a>
</div>











# Содержание

* [Об авторе](#about-the-author)
* [Сотрудничество](#contributing)
* [О Sass](#about-sass)
  * [Ruby Sass или LibSass](#ruby-sass-or-libsass)
  * [Sass или SCSS](#sass-or-scss)
  * [Другие препроцессоры](#other-preprocessors)
* [Введение](#introduction)
  * [Зачем руководство](#why-a-styleguide)
  * [Отказ от ответственности](#disclaimer)
  * [Ключевые принципы](#key-principles)
* [Синтакс и Форматирование](#syntax--formatting)
  * [Строки](#strings)
  * [Числа](#numbers)
    * [Нули](#zeros)
    * [Единицы измерения](#units)
    * [Вычисления](#calculations)
    * [Магические цифры](#magic-numbers)
  * [Цвета](#colors)
    * [Цветовые форматы](#color-formats)
    * [Цвета и переменные](#colors-and-variables)
    * [Освесление и затемнение цветов](#lightening-and-darkening-colors)
  * [Списки](#lists)
  * [Карты](#maps)
    * [Отладка карт Sass](#debugging-a-sass-map)
  * [Набор правил CSS](#css-ruleset)
  * [Объявление сортировки](#declaration-sorting)
  * [Вкладывание селекторов](#selector-nesting)
    * [Общие правила](#general-rule)
    * [Исключения](#exceptions)
* [Соглашения по именованию](#naming-conventions)
  * [Константы](#constants)
  * [Пространство имен](#namespace)
* [Комментирвание](#commenting)
  * [Написание комментариев](#writing-comments)
  * [Документирование](#documentation)
* [Архитектура](#architecture)
  * [Компоненты](#components)
  * [Шаблон 7-1](#the-7-1-pattern)
    * [Основная папка](#base-folder)
    * [Папка компонентов](#components-folder)
    * [Папка лэйаута](#layout-folder)
    * [Папка страниц](#pages-folder)
    * [Папка тем](#themes-folder)
    * [Папка утилит](#utils-folder)
    * [Папка вендоров](#vendors-folder)
    * [Главный файл](#main-file)
  * [Файл позора](#shame-file)
* [Адаптивный веб-дизайн и точки остановки](#responsive-web-design-and-breakpoints)
  * [Именование точек остановки](#naming-breakpoints)
  * [Менеджер точек остановки](#breakpoint-manager)
  * [Использование медиа-запросов](#media-queries-usage)
* [Переменные](#variables)
  * [Контекст](#scoping)
  * [Флаг !default](#default-flag)
  * [Флаг !global](#global-flag)
  * [Много переменных или карты](#multiple-variables-or-maps)
* [Расширение](#extend)
* [Примеси](#mixins)
  * [Основы](#basics)
  * [Список аргументов](#arguments-list)
  * [Примеси и вендорные префиксы](#mixins-and-vendor-prefixes)
* [Условные операторы](#conditional-statements)
* [Циклы](#loops)
  * [Each](#each)
  * [For](#for)
  * [While](#while)
* [Ошибки и предупреждения](#warnings-and-errors)
  * [Предупреждения](#warnings)
  * [Ошибки](#errors)
* [Инструментарий](#tools)
  * [Compass](#compass)
  * [Сетки](#grid-systems)
  * [SCSS-lint](#scss-lint)
* [Слишком длинно; Не читал](#too-long-didnt-read)











# О Sass

Вот так [Sass](http://sass-lang.com) описывает сам себя в своей [документации](http://sass-lang.com/documentation/file.SASS_REFERENCE.html):

> Sass — это расширение CSS, которое добавляет силу и элигантность к основному языку.

Основая цель Sass — это исправить недостатки CSS. CSS, как мы все знаем, не самый лучший язык в мире <sup>[указать источник]</sup>. Являясь довольно простым для освоения, он может быстро стать запутанным, особенно на больших проектах.

Вот в это время и вступает в свою роль Sass как язык мета-программирования, чтобы улучшить CSS синтаксис, для того, чтобы обеспечить дополнительные функции и удобные инструменты.
Между тем, Sass остаётся консервативным в отношении языка CSS.

Цель в том, чтобы не превратить CSS в полнофункциональный язык программирования; Sass только хочет помочь там, где CSS не справляется. Поэтому начать использовать Sass не сложнее, чем начать изучать CSS. Он просто добавляет дополнительные возможности поверх CSS.

Есть много способов использовать эти возможности. Какие-то способы хороши, какие-то – не очень, а некоторые вообще необычные. Это руководство предназначено для того, чтобы дать последовательный и документированый подход для написания Sass.

### Дальнейшее чтение

* [Sass](http://sass-lang.com)
* [Sass documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)






## Ruby Sass или LibSass

[Первый коммит в Sass](https://github.com/hcatlin/sass/commit/fa5048ba405619273e474a50400c7243fbff54fe) был сделан в конце 2006, более 8 лет назад. Излишне говорить, что Sass прошёл долгий путь с тех пор. Изначально разработанный на Ruby, он получил множество портов там и тут. Самый популяный – [LibSass](https://github.com/sass/libsass) (написан на Си), сейчас близок к полной совместимости с изначальным исполнением на Ruby.

В 2014 [команды Ruby Sass и LibSass решили подождать синхронизации версий, прежде чем двигаться дальше](https://github.com/sass/libsass/wiki/The-LibSass-Compatibility-Plan). С тех пор LibSass активно выпускает версии, чтобы иметь контроль над чётностью версий со старшим братом. Последние оставшиеся несоответствия собраны и перечислены мной в проекте [Sass-Compatibility](http://sass-compatibility.github.io). Если вы знаете о несовместимости между этими двумя версиями, которой нет в списке, пожалуйста, создайте соответствующий issue.

Вернёмся к выбору компилятора. На самом деле, всё зависит от вашего проекта. Если это Ruby on Rails, вам лучше использовать Ruby Sass, который идеально подходит для такого случая. Также следует помнить, что Ruby Sass — это всегда эталонная реализация и всегда будет обгонять LibSass.

Не на Ruby-проектах, которые нуждаются в интеграции рабочего процесса, LibSass, вероятно, лучшая идея, поскольку является наиболее популярным. Так что если вы хотите использовать, скажем, NodeJS, [node-sass](https://github.com/sass/node-sass) — ваш выбор.

### Дальнейшее чтение

* [LibSass](https://github.com/sass/libsass)
* [Sass-Compatibility](http://sass-compatibility.github.io)
* [Switching from Ruby Sass to LibSass](http://www.sitepoint.com/switching-ruby-sass-libsass/)






## Sass или SCSS

Существует довольно много путаницы относительно семантики имени *Sass*, и не зря: Sass означает как препроцессор, так и свой собственный синтаксис. Не очень удобно, не так ли?

Как видите, Sass первоначально описал синтаксис, определяющей характеристикой которого является его чувствительность к вложености. Вскоре в Sass решили сократить разрыв между Sass и CSS, обеспечивая дружественный для CSS синтаксис под названием *SCSS* или *Sassy CSS*. Девиз: “если это правильный CSS, то это правильный SCSS”.

С тех пор, Sass (препроцессор) предоставляет два различных синтаксиса: Sass (не все буквы заглавные, [пожалуйста](http://sassnotsass.com)), также известный как *синтаксис с отступом,* и SCSS. Какой из них использовать в значительной степени, зависит от вас, так как оба строго равны по возможностям. Это только вопрос эстетики.

Cинтаксис Sass опирается на отступы, чтобы избавиться от скобок, точки с запятой и других символов пунктуации, что приводит к более компактному и более короткому синтаксису. Между тем, SCSS легче учиться, так как это в основном крошечные дополнительные кусочки на вершине CSS.

Лично я предпочитаю SCSS вместо Sass, потому что он близок к CSS и более дружелюбен для большинства разработчиков. Поэтому я буду использовать SCSS в этом руководстве.



### Дальнейшее чтение

* [What's the difference between Sass and SCSS](http://www.sitepoint.com/whats-difference-sass-scss/)






## Другие препроцессоры

Sass — это препроцессор, коих много. Самый серьёзный соперник — это [LESS](http://lesscss.org/), основанный на NodeJS, который стал весьма популярен благодаря CSS-фреймворку [Bootstrap](http://getbootstrap.com/). Также есть [Stylus](http://learnboost.github.io/stylus/), который позволяет делать очень многое, так как почти превращает CSS в язык программирования.

*Почему выбирать Sass, а не другой препроцессор?* Это всё еще действующий вопрос сегодня. Не так давно мы рекомендовали использовать Sass для проектов на Ruby, потому что Sass был создан в Ruby и хорошо работает с Ruby On Rails. Теперь, когда LibSass догнал (в основном) оригинальный Sass, это уже не актуальный совет.

То, что мне нравится в Sass, так это его консервативный подход к CSS. Дизайн Sass основан на строгих принципах: большая часть проектного подхода приходит из мнений команды, о том что что: а) добавление возможностей имеет стоимость сложности, которая должна быть оправдана полезностью, и б) должно быть легко понять, что делает определённый блок стилей, глядя только на него. Кроме того, Sass имеет гораздо более четкое внимание к деталям, чем другие препроцессоры. Насколько я могу судить, основные разработчики очень заботятся о поддержке совместимости с CSS, и любое общее поведение является последовательным.

Другими словами, Sass – не препроцессор, который направлен на удовлетворение гиковатых программистов вроде меня, добавляя в язык возможности, которые не предназначены для поддержки любых логических сценариев использования. Это программное обеспечение, направленое на решение действительных вопросов; он помогает обеспечить полезные возможности CSS, где CSS не дотягивает.

Препроцессоры в сторону, мы должны также упомянуть постпроцессоры, которые получили значительные дозы внимания в течение последних нескольких месяцев, главным образом благодаря [PostCSS](https://github.com/postcss/postcss) и [cssnext](HTTPS://cssnext.github.io/). Постпроцессоры довольно во многом похожи на препроцессоры, кроме того что они не обеспечивают ничего, кроме синтаксиса CSS.

Вы можете думать о постпроцессорах как о поли-заполнителе для неподдерживаемых возможностей CSS. Например, можно было бы написать переменные, как они описаны в [спецификации CSS](http://dev.w3.org/csswg/css-variables/), затем скомпилировать таблицы стилей с постпроцессором – только чтобы найти каждую переменную и заменить на соотвествующее значение, как Sass и сделал бы.

Идея постпроцессоров в том, что как только браузеры поддерживают новые возможности (например, переменные CSS), постпроцессор больше не компилирует их, позволяя браузерам взять это на себя.

Предоставление синтаксиса завтрашнего дня является благородной идеей; я должен сказать, что я по-прежнему предпочитаю использовать Sass для большинства задач. Тем не менее, есть некоторые случаи, когда я считаю, что постпроцессоры подходят больше, чем Sass – например, для вендорных префиксов CSS – но мы к этому ещё вернёмся.


### Дальнейшее чтение

* [LESS](http://lesscss.org/)
* [Stylus](http://learnboost.github.io/stylus/)
* [cssnext](https://cssnext.github.io/)
* [PostCSS](https://github.com/postcss/postcss)











# Введение





## Зачем руководство

Руководство по стилям – это не просто приятный документ для чтения, рисующий ваш код идеальным. Это ключевой документ в жизни проекта, рассказывающий, как и почему код должен быть написан. Это может выглядеть как перебор для небольших проектов, но это очень помогает сохранять кодовую базу чистой, масштабируемой и лёгкой в обслуживании.

Излишне говорить, что чем больше разработчиков, участвующих в проекте, тем больше руководств требуется. Так же, чем больше проект, тем больше руководство по стилям, и это обязательно.

[Гарри Робертс](http://csswizardry.com) очень хорошо об этом говорит в [CSS Guidelines](http://cssguidelin.es/#the-importance-of-a-styleguide):

<blockquote>
  <p>Руководство по написанию стилей (заметьте, не визуальное) является ценным инструментом для команд, которые:</p>
  <ul>
    <li>создают и поддерживают продукты в разумные сроки;</li>
    <li>имеют ряд разработчиков, различающихся способностями и специальностями;</li>
    <li>имеют ряд различных разработчиков, работающих на продуктом в любой момент времени;</li>
    <li>имеют постоянную текучку кадров;</li>
    <li>имеют много разного кода, в который разработчики погружаются.</li>
  </ul>
</blockquote>






## Отказ от ответственности

Во-первых: **это не руководство по CSS**. Этот документ не будет обсуждать именования классов CSS, модульные шаблоны и вопрос об ID в мире CSS. Это руководство направлено только на работу с Sass.

Кроме того, это мое личное руководство стилей и поэтому **очень субъективное**. Думайте об этом, как о совокупности методологий и советов, которые я улучшал на протяжении многих лет. Это также даёт мне возможность расставить ссылки на полезные и вдохновляющие ресурсы, так что не забудьте проверять разделы *Дальнейшего чтения*.

Очевидно, что это, конечно, не единственный способ делать вещи, и это может или не может удовлетворить ваш проект. Не стесняйтесь брать отсюда код и подстраивать его под свои нужды. Как говорят у нас, *ваш пробег может отличаться* (в том смысле, что в вашей ситуации может быть по-другому).






## Ключевые принципы

В конце концов, есть одна вещь, которую я хочу донести вам в этом руководстве – **Sass должен быть предельно прост, насколько это возможно**.

Спасибо моим глупым эскпирементам, таким как [битовы операции](https://github.com/HugoGiraudel/SassyBitwise), [итераторы и генераторы](https://github.com/HugoGiraudel/SassyIteratorsGenerators) и [парсер JSON](https://github.com/HugoGiraudel/SassyJSON) на Sass, и теперь мы все хорошо знаем, что можно сделать с этим препроцессором.

Между тем, CSS является простым языком. Sass, предназначенный, чтобы написать CSS, не должен получаться гораздо сложнее, чем обычный CSS. [Принцип KISS](https://ru.wikipedia.org/wiki/KISS_(принцип)) (**K**eep **I**t **S**imple **S**tupid, делай это проще, тупица) является ключевым моментом здесь и может даже взять верх над [принципом DRY](https://ru.wikipedia.org/wiki/Don’t_repeat_yourself) (**D**on't **R**epeat **Y**ourself, не повторяйся) в некоторых случаях.

Иногда лучше повторяться немного, чтобы держать код понятным, а не строить тяжелую, громоздкую, сложную систему, которая полностью нечитаема и сложна в поддержке.

Кроме того, и позвольте мне процитировать [Гарри Робертса](https://csswizardry.com) еще раз, **прагматизм – козырь совершенства**. В какой-то момент, вы, вероятно, пойдёте против правил, описанных здесь. Если это имеет смысл — сделайте это. Код – просто средство, а не цель.



### Дальнейшее чтение

* [KISS principle](http://en.wikipedia.org/wiki/KISS_principle)
* [DRY principle](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
* [Keep Sass Simple](http://www.sitepoint.com/keep-sass-simple/)











# Синтаксис и форматирование

Если вы спросите меня, что таблица стилей должна делать в первую очередь – так это показать, как мы хотим наш код преподнести.

Когда несколько разработчиков участвуют в написании CSS проекта(ов), то это только вопрос времени, прежде чем один из них начинает делать вещи по-своему. Руководство стилей способствуют не только в согласованости, но и помогает, когда приходит время читать и обновлять код.

Грубо говоря, мы хотим (бесстыдно вдохновлён [CSS Guidelines](http://cssguidelin.es/#syntax-and-formatting)):

* двойные (2) отступы пробелом, никаких табов;
* в идеале, 80-символьную ширину линий;
* правильно написанные многострочные CSS правила;
* осмысленное использование пробелов.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  display: block;
  overflow: hidden;
  padding: 0 1em;
}

// Nope
.foo {
    display: block; overflow: hidden;

    padding: 0 1em;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Так как Sass-синтаксис заставляет использовать эти стандарты написания
// Не будет способа неправльного подхода к написанию
.foo
  display: block
  overflow: hidden
  padding: 0 1em
{% endhighlight %}
  </div>
</div>

Мы не будем решать вопрос организации файлов в этом разделе. Это объект архитектуры [другого раздела](#architecture).






## Строки

CSS не требует, чтобы строки были помещены в кавычки, даже те, что содержат пробелы. Возьмите названия семейства шрифтов, например: не имеет значения, оборачиваете ли вы их в кавычки для CSS-парсера или нет.

Из-за этого, Sass *также* не требует помещения строк в кавычки. Даже лучше (и, *к счастью,* вы согласитесь), строка в кавычках является точным соответствием её двойника без кавычек (например, строка `'abc'` строго равна `abc`).

Языки, которые не требуют, чтобы строки были в кавычках, определенно, в меньшинстве, так что **строки должны всегда быть обёрнуты в одинарные кавычки** в Sass (одну проще набрать, чем двойную, на *QWERTY*-клавиатуре). Кроме того, для согласованности с другими языками, в том числе с двоюродным братом CSS – JavaScript'ом, есть несколько причин для такого выбора:

* названия цветов рассматриваются как цвета, когда без кавычек, что может привести к серьёзным проблемам;
* большинство синтаксических анализаторов будут в шоке от строк без кавычек;
* это помогает общей читаемости;
* нет правильной причины не обворачивать строки в ковычки.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$font-stack: 'Helvetica Neue Light', 'Helvetica', 'Arial', sans-serif;

// Nope
$font-stack: "Helvetica Neue Light", "Helvetica", "Arial", sans-serif;

// Nope
$font-stack: Helvetica Neue Light, Helvetica, Arial, sans-serif;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$font-stack: 'Helvetica Neue Light', 'Helvetica', 'Arial', sans-serif

// Nope
$font-stack: "Helvetica Neue Light", "Helvetica", "Arial", sans-serif

// Nope
$font-stack: Helvetica Neue Light, Helvetica, Arial, sans-serif
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p>В предыдущем примере, <code>sans-serif</code> не был обёрнут в кавычки, потому что это специальное значение CSS, которые должно быть без кавычек.</p>
</div>

URL тоже дожны быть в кавычках, по тем же причинам, что и выше:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  background-image: url('/images/kittens.jpg');
}

// Nope
.foo {
  background-image: url(/images/kittens.jpg);
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo
  background-image: url('/images/kittens.jpg')

// Nope
.foo
  background-image: url(/images/kittens.jpg)
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [All You Ever Need to Know About Sass Interpolation](http://webdesign.tutsplus.com/tutorials/all-you-ever-need-to-know-about-sass-interpolation--cms-21375)
* [SassyStrings](https://github.com/HugoGiraudel/SassyStrings)






## Числа

В Sass, число это тип данных, включая все, от безразмерных чисел до длин, длительности, частоты, углов и так далее. Это позволяет проводить на них расчеты.



### Нули

Числа должны отображать нули перед десятичным значением меньше единицы. Никогда не отображайте без нулей.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  padding: 2em;
  opacity: 0.5;
}

// Nope
.foo {
  padding: 2.0em;
  opacity: .5;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo
  padding: 2em
  opacity: 0.5

// Nope
.foo
  padding: 2.0em
  opacity: .5
{% endhighlight %}
  </div>
</div>



### Единицы измерения

При работе с длинами, '0' значение никогда не должны иметь единицу измерения.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$length: 0;

// Nope
$length: 0em;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$length: 0

// Nope
$length: 0em
{% endhighlight %}
  </div>
</div>

Самая распространенная ошибка о числах в Sass, думает, это что единицы лишь некоторые строки, которые можно безопасно прилагать к числу. Хотя это и звучит как правда, это, конечно, не так, как единицы работают. Думайте о единицах, в контексте алгебраических символов. Например, в реальном мире, умножая 5 дюймов на 5 дюймов дает вам 25 квадратных дюймов.Та же логика применима к Sass.

Чтобы добавить единицу измерения в число, нужно умножить это число на * 1 единицу измерения *.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$value: 42;

// Yep
$length: $value * 1px;

// Nope
$length: $value + px;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$value: 42

// Yep
$length: $value * 1px

// Nope
$length: $value + px
{% endhighlight %}
  </div>
</div>

Заметим, что добавление *0 это единицы измерения* также работает, но я скорее бы порекомендовал вышеупомянутый метод, так как добавление *0 единицу измерения* может быть немного запутанным. Действительно, при попытке преобразовать число в другую единицу измерения, добавление 0 не будет делать трюк.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$value: 42 + 0px;
// -> 42px

$value: 1in + 0px;
// -> 1in

$value: 0px + 1in;
// -> 96px
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$value: 42 + 0px
// -> 42px

$value: 1in + 0px
// -> 1in

$value: 0px + 1in
// -> 96px
{% endhighlight %}
  </div>
</div>

В конце концов, это действительно зависит от того, чего вы пытаетесь достичь. Просто имейте в виду, что добавление единицы измерения как строки не хороший способ.

Для единицы измерения из значения, вы должны разделить его на *одну единицу этой же меры*.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$length: 42px;

// Yep
$value: $length / 1px;

// Nope
$value: str-slice($length + unquote(''), 1, 2);
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$length: 42px

// Yep
$value: $length / 1px

// Nope
$value: str-slice($length + unquote(''), 1, 2)
{% endhighlight %}
  </div>
</div>

Добавляя единицу измерения как строку в число превращает все в строку, предотвращая любую дополнительную операцию. Разделение числа и единицы измерения тоже приводит к строке. Это не то, что вы хотите.



### Вычисления

**Числовые расчеты должны всегда быть в скобках **. Мало того, что это требование значительно улучшает читаемость, оно также предотвращает некоторые крайние случаи, заставляя Sass оценивать содержимое скобок.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  width: (100% / 3);
}

// Nope
.foo {
  width: 100% / 3;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo
  width: (100% / 3)

// Nope
.foo
  width: 100% / 3
{% endhighlight %}
  </div>
</div>



### Магические числа

"Магическое число" - это [олдскульный термин программирования](http://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants) для *неименованнах числовых констант*. В принципе, это просто случайное число, которое *просто работает*™ и еще не привязанное к какому-либо логическому объяснению.

Излишне говорить **магические числа — чума и их следует избегать любой ценой**. Если вы не можете найти разумное объяснение тому, почему число работает, добавьте обширный комментарий, объясняющий, как вы туда попали и почему вы думаете, что это работает. Признавая, что вы не знаете, почему что-то работает будет еще более полезным для следующего разработчика, чем их исследования, что происходит на пустом месте.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/**
 * 1. Магическое число. Это минимальное число, которое я смог найти, что выровнять верх
 * `.foo` с его предком. Идеально, мы должны починить это правилньно.
 */
.foo {
  top: 0.327em; /* 1 */
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/**
 * 1. Магическое число. Это минимальное число, которое я смог найти, что выровнять верх
 * `.foo` с его предком. Идеально, мы должны починить это правилньно.
 */
.foo
  top: 0.327em /* 1 */
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Use Lengths, Not Strings](http://hugogiraudel.com/2013/09/03/use-lengths-not-strings/)
* [Correctly Adding Unit to Number](http://css-tricks.com/snippets/sass/correctly-adding-unit-number/)
* [Magic Numbers in CSS](http://css-tricks.com/magic-numbers-in-css/)
* [Sassy-Math](https://github.com/at-import/sassy-math)






## Цвета

Цвета занимают важное место в языке CSS. Естественно, Sass является ценным союзником, когда дело доходит до манипулирования цветами, в основном путем предоставления [мощных функций](http://sass-lang.com/documentation/Sass/Script/Functions.html).



### Цветовые форматы

Для того, чтобы сделать цвета просто, как только возможно, мой совет будет в соблюдение следующего порядка в предпочтение цветных форматов:

1. [CSS ключеые слова](http://www.w3.org/TR/css3-color/#svg-color);
1. [HSL нотация](http://en.wikipedia.org/wiki/HSL_and_HSV);
1. [RGB нотация](http://en.wikipedia.org/wiki/RGB_color_model);
1. Шестнадцатеричная нотация. Предпочтительно в нижнем ригистре и укороченная по возможности.

Во-первых, ключевые слова часто говорят сами за себя. Представление HSL не только самое простое для человеческого мозга, чтобы понять, <SUP> [править] </ SUP>, это также делает его легким для настроики цвета путем регулировки цветового тона, насыщенности и яркости индивидуально. RGB-прежнему имеет преимущество, показывая прямо сейчас, если цвет более синий, зеленый или красный, но это не делает его легким в построение цвета из трех частей. Наконец, шестнадцатеричное представление близко сложно к расшифроке человеческого ума.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  color: red;
}

// Nope
.foo {
  color: #FF0000;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo
  color: red

// Nope
.foo
  color: #FF0000
{% endhighlight %}
  </div>
</div>

При использовании HSL или обозначения RGB, всегда добавляйте один пробел после запятой (`,`) и без пробела между скобками ((`, `)`) и содержанию.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo {
  color: rgba(0, 0, 0, 0.1);
  background: hsl(300, 100%, 100%);
}

// Nope
.foo {
  color: rgba(0,0,0,0.1);
  background: hsl( 300, 100%, 100% );
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo
  color: rgba(0, 0, 0, 0.1)
  background: hsl(300, 100%, 100%)

// Nope
.foo
  color: rgba(0,0,0,0.1)
  background: hsl( 300, 100%, 100% )
{% endhighlight %}
  </div>
</div>



### Цвета и переменные

При использовании цвета более чем одного раза, сохраняйтк его в переменной с многозначительным названием, представляющим цвет.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$sass-pink: #c69;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$sass-pink: #c69
{% endhighlight %}
  </div>
</div>

Теперь вы можете использовать эту переменную, когда вы захотите. Однако, если ваш использование сильно привязаны к теме, я бы не советовал переменные. Вместо этого, храните его в другой переменной с именем, объясняя, как она должна быть использована.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$main-theme-color: $sass-pink;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$main-theme-color: $sass-pink
{% endhighlight %}
  </div>
</div>

Это будет препятствовать смене темы, ведущую к чему-то вроде `$sass-pink:: blue`.

{% include donate.html %}



### Осветление и затемнение цветов



И [`осветление`](http://sass-lang.com/documentation/Sass/Script/Functions.html#lighten-instance_method) и [`затемнение`](http://sass-lang.com/documentation/Sass/Script/functions.html#darken-instance_method) — функции манипулирования цвета HSL пространства, добавляя или вычитая в HSL пространстве. В принципе, они не что иное, как алиасы для `$lightness` параметра [`adjust-color`](http://sass-lang.com/documentation/Sass/Script/Functions.html#adjust_color-instance_method) функции.

Дело в том, эта функция часто не дает ожидаемого результата. С другой стороны, функция [`mix`](http://sass-lang.com/documentation/Sass/Script/Functions.html#mix-instance_method) является хорошим способом осветлить или затемнить цвет, смешивая его либо `white` или` black`.

Преимущество использования `mix`, а не одним из двух указанных функций является то, что она будет постепенно меняться на черный (или белый), когда вы уменьшаете долю цвета, в то время как` darken` и `lighten` быстро меняют цвет с черного и белого.

<figure role="group">
  <img src="/assets/images/lighten-darken-mix.png" alt="Иллюстрация разницы между освтлением/затемнением и mix функции Sass" />
  <figcaption>Иллюстрация разницы между <code>lighten</code>/<code>darken</code> и <code>mix</code>функции Sass от <a href="http://codepen.io/KatieK2/pen/tejhz/" target="_blank">KatieK</a></figcaption>
</figure>

Если вы не хотите, чтобы писать `mix` функцию каждый раз, вы можете создать две простых в использовании функций `tint` и `shade` (которые также являются частью [Compass](HTTP://compass- style.org/reference/compass/helpers/colors/#shade)), чтобы сделать то же самое:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Немного осветлить цвет
/// @access public
/// @param {Color} $color - цвет для осветления
/// @param {Number} $percentage - процент `$color` в возвращаемом цвете
/// @return {Color}
@function tint($color, $percentage) {
  @return mix($color, white, $percentage);
}

/// Немного затемнить цвет
/// @access public
/// @param {Color} $color - цвет для затемнения
/// @param {Number} $percentage - процент `$color` в возвращаемом цвете
/// @return {Color}
@function shade($color, $percentage) {
  @return mix($color, black, $percentage);
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Немного осветлить цвет
/// @access public
/// @param {Color} $color - цвет для осветления
/// @param {Number} $percentage - процент `$color` в возвращаемом цвете
/// @return {Color}
@function tint($color, $percentage)
  @return mix($color, white, $percentage)

/// Немного затемнить цвет
/// @access public
/// @param {Color} $color - цвет для затемнения
/// @param {Number} $percentage - процент `$color` в возвращаемом цвете
/// @return {Color}
@function shade($color, $percentage)
  @return mix($color, black, $percentage)
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p><a href="http://sass-lang.com/documentation/Sass/Script/Functions.html#scale_color-instance_method"><code>scale-color</code></a> функция разработана, чтобы изменять свойства более плавно, принимая во внимание насколько они уже изменениы. Результат так же хорош, как и от <code>mix</code>, но с более удобной конвенцией вызова. Хотя, коэффициент масштабирования не совсем то же самое.</p>
</div>



### Дальнейшее чтение

* [A Visual Guide to Sass & Compass Color Functions](http://jackiebalzer.com/color)
* [How to Programmatically Go From One Color to Another](http://thesassway.com/advanced/how-to-programtically-go-from-one-color-to-another-in-sass)
* [Sass Color Variables That Don't Suck](http://davidwalsh.name/sass-color-variables-dont-suck)
* [Using Sass to Build Color Palettes](http://www.sitepoint.com/using-sass-build-color-palettes/)
* [Dealing with Color Schemes in Sass](http://www.sitepoint.com/dealing-color-schemes-sass/)






## Листы

Списки Sass эквиваленты массивам.Список представляет собой плоскую структуру данных (в отличие от [карт кода](#maps)) предназначенную для хранения значения любого типа (в том числе списков со вложенными списками).

Списки должны соблюдать следующие правила:

* если не слишком длинный и помещается на 80-символьную строку, всегда отображать его на одной линии;
* если не используется для целей CSS, всегда пользуйтесь запятой в качестве разделителя;
* если не пустой или вложен в другой список, никогда не пишите скобки;
* никогда не добавляйте точку с запятой.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$font-stack: 'Helvetica', 'Arial', sans-serif;

// Nope
$font-stack:
  'Helvetica',
  'Arial',
  sans-serif;

// Nope
$font-stack: 'Helvetica' 'Arial' sans-serif;

// Nope
$font-stack: ('Helvetica', 'Arial', sans-serif);

// Nope
$font-stack: ('Helvetica', 'Arial', sans-serif,);
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$font-stack: 'Helvetica', 'Arial', sans-serif

// Nope (since it is not supported)
$font-stack:
  'Helvetica',
  'Arial',
  sans-serif

// Nope
$font-stack: 'Helvetica' 'Arial' sans-serif

// Nope
$font-stack: ('Helvetica', 'Arial', sans-serif)

// Nope
$font-stack: ('Helvetica', 'Arial', sans-serif,)
{% endhighlight %}
  </div>
</div>

При добавлении новых записей в список, всегда используйте прилагаемый API. Не пытайтесь добавлять новые элементы вручную.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$shadows: 0 42px 13.37px hotpink;

// Yep
$shadows: append($shadows, $shadow, comma);

// Nope
$shadows: $shadows, $shadow;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$shadows: 0 42px 13.37px hotpink

// Yep
$shadows: append($shadows, $shadow, comma)

// Nope
$shadows: $shadows, $shadow
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [SassyLists](http://sassylists.com)






## Карты кода

Начиная с Sass 3.3, авторы таблиц стилей могут определить карты коды, которые являются термином Sass для ассоциативных массивов, хэшей или даже JavaScript объектов. Карта кода является структура данных ключи-отображения (это может быть любой тип данных, включая карты коды, хотя я бы не рекомендовал его) для значений любого типа.

Карты коды должны быть записаны следующим образом:

* пробел после двоеточия (`:`);
* открывающая скобка (`(`) на той же линии, что и двоеточие (`:`);
* **ключи в ковычках**, если они строки (в 99% случаев);
* каждая key/value пара на новой линии;
* запятая (`,`) на конце каждой пары key/value;
* **точка с запятой** (`,`) на последней паре, что было легче добавлять, удалять или переставлять пункты;
* закрывающая скобка (`)`) на своей новой линии;
* без пробела или новой лини между закрывающей скобкой (`)`) и точкой с запятой (`;`).

Иллюстрация:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$breakpoints: (
  'small': 767px,
  'medium': 992px,
  'large': 1200px,
);

// Nope
$breakpoints: ( small: 767px, medium: 992px, large: 1200px );
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$breakpoints: ('small': 767px, 'medium': 992px, 'large': 1200px,)

// Nope
$breakpoints: ( 'small': 767px, 'medium': 992px, 'large': 1200px )

// Nope
$breakpoints: (small: 767px, medium: 992px, large: 1200px,)

// Nope (since it is not supported)
$breakpoints: (
  'small': 767px,
  'medium': 992px,
  'large': 1200px,
)
{% endhighlight %}
  </div>
</div>



### Отладка Sass карт кода

Если вы когда-нибудь потерялись, не понимая что за сумасшедшия магия происходит в карте кода Sass, не волнуйтесь, потому что есть еще способ, чтобы спастись.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@mixin debug-map($map) {
  @at-root {
    @debug-map {
      __toString__: inspect($map);
      __length__: length($map);
      __depth__: if(function-exists('map-depth'), map-depth($map), null);
      __keys__: map-keys($map);
      __properties__ {
        @each $key, $value in $map {
          #{'(' + type-of($value) + ') ' + $key}: inspect($value);
        }
      }
    }
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
=debug-map($map)
  @at-root
    @debug-map
      __toString__: inspect($map)
      __length__: length($map)
      __depth__: if(function-exists('map-depth'), map-depth($map), null)
      __keys__: map-keys($map)
      __properties__
        @each $key, $value in $map
          #{'(' + type-of($value) + ') ' + $key}: inspect($value)
{% endhighlight %}
  </div>
</div>

Если вы заинтересованы в глубине карты кода, добавьте следующую функцию. Примесь будет отображать её автоматически.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Вычислить максимальную глубину карты
/// @param {Map} $map
/// @return {Number} max depth of `$map`
@function map-depth($map) {
  $level: 1;

  @each $key, $value in $map {
    @if type-of($value) == 'map' {
      $level: max(map-depth($value) + 1, $level);
    }
  }

  @return $level;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Вычислить максимальную глубину карты
/// @param {Map} $map
/// @return {Number} max depth of `$map`
@function map-depth($map)
  $level: 1

  @each $key, $value in $map
    @if type-of($value) == 'map'
      $level: max(map-depth($value) + 1, $level)

  @return $level;
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Using Sass Maps](http://www.sitepoint.com/using-sass-maps/)
* [Debugging Sass Maps](http://www.sitepoint.com/debugging-sass-maps/)
* [Real Sass, Real Maps](http://blog.grayghostvisuals.com/sass/real-sass-real-maps/)
* [Sass Maps are Awesome](http://viget.com/extend/sass-maps-are-awesome)
* [Sass list-maps](https://github.com/lunelson/sass-list-maps)
* [Sass Maps Plus](https://github.com/lunelson/sass-maps-plus)
* [Sassy-Maps](https://github.com/at-import/sassy-maps)
* [Introduction to Sass Maps Usage and Examples](http://webdesign.tutsplus.com/tutorials/an-introduction-to-sass-maps-usage-and-examples--cms-22184)






## Набор правил CSS

На данный момент, это, в основном, пересмотр того, что все знает, но вот как набор правил CSS  должен быть написан (по крайней мере, по мнению большинства руководств, в том числе [CSS Руководства](http://cssguidelin.es/#anatomy-of--набор правил)):

* связанные селекторы на одной строке; не связанные селекторы на новой линии;
* открывающая скобка (`{`) отделяется от последнего селектора одним пробелом;
* каждое объявление на собственной новой линии;
* пробел после двоеточия (`:`);
* завершающая точка с запятой (`;`) в конце всех деклараций;
* закрывающая скобка (`}`) на своей новой линии;
* новая линия после закрывающей скобки `}`.

Иллюстрация:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
.foo, .foo-bar,
.baz {
  display: block;
  overflow: hidden;
  margin: 0 auto;
}

// Nope
.foo,
.foo-bar, .baz {
    display: block;
    overflow: hidden;
    margin: 0 auto }
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
.foo, .foo-bar,
.baz
  display: block
  overflow: hidden
  margin: 0 auto

// Nope
.foo,
.foo-bar, .baz
    display: block
    overflow: hidden
    margin: 0 auto
{% endhighlight %}
  </div>
</div>

Добавляя эти принципы CSS, мы хотим обратить внимание на:

* локальные переменные объявляются перед объявлениями, потом отделены от деклараций новой линии;
* вызовы миксинов с `@content` перед декларациец;
* вложенные селекторы всегда идут после новой линии;
* вызовы миксинов с `@content` идут после вложенных селекторов;
* без новых строк перед закрывающей фигурной скобкой (`}`).

Иллюстрация:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo, .foo-bar,
.baz {
  $length: 42em;

  @include ellipsis;
  @include size($length);
  display: block;
  overflow: hidden;
  margin: 0 auto;

  &:hover {
    color: red;
  }

  @include respond-to('small') {
    overflow: visible;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo, .foo-bar,
.baz
  $length: 42em

  +ellipsis
  +size($length)
  display: block
  overflow: hidden
  margin: 0 auto

  &:hover
    color: red

  +respond-to('small')
    overflow: visible
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Anatomy of a Ruleset](http://cssguidelin.es/#anatomy-of-a-ruleset)






## Декларация сортировки

Я не знаю много темах, где мнения разделенны, о том как они расценивают декларацию сортировки в CSS. Конкретно, существуют две фракции здесь:

* придерживаться алфавитного порядка;
* декларация по типу (position, display, colors, font, miscellaneous...).

Есть плюсы и минусы в обоих вариантах. С одной стороны, сортировка в алфавитном порядке является универсальной (по крайней мере для языков, использующих латинский алфавит), поэтому нет никаких споров о сортировке свойств. Тем не менее, мне весьма странно видеть свойства, такие как `bottom` и` top` не рядом друг с другом. Почему анимации должно появиться перед видом? Есть много странностей с алфавитной сортировкой.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  background: black;
  bottom: 0;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
  height: 100px;
  overflow: hidden;
  position: absolute;
  right: 0;
  width: 100px;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  background: black
  bottom: 0
  color: white
  font-weight: bold
  font-size: 1.5em
  height: 100px
  overflow: hidden
  position: absolute
  right: 0
  width: 100px
{% endhighlight %}
  </div>
</div>

С другой стороны, сортировка свойств по типу имеет смысл. Каждые объявления относящиеся к шрифтам  располагаются рядом, как `top` и` bottom`, и чтение набора правил отчасти становится как чтение рассказа. Но если вы не будете придерживаться некоторых конвенций, как [Идиоматический CSS](https://github.com/necolas/idiomatic-css), есть много места для интерпретации. Где будет `white-space` рядом со шрифтами или с видом? Где расположить `overflow`? Что такое порядок свойств в группе (это может быть в алфавитном порядке, о ирония)?

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  height: 100px;
  width: 100px;
  overflow: hidden;
  position: absolute;
  bottom: 0;
  right: 0;
  background: black;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  height: 100px
  width: 100px
  overflow: hidden
  position: absolute
  bottom: 0
  right: 0
  background: black
  color: white
  font-weight: bold
  font-size: 1.5em
{% endhighlight %}
  </div>
</div>

Существует также еще одно интересное поддерево типа упорядочения и называется [Концентрический CSS](https://github.com/brandon-rhodes/Concentric-CSS), который, кажется, довольно популярен, что хорошо. В основном, концентрический CSS опирается на блочную модель, чтобы определить порядок: начинается за пределами, движется внутрь.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  width: 100px;
  height: 100px;
  position: absolute;
  right: 0;
  bottom: 0;
  background: black;
  overflow: hidden;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  width: 100px
  height: 100px
  position: absolute
  right: 0
  bottom: 0
  background: black
  overflow: hidden
  color: white
  font-weight: bold
  font-size: 1.5em
{% endhighlight %}
  </div>
</div>

Я должен сказать, что я не могу решить сам.[Недавний опрос на CSS-Tricks], что (http://css-tricks.com/poll-results-how-do-you-order-your-css-properties/) установлено, что более 45% разработчиков упорядочивают свойства по типу, против 14% в алфавитном порядке. Кроме того, есть 39%, которые делают это случайно, я в том числе.

<figure role="group">
  <img src="/assets/images/css_order_chart.png" alt="График, показывающий, как разработчики упорядочивают свой CSS" />
  <figcaption>График, показывающий, как разработчики упорядочивают свой CSS</figcaption>
</figure>

Из-за этого, я не буду навязывать вам выбор. Выберите тот, который вы предпочитаете, пока вы последовательны в ваших стилях.

<div class="note">
  <p>A <a href="http://peteschuster.com/2014/12/reduce-file-size-css-sorting/">Недавние исследования</a> показали, что использование <a href="https://github.com/csscomb/csscomb.js">CSS Comb</a> (которое использует <a href="https://github.com/csscomb/csscomb.js/blob/master/config/csscomb.json">для упорядовачивания по типу</a>) для упорядочивания CSS помагает уменьшить общий размер файлы при Gzip сжатие на 2.7%, в сравнение с 1.3%, когда происходи упорядочение по алфовиту.</p>
</div>



### Дальнейшее чтение

* [CSS Comb](https://github.com/csscomb/csscomb.js)
* [Concentric CSS](https://github.com/brandon-rhodes/Concentric-CSS)
* [Idiomatic CSS](https://github.com/necolas/idiomatic-css)
* [On Declaration Sorting](http://meiert.com/en/blog/20140924/on-declaration-sorting/)
* [Reduce File Size With CSS Sorting](http://peteschuster.com/2014/12/reduce-file-size-css-sorting/)
* [Poll Results: How Do You Order Your CSS Properties?](http://css-tricks.com/poll-results-how-do-you-order-your-css-properties/)






## Вложеность селекторов

Одна особенность Sass, которую не слишком используют многие разработчики *вложенность селекторов*. Она повзволяет автору таблицы стилей вычислять длинные селектыр вкладывая короткие селекторы друг в друга.

### Общие правила

Например, такая Sass вложенность:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  .bar {
    &:hover {
      color: red;
    }
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  .bar
    &:hover
      color: red
{% endhighlight %}
  </div>
</div>

... сгенерирует такой CSS:

{% highlight css %}
.foo .bar:hover {
  color: red;
}
{% endhighlight %}

В Sass 3.3 можно использовать ссылку на текущий селектор, используя (`&`), чтобы создать дополнительные селекторы. Например:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  &-bar {
    color: red;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  &-bar
    color: red
{% endhighlight %}
  </div>
</div>

... сгенерирует такой CSS:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo-bar {
  color: red;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo-bar
  color: red
{% endhighlight %}
  </div>
</div>

Это метода часто используется в  [BEM методологие](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) для генерации `.block__element` и `.block--modifier` селекторов, основанных на базовом селекторе (т.е `.block` в данном примере).

<div class="note">
  <p>Выходит анекдот, что создавая новые селекторы из ссылки на текущий селектора
</div>

Проблема с вложенностью селекторов в том, что это в конечном итоге делает код более трудным для чтения. Нужно уметь мысленно вычислять, что получится в результате из уровней вложенности; не всегда вполне очевидно, что за CSS будет в конечном итоге.

Это утверждение становится правдивее, когда селекторы становяться длиньше и ссылки на текущий селектор (`&`) более частыми. В какой-то момент, риск потерять след и не будучи в состоянии понять, что происходит на больше настолько высока, не стоит этого.

Чтобы предотвратить такую ситуацию, **избегайте вложенности селекторов, насколько это возможно**. Тем не менее, есть, очевидно, несколько исключений из этого правила.

### Исключения

Во-первых, разрешено и даже рекомендуется вкладывать псевдо-классы и псевдо-элементы в начальный селектор.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  color: red;

  &:hover {
    color: green;
  }

  &::before {
    content: 'псевдо-элемент';
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  color: red

  &:hover
    color: green

  &::before
    content: 'псевдо-элемент'
{% endhighlight %}
  </div>
</div>

Использование вложенности селекторов для псевдо-классов и псевдо-элементов не только имеет смысл (потому что имеет дело с тесно связанными селекторами), но также помогает держать всю информацию о компонента в одном месте.

Кроме того, при использовании классов, обозначающих состояние, таких как `.is-active`, это прекрасно подходит для того, чтобы вкладывать их под селектор компонента, чтобы все выглядело аккуратно.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  // ...

  &.is-active {
    font-weight: bold;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  // ...

  &.is-active
    font-weight: bold
{% endhighlight %}
  </div>
</div>

Последнее, но не менее важное, при оформлении элемента, часто случается, что он содержится в другом элементе, тут также хорошо использовать вложенность, чтобы держать все о компоненте в том же месте.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  // ...

  .no-opacity & {
    display: none;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  // ...

  .no-opacity &
    display: none
{% endhighlight %}
  </div>
</div>

При работе с неопытными разработчиками, селекторны такие как `.no-opacity &` могут выглядеть немного странно. Для предотвращения какой-либо путаницы, можно построить очень короткий миксин, который преобразует этот странный синтаксис в явный API.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Миксин для предоставления простого API вложенности
/// @param {String} $selector - Selector
@mixin when-inside($selector) {
  #{$selector} & {
    @content;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Миксин для предоставления простого API вложенности
/// @param {String} $selector - Selector
=when-inside($selector) {
  #{$selector} &
    @content
}
{% endhighlight %}
  </div>
</div>

Переписывание нашего предыдущего примера будет выглядеть следующим образом:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  // ...

  @include when-inside('.no-opacity') {
    display: none;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  // ...

  +when-inside('.no-opacity')
    display: none
{% endhighlight %}
  </div>
</div>

Как и везде, специфика несколько неуместна, последовательность является ключевым фактором. Если вы чувствуете, что полностью уверены во вложенности селекторов, тогда используйте ее. Просто убедитесь, что вся ваша команда справится с этим.






### Дальнейшее чтение

* [Beware of Selector Nesting](http://www.sitepoint.com/beware-selector-nesting-sass/)
* [The Inception Rule](http://thesassway.com/beginner/the-inception-rule)
* [Avoid nested selectors for more modular CSS](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css)











# Конвенции наименования

В этом разделе мы не будем иметь дело с лучшими конвенциями CSS именования для сопровождения и масштабирования; не только потому, что это остается за вами, это также из области руководства по стилям для Sass. Я предлагаю те, которые рекомендованы [CSS Руководством](http://cssguidelin.es/#naming-conventions).

Есть несколько вещей, которые вы можете называть в Sass, и очень важно, чтобы названия были хорошими, чтобы весь код выглядил последовательным и легко читался:

* переменные;
* функции;
* миксины.

Sass заполнители намеренно исключены из этого списка, так как они могут быть рассмотрены как обычные селекторы CSS и использовать теже принципы именования как и классы.

Что касается переменных, функций и миксинов, мы будем придерживаться чего-то очень *CSS-ого*: **нижние подчеркивание и дефисы**, и, прежде всего смысл.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$vertical-rhythm-baseline: 1.5rem;

@mixin size($width, $height: $width) {
  // ...
}

@function opposite-direction($direction) {
  // ...
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$vertical-rhythm-baseline: 1.5rem

=size($width, $height: $width)
  // ...

@function opposite-direction($direction)
  // ...
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [CSS Guidelines' Naming Conventions](http://cssguidelin.es/#naming-conventions)






## Константы

Если вы разработчик фреймворка или библиотеки, вам бы пришлось иметь дело с переменными, которые не предназначены для обновления при любых обстоятельствах: константами. К сожалению (или к счастью?), Sass не дает какой-либо способ определения таких переменных, поэтому мы должны придерживаться строгих соглашений об именование.

Как и для многих языков, я предлагаю делать константы переменными в верхнем регистре. Это не только очень старое соглашение, но это также хорошо контрастирует с обычными строчными переменными.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$CSS_POSITIONS: top, right, bottom, left, center;

// Nope
$css-positions: top, right, bottom, left, center;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$CSS_POSITIONS: top, right, bottom, left, center

// Nope
$css-positions: top, right, bottom, left, center
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Dealing With Constants in Sass](http://www.sitepoint.com/dealing-constants-sass/)






## Пространство имен

Если вы собираетесь распространять ваш Sass код, например, как библиотеку, фрейворк, сетку или что угодно, вы, возможно, захотите рассмотреть пространства имен всех своих переменных, функций,  миксинов и заполнителей, так чтобы они не конфликтовали с чьим-либо кодом.

Например, если вы работаете над проектом *Sassy Unicorn*, который предназначен для использования разработчиками по всему миру (кто бы не хотел, не так ли?), Вы можете рассмотреть возможность использования `su-` как пространство имен. Это достаточно конкретно, чтобы предотвратить любые конфликты имен и достаточно коротко, чтобы не быть болью при написание кода.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$su-configuration: ( ... );

@function su-rainbow($unicorn) {
  // ...
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$su-configuration: ( ... )

@function su-rainbow($unicorn)
  // ...
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p>Обратите внимание, что автоматическая генерация пространств имен, безусловно, цель для предстоящего проекта <code>@import</code> Sass 4.0. Так как это становится все ближе и ближе, то использование библиотек с пространством имен написанным вручную может стать сложнее в использование.</p>
</div>

### Дальнейшее чтение

* [Please Respect the Global CSS Namespace](http://blog.kaelig.fr/post/44554267597/please-respect-the-global-css-namespace)











# Комментирование

CSS является сложным языком, полным хаков и курьезов. Из-за этого, он должен быть прокомментирован, особенно, если вы или кто-то еще собирается читать и обновлять код 6 месяцев или 1 год спустя. Не ставьте себя или кого-нибудь другого в положении *Я не писал этого, о боже, почему*.

Есть еще много возможностей для комментариев в CSS. Это могут быть объяснениями:

* Структура и/или роль файла
* цель набора правил;
* объяснение использования магического числа;
* причина объявления CSS;
* порядок объявления в CSS;
* мыслительный процесс.

И я, наверное, забыл много других различных причин. Комментирование занимает очень мало времени, когда делается вместе с написанием кода, так что делайте это в нужное время. Возвращаясь на кусок кода, чтобы комментировать его не только совершенно нереально, но и крайне раздражительно.






## Написание комментариев

В идеале, *любой* набор CSS правил должен предшествовать комментарию в C-стиле, объясняя цель CSS блока. Этот комментарий также принимает пронумерованные объяснения по поводу конкретных частей набора правил. Например:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/**
 * Вспомогательный класс для усечения и добавления многоточия в слишком длинную строку
 * на одной линии.
 * 1. Предотвращает сворачивание контента, оставляет его на одной линии.
 * 2. Добавляет многоточие на конце линии.
 */
.ellipsis {
  white-space: nowrap; /* 1 */
  text-overflow: ellipsis; /* 2 */
  overflow: hidden;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/**
 * Вспомогательный класс для усечения и добавления многоточия в слишком длинную строку
 * на одной линии.
 * 1. Предотвращает сворачивание контента, оставляет его на одной линии.
 * 2. Добавляет многоточие на конце линии.
 */
.ellipsis
  white-space: nowrap /* 1 */
  text-overflow: ellipsis /* 2 */
  overflow: hidden
{% endhighlight %}
  </div>
</div>

В основном все, что не является очевидным, на первый взгляд, должны быть прокомментировано. Нет такого понятия, как слишком много документации. Помните, что вы не можете *комментировать слишком много*, так что пишите комментарии ко всему, что стоит их.

Комментируя Sass раздел, используйте Sass встроенные комментарии вместо блока в C-стиле. Это делает комментарий невидимым на выходе, даже в расширенном режиме в процессе разработки.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Добавить текущий модуль в список импортируемых модулей.
// `!global` важный флаг для глобального обновления переменной.
$imported-modules: append($imported-modules, $module) !global;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Добавить текущий модуль в список импортируемых модулей.
// `!global` важный флаг для глобального обновления переменной.
$imported-modules: append($imported-modules, $module) !global
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [CSS Guidelines' Commenting section](http://cssguidelin.es/#commenting)

{% include donate.html %}






## Документация

Каждая переменная, функция, миксин и плейсхолдер, который предназначен для повторного использования во всем коде должен быть задокументирован как часть глобального API с использованием [SassDoc](http://sassdoc.com).

SassDoc обеспечивает два различных синтаксиса для комментариев: или C-стиль или инлайн. Например, оба из следующих фрагментов являются допустимыми комментариями SassDoc:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/**
 * Вертикальный ритм, использующийся во всем коде.
 * @type Length
 */
$vertical-rhythm-baseline: 1.5rem;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/**
 * Вертикальный ритм, использующийся во всем коде.
 * @type Length
 */
$vertical-rhythm-baseline: 1.5rem
{% endhighlight %}
  </div>
</div>

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Вертикальный ритм, использующийся во всем коде.
/// @type Length
$vertical-rhythm-baseline: 1.5rem;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Вертикальный ритм, использующийся во всем коде.
/// @type Length
$vertical-rhythm-baseline: 1.5rem
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p>Необходим тройной слэш (<code>/</code>).</p>
</div>

Нет никакой выгоды в использовании одного над другим, так что выбирайте тот, который в котром чувствуете себя наиболее уверенно.

SassDoc имеет две основные фунцкии:

* обходит стандартные комментарии, используя систему аннотации на основе всего, что является частью публичного или частного API;
* возможность генерировать HTML версию документации API с помощью любого инструмента генерирования SassDoc (CLI tool, Grunt, Gulp, Broccoli, Node...).

<figure role="group">
<img alt="Документация сгенерированная SassDoc" src="/assets/images/sassdoc-preview.png" />
<figcaption>Документация сгенерированная SassDoc</figcaption>
</figure>

Вот пример миксина обширно документированого с SassDoc:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Миксин позволяет определять `width` и `height` одновременно.
///
/// @author Hugo Giraudel
///
/// @access public
///
/// @param {Length} $width - Element's `width`
/// @param {Length} $height ($width) - Element's `height`
///
/// @example scss - Usage
/// .foo {
///   @include size(10em);
/// }
///
/// .bar {
///   @include size(100%, 10em);
/// }
///
/// @example css - CSS output
/// .foo {
///   width: 10em;
///   height: 10em;
/// }
///
/// .bar {
///   width: 100%;
///   height: 10em;
/// }
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Миксин позволяет определять `width` и `height` одновременно.
///
/// @author Hugo Giraudel
///
/// @access public
///
/// @param {Length} $width - Element's `width`
/// @param {Length} $height ($width) - Element's `height`
///
/// @example scss - Usage
/// .foo
///   +size(10em)
///
/// .bar
///   +size(100%, 10em)
///
/// @example css - CSS output
/// .foo {
///   width: 10em;
///   height: 10em;
/// }
///
/// .bar {
///   width: 100%;
///   height: 10em;
/// }
=size($width, $height: $width)
  width: $width
  height: $height
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [SassDoc](http://sassdoc.com)
* [SassDoc: a Documentation Tool for Sass](http://www.sitepoint.com/sassdoc-documentation-tool-sass/)
* [New Features and New Look for SassDoc](http://webdesign.tutsplus.com/articles/new-features-and-a-new-look-for-sassdoc--cms-21914)











# Архитектура

Разработка архитектуры CSS проекта, вероятно, один из самых сложных вещей, которые вы должны будете сделать в жизни проекта. Сохранение архитектуры последовательной и значимой еще сложнее.

К счастью, одно из главных преимуществ использования CSS препроцессоров, возможность разделить кодовую базы в несколько файлов без ущерба для производительности (например,  CSS директива  `@import`). Благодаря Sass `@import`, это совершенно безопасно (и на самом деле рекомендуется), использовать столько файлов, сколько необходимо в развитии, все они потом будут собраны в одном файлк стилей в продакшене.

Кроме того, я не могу не подчеркнуть потребность в папках, даже на небольших проектах. Дома вы не кладете каждый лист бумаги в один и тот же ящик. Вы можете использовать папки; одну для дома, другую для банка, третью для счетов, и так далее. Нет причин поступить иначе при структурировании CSS проекта. Разделяйте кодовую базы на папки, чтобы легко найти материал позже.

Есть много популярных архитектур CSS проектов: [OOCSS](http://oocss.org/), [атомной дизайн](http://bradfrost.com/blog/post/atomic-web-design/), [Bootstrap](http://getbootstrap.com/), [Foundation](http://foundation.zurb.com/) и тому подобные ... все они имеют свои достоинства, плюсы и минусы.

Я сам, использовую подход, который, очень похож на [SMACSS](https://smacss.com/) от [Джонатана Снука](http://snook.ca/), который сосредотачивается на сохранении простоты и очевидности.

<div class="note">
  <p>Я понял, что в основном архитектура зависит от проекта. Используйте или адаптируйте предложенное решение, так чтобы вы имели дело с системой, которая соответствует вашим потребностям.</p>
</div>



### Дальнейшее чтение

* [Architecture for a Sass project](http://www.sitepoint.com/architecture-sass-project/)
* [A Look at Different Sass Architectures](http://www.sitepoint.com/look-different-sass-architectures/)
* [FR] [Sass, une architecture composée](http://slides.com/hugogiraudel/sass-une-architecture-composee)
* [SMACSS](https://smacss.com/)
* [An Introduction to OOCSS](http://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/)
* [Atomic Web Design](http://bradfrost.com/blog/post/atomic-web-design/)






## Компоненты

Существует главное отличие между тем, чтобы сделать код *работающим*, или сделать его *хорошим*. Опять таки, CSS вполне несносный язык <sup>[citation needed]</sup>. Чем меньше CSS мы имеем, тем лучше. Мы не хотим иметь дело с мегабайтами кода. Чтобы держать стилевые файлы короткими и эффективными&mdash;и это не будет для вас сюрпризом&mdash;чаще всего бедут хорошей идеей подумать об интерфейсе, как о наборе компонентов.

Компоненты могут быть чем угодно, до тех пор пока они:

* делают одну и только одну вещь;
* могут быть повторно используемы;
* независимы.

Например, форма поиска должна рассматриваться в качестве компонента. Она должна иметь возможность быть использована повторно на разных страницах, в различных ситуациях. Она не должна зависеть от положения в DOM(подвале, боковой панели, главного содержания ...).

Большинство интерфейсов можно рассматривать как набор маленьких компонентов, и я настоятельно рекомендую вам придерживаться этой парадигмы. Это позволит не только сократить количество CSS, необходимого для всего проекта, но также, упростить его поддержку, и хаотический беспорядок.






## Шаблон 7-1

Возвратимся к архитектуре? Я обычно использую, что я называю *Шаблон 7-1*: 7 папок, 1 файл. Обычно у вас есть все ваши паршлы в 7 разных папках, и один файл в корневом каталоге (обычно с именем `main.scss`), который импортирует их все.

* `base/`
* `components/`
* `layout/`
* `pages/`
* `themes/`
* `utils/`
* `vendors/`

И конечно:

* `main.scss`

<figure role="group">
  <img src="/assets/images/sass-wallpaper.jpg" alt="Один файл чтобы управлять ими всеми, один файл, чтобы найти их, один файл, чтобы привести их всех и отдать Sass для объединения их." />
  <figcaption>Обои от <a href="https://twitter.com/julien_he">Julien He</a></figcaption>
</figure>

В идеале, мы может закончить с чем-то похожим:

<div class="highlight"><pre><code>
sass/
|
|– base/
|   |– _reset.scss       # Reset/normalize
|   |– _typography.scss  # Типографисечкие правила
|   ...                  # и т.д.
|
|– components/
|   |– _buttons.scss     # Кнопки
|   |– _carousel.scss    # Карусель
|   |– _cover.scss       # Обложка
|   |– _dropdown.scss    # Выпадающий список
|   ...                  # и т.д.
|
|– layout/
|   |– _navigation.scss  # Навигация
|   |– _grid.scss        # Сетка
|   |– _header.scss      # Шапка
|   |– _footer.scss      # Подвал
|   |– _sidebar.scss     # Боковая панель
|   |– _forms.scss       # Формы
|   ...                  # и т.д.
|
|– pages/
|   |– _home.scss        # Стили, специфичные для главной страницы
|   |– _contact.scss     # Стили, специфичные для страницы контактов
|   ...                  # и т.д.
|
|– themes/
|   |– _theme.scss       # Тема по умолчанию
|   |– _admin.scss       # Тема админа
|   ...                  # и т.д.
|
|– utils/
|   |– _variables.scss   # Sass переменные
|   |– _functions.scss   # Sass функции
|   |– _mixins.scss      # Sass миксины
|   |– _helpers.scss     # Хелперы классов & плейсходеров
|
|– vendors/
|   |– _bootstrap.scss   # Bootstrap
|   |– _jquery-ui.scss   # jQuery UI
|   ...                  # и т.д.
|
|
`– main.scss             # главный Sass файл
</code></pre></div>

<div class="note">
  <p>Следующие файлы имеют туже конвенцию наименования, что и выше: они отделены нижним подчеркивание.</p>
</div>



### Папка Base

Папка `base/` содержит шаблонный код проекта. Там, вы можете найти файл сброса, некоторые типографские правила, и, вероятно, стили (я привык их называть `_base.scss`), определяющие некоторые стандартные стили для часто используемых элементов HTML.

* `_base.scss`
* `_reset.scss`
* `_typography.scss`



### Папка Layout

Папка `layout/` содержит все, что принимает участие в постройке сайта или приложения. Эта папка может содержать стили для основных частей сайта (шапка, футер, навигация, боковая панель...), сетка или даже CSS стили для всех форм.

* `_grid.scss`
* `_header.scss`
* `_footer.scss`
* `_sidebar.scss`
* `_forms.scss`
* `_navigation.scss`

<div class="note">
  <p>Папка <code>layout/</code> может быть названа <code>partials/</code>, на ваше усморение.</p>
</div>



### Папка Components

Для маленьких компонентов, есть папка `components/`. В то время, как `layout/`  *макро* (определяет глобальную сетку), `components/` больше сфокусирована на виджетах. И содержит все модули по типу слайдер, лоудера и т.п. виджетов. Обычно там много файлов `components/` с тех пор как приложение или сайт состоит из мгножества мелких модулей.

* `_media.scss`
* `_carousel.scss`
* `_thumbnails.scss`

<div class="note">
  <p>Папка <code>components/</code> может быть <code>modules/</code>, на ваше усмотрение.</p>
</div>



### Папка Pages

Если у вас есть стили зависищие от страницы, лучше положить их в папку `pages/`, в файл, названный в честь страницы. Например, это не редкость иметь очень конкретные стили для главной страницы, следовательно, существует потребность в `_home.scss` в `pages/`.

* `_home.scss`
* `_contact.scss`

<div class="note">
  <p>В зависимости от способа доставки когда, эти файлы можно было бы назвать самостоятельно, чтобы избежать их объединения с другими стилями. На ваше усмотрение.</p>
</div>



### Папка Themes

В больших сайтах и проложения не является необчным наличие разных тем. Есть разные способы работы с темами, я лично предпочитаю складывать их в папку `themes/`.

* `_theme.scss`
* `_admin.scss`

<div class="note">
  <p>Это очень специфично для проектов и не сильно распространено.</p>
</div>



### Папка Utils

Папка `utils/` собирает Sass инструменты и хелперы в проекте. Каждая глобальная переменная, функция, миксин должна быть помещена сюда.

Правило для этой папки в том, что она не должна генерировать CSS при компиляции сама по себе. Это не что иное, как Sass хелперы.

* `_variables.scss`
* `_mixins.scss`
* `_functions.scss`
* `_placeholders.scss` (frequently named `_helpers.scss`)

<div class="note">
  <p>Папка <code>utils/</code> может также быть названа <code>helpers/</code>, <code>sass-helpers/</code> или <code>sass-utils/</code>, на ваше усмотрение.</p>
</div>



### папка Vendors

И последнее, но менее важное, что больгинство проектов будут иметь папку `vendors/`, содержащую все CSS файлы из внешних библиотет и фреймворков – Normalize, Bootstrap, jQueryUI, FancyCarouselSliderjQueryPowered, и так далее. Нахождение этих файлов в этой папке хороший способ сказать: "Эй, это не от меня, а не мой код, не моя обязанность".

* `_normalize.scss`
* `_bootstrap.scss`
* `_jquery-ui.scss`
* `_select2.scss`

Если вы хотите что-то переписать в этих файлах, то я рекомендую вам ввести 8 папку `vendors-extensions/`, в которой вы будете хранить файлы перезаписи свойст точно с такими же именами.

Например, `vendors-extensions/_boostrap.scss` файл, содержащий все CSS парвила на перезапись правил CSS Bootstrap. Это для того, чтобы не править сами вендоры, что на самом деле не очень хорошая идея.



### Main файл

Главный файл (обычно названный `main.scss`) должен быть единственным файлом Sass, который не начинается с нижнего поддчекивания. Этот файл не должен содержать ничего кроме `@import` и комментариев.

Файлы должны быть импортированы в соответствие с папкой размещения, один за другим в соответствуещем порядке:

1. `vendors/`
1. `utils/`
1. `base/`
1. `layout/`
1. `components/`
1. `pages/`
1. `themes/`

Чтобы улучшить читаемость, главный файл должен следовать этим рекомендация:

* один `@import` на линии;
* не вставлять новые линии между файлами из одной папки;
* новая линия после вставки последнего `@import` из одной и той же папки;
* не писать расширения и нижние подчеркивание.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@import 'vendors/bootstrap';
@import 'vendors/jquery-ui';

@import 'utils/variables';
@import 'utils/functions';
@import 'utils/mixins';
@import 'utils/placeholders';

@import 'base/reset';
@import 'base/typography';

@import 'layout/navigation';
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';
@import 'layout/sidebar';
@import 'layout/forms';

@import 'components/buttons';
@import 'components/carousel';
@import 'components/cover';
@import 'components/dropdown';

@import 'pages/home';
@import 'pages/contact';

@import 'themes/theme';
@import 'themes/admin';
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@import vendors/bootstrap
@import vendors/jquery-ui

@import utils/variables
@import utils/functions
@import utils/mixins
@import utils/placeholders

@import base/reset
@import base/typography

@import layout/navigation
@import layout/grid
@import layout/header
@import layout/footer
@import layout/sidebar
@import layout/forms

@import components/buttons
@import components/carousel
@import components/cover
@import components/dropdown

@import pages/home
@import pages/contact

@import themes/theme
@import themes/admin
{% endhighlight %}
  </div>
</div>

Существует еще один способ импорта, который действует также. На одной стороны, это делает файл более читаемым. С другой стороны, это делает его обновления немного более болезненным. Во всяком случае, вам решать, что лучше, это не имеет большого значения. Основной файл следует следующим принципам:

* один `@import` на папку;
* перенос строки после `@import`;
* каждый файл на своей строке;
* новая строка после последнего импорта файлы из папки;
* расширение файлов и нижние поддчеркивание упускается.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@import
  'vendors/bootstrap',
  'vendors/jquery-ui';

@import
  'utils/variables',
  'utils/functions',
  'utils/mixins',
  'utils/placeholders';

@import
  'base/reset',
  'base/typography';

@import
  'layout/navigation',
  'layout/grid',
  'layout/header',
  'layout/footer',
  'layout/sidebar',
  'layout/forms';

@import
  'components/buttons',
  'components/carousel',
  'components/cover',
  'components/dropdown';

@import
  'pages/home',
  'pages/contact';

@import
  'themes/theme',
  'themes/admin';
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@import
  vendors/bootstrap,
  vendors/jquery-ui

@import
  utils/variables,
  utils/functions,
  utils/mixins,
  utils/placeholders

@import
  base/reset,
  base/typography

@import
  layout/navigation,
  layout/grid,
  layout/header,
  layout/footer,
  layout/sidebar,
  layout/forms

@import
  components/buttons,
  components/carousel,
  components/cover,
  components/dropdown

@import
  pages/home,
  pages/contact

@import
  themes/theme,
  themes/admin
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p>In order to not have to import each file manually, there is an extension to Ruby Sass called <a href="https://github.com/chriseppstein/sass-globbing">sass-globbing</a>, making it possible to use glob patterns in Sass <code>@import</code> such as <code>@import "components/*"</code>.</p>
  <p>That being said, I would not recommend it because it imports files following the alphabetical order which is usually not what you want, especially when dealing with a source-order dependent language.</p>
</div>






## Shame file

There is an interesting concept that has been made popular by [Harry Roberts](http://csswizardry.com), [Dave Rupert](http://daverupert.com) and [Chris Coyier](http://css-tricks.com) that consists of putting all the CSS declarations, hacks and things we are not proud of in a *shame file*. This file, dramatically titled `_shame.scss`, would be imported after any other file, at the very end of the stylesheet.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/**
 * Nav specificity fix.
 *
 * Someone used an ID in the header code (`#header a {}`) which trumps the
 * nav selectors (`.site-nav a {}`). Use !important to override it until I
 * have time to refactor the header stuff.
 */
.site-nav a {
    color: #BADA55 !important;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/**
 * Nav specificity fix.
 *
 * Someone used an ID in the header code (`#header a {}`) which trumps the
 * nav selectors (`.site-nav a {}`). Use !important to override it until I
 * have time to refactor the header stuff.
 */
.site-nav a
    color: #BADA55 !important
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [shame.css](http://csswizardry.com/2013/04/shame-css/)
* [shame.css - full .net interview](http://csswizardry.com/2013/04/shame-css-full-net-interview/)











# Responsive Web Design and breakpoints

I do not think we still have to introduce Responsive Web Design now that it is everywhere. However you might ask yourself *why is there a section about RWD in a Sass styleguide?* Actually there are quite a few things that can be done to make working with breakpoints easier, so I thought it would not be such a bad idea to list them here.






## Naming breakpoints

I think it is safe to say that media queries should not be tied to specific devices. For instance, this is definitely a bad idea to try targeting iPads or Blackberry phones specifically. Media queries should take care of a range of screen sizes, until the design breaks and the next media query takes over.

For the same reasons, breakpoints should not be named after devices but something more general. Especially since some phones are now bigger than tablets, some tablets bigger than some tiny screen computers, and so on...

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$breakpoints: (
  'medium': (min-width: 800px),
  'large': (min-width: 1000px),
  'huge': (min-width: 1200px),
);

// Nope
$breakpoints: (
  'tablet': (min-width: 800px),
  'computer': (min-width: 1000px),
  'tv': (min-width: 1200px),
);
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$breakpoints: ("medium": (min-width: 800px), "large": (min-width: 1000px), "huge": (min-width: 1200px))

// Nope
$breakpoints: ("tablet": (min-width: 800px), "computer": (min-width: 1000px), "tv": (min-width: 1200px))
{% endhighlight %}
  </div>
</div>

At this point, any naming convention that makes crystal clear that a design is not intimately tied to a specific device type will do the trick, as long as it gives a sense of magnitude.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$breakpoints: (
  'seed': (min-width: 800px),
  'sprout': (min-width: 1000px),
  'plant': (min-width: 1200px),
);
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$breakpoints: ("seed": (min-width: 800px), "sprout": (min-width: 1000px), "plant": (min-width: 1200px))
{% endhighlight %}
  </div>
</div>




### Дальнейшее чтение

* [Naming Media Queries](http://css-tricks.com/naming-media-queries/)






## Breakpoint manager

Once you have named your breakpoints the way you want, you need a way to use them in actual media queries. There are plenty of ways to do so but I must say I am a big fan of the breakpoint map read by a getter function. This system is both simple and efficient.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Responsive manager.
/// @access public
/// @param {String} $breakpoint - Breakpoint
/// @requires $breakpoints
@mixin respond-to($breakpoint) {
  @if map-has-key($breakpoints, $breakpoint) {
    @media #{inspect(map-get($breakpoints, $breakpoint))} {
      @content;
    }
  }

  @else {
    @error 'No value found for `#{$breakpoint}`. '
         + 'Please make sure it is defined in `$breakpoints` map.';
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Responsive manager.
/// @access public
/// @param {String} $breakpoint - Breakpoint
/// @requires $breakpoints
=respond-to($breakpoint)
  @if map-has-key($breakpoints, $breakpoint)
    @media #{inspect(map-get($breakpoints, $breakpoint))}
      @content

  @else
    @error 'No value found for `#{$breakpoint}`. '
         + 'Please make sure it is defined in `$breakpoints` map.'
{% endhighlight %}
  </div>
</div>

<div class="note">
  <p>Obviously, this is a fairly simplistic breakpoint manager that will not do the trick when dealing with custom and/or multiple-checks breakpoints.</p>
  <p>If you need a slightly more permissive breakpoint manager, may I recommend you do not reinvent the wheel and use something that has been proven effective such as <a href="https://github.com/sass-mq/sass-mq">Sass-MQ</a>, <a href="http://breakpoint-sass.com/">Breakpoint</a> or <a href="https://github.com/eduardoboucas/include-media">include-media</a>.</p>
</div>



### Дальнейшее чтение

* [Managing Responsive Breakpoints in Sass](http://www.sitepoint.com/managing-responsive-breakpoints-sass/)
* [Approaches to Media Queries in Sass](http://css-tricks.com/approaches-media-queries-sass/)






## Media Queries Usage

Not so long ago, there has been a quite hot debate about where should be written media queries: should they belong within selectors (as Sass allows it) or strictly dissociated from them? I have to say I am a fervent defender of the *media-queries-within-selectors* system, as I think it plays well with the ideas of *components*.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  color: red;

  @include respond-to('medium') {
    color: blue;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  color: red

  +respond-to('medium')
    color: blue
{% endhighlight %}
  </div>
</div>

Leading to the following CSS output:

{% highlight css %}
.foo {
  color: red;
}

@media (min-width: 800px) {
  .foo {
    color: blue;
  }
}
{% endhighlight %}

You might hear that this convention results in duplicated media queries in the CSS output. That is definitely true. Although, [tests have been made](http://sasscast.tumblr.com/post/38673939456/sass-and-media-queries) and the final word is that it doesn't matter once Gzip (or any equivalent) has done its thing:

> … we hashed out whether there were performance implications of combining vs scattering Media Queries and came to the conclusion that the difference, while ugly, is minimal at worst, essentially non-existent at best.<br>
> &mdash; [Sam Richards](https://twitter.com/snugug), regarding [Breakpoint](http://breakpoint-sass.com/)

Now, if you really are concerned about duplicated media queries, you can still use a tool to merge them such as [this gem](https://github.com/aaronjensen/sass-media_query_combiner) however I feel like I have to warn you against possible side-effects of moving CSS code around. You are not without knowing that source order is important.



### Дальнейшее чтение

* [Sass and Media Queries](http://sasscast.tumblr.com/post/38673939456/sass-and-media-queries)
* [Inline or Combined Media queries? Fight!](http://benfrain.com/inline-or-combined-media-queries-in-sass-fight/)
* [Sass::MediaQueryCombiner](https://github.com/aaronjensen/sass-media_query_combiner)











# Variables

Variables are the essence of any programming language. They allow us to reuse values without having to copy them over and over again. Most importantly, they make updating a value very easy. No more find and replace or manual crawling.

However CSS is nothing but a huge basket containing all our eggs. Unlike many languages, there are no real scopes in CSS. Because of this, we have to pay real attention when adding variables at the risk of witnessing conflicts.

My advice would be to only create variables when it makes sense to do so. Do not initiate new variables for the heck of it, it won't help. A new variable should be created only when all of the following criteria are met:

* the value is repeated at least twice;
* the value is likely to be updated at least once;
* all occurrences of the value are tied to the variable (i.e. not by coincidence).

Basically, there is no point declaring a variable that will never be updated or that is only being used at a single place.






## Scoping

Variable scoping in Sass has changed over the years. Until fairly recently, variable declarations within rulesets and other scopes were local by default. However when there was already a global variable with the same name, the local assignment would change the global variable. Since version 3.4, Sass now properly tackles the concept of scopes and create a new local variable instead.

The docs talk about *global variable shadowing*. When declaring a variable that already exists on the global scope in an inner scope (selector, function, mixin...), the local variable is said to be *shadowing* the global one. Basically, it overrides it just for the local scope.

The following code snippet explains the *variable shadowing* concept.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Initialize a global variable at root level.
// In this case, the `!global` flag is optional.
$variable: 'initial value' !global;

// Create a mixin that overrides that global variable.
@mixin global-variable-overriding {
  $variable: 'mixin value' !global;
}

.local-scope::before {
  // Create a local variable that shadows the global one.
  $variable: 'local value';

  // Include the mixin: it overrides the global variable.
  @include global-variable-overriding;

  // Print the variable's value.
  // It is the **local** one, since it shadows the global one.
  content: $variable;
}

// Print the variable in another selector that does no shadowing.
// It is the **global** one, as expected.
.other-local-scope::before {
  content: $variable;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Initialize a global variable at root level.
// In this case, the `!global` flag is optional.
$variable: 'initial value' !global

// Create a mixin that overrides that global variable.
@mixin global-variable-overriding
  $variable: 'mixin value' !global

.local-scope::before
  // Create a local variable that shadows the global one.
  $variable: 'local value'

  // Include the mixin: it overrides the global variable.
  +global-variable-overriding

  // Print the variable's value.
  // It is the **local** one, since it shadows the global one.
  content: $variable

// Print the variable in another selector that does no shadowing.
// It is the **global** one, as expected.
.other-local-scope::before
  content: $variable
{% endhighlight %}
  </div>
</div>

{% include donate.html %}






## `!default` flag

When building a library, a framework, a grid system or any piece of Sass that is intended to be distributed and used by external developers, all configuration variables should be defined with the `!default` flag so they can be overwritten.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
$baseline: 1em !default;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
$baseline: 1em !default
{% endhighlight %}
  </div>
</div>

Thanks to this, a developer can define his own `$baseline` variable *before* importing your library without seeing his value redefined.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Developer's own variable
$baseline: 2em;

// Your library declaring `$baseline`
@import 'your-library';

// $baseline == 2em;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Developer's own variable
$baseline: 2em

// Your library declaring `$baseline`
@import your-library

// $baseline == 2em
{% endhighlight %}
  </div>
</div>






## `!global` flag

The `!global` flag should only be used when overriding a global variable from a local scope. When defining a variable at root level, the `!global` flag should be omitted.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
$baseline: 2em;

// Nope
$baseline: 2em !global;
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
$baseline: 2em

// Nope
$baseline: 2em !global
{% endhighlight %}
  </div>
</div>






## Multiple variables or maps

There are advantages of using maps rather than multiple distinct variables. The main one is the ability to loop over a map, which is not possible with distinct variables.

Another pro of using a map is the ability to create a little getter function to provide a friendlier API. For instance, consider the following Sass code:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Z-indexes map, gathering all Z layers of the application
/// @access private
/// @type Map
/// @prop {String} key - Layer's name
/// @prop {Number} value - Z value mapped to the key
$z-indexes: (
  'modal': 5000,
  'dropdown': 4000,
  'default': 1,
  'below': -1,
);

/// Get a z-index value from a layer name
/// @access public
/// @param {String} $layer - Layer's name
/// @return {Number}
/// @require $z-indexes
@function z($layer) {
  @return map-get($z-indexes, $layer);
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Z-indexes map, gathering all Z layers of the application
/// @access private
/// @type Map
/// @prop {String} key - Layer's name
/// @prop {Number} value - Z value mapped to the key
$z-indexes: ('modal': 5000, 'dropdown': 4000, 'default': 1, 'below': -1,)

/// Get a z-index value from a layer name
/// @access public
/// @param {String} $layer - Layer's name
/// @return {Number}
/// @require $z-indexes
@function z($layer)
  @return map-get($z-indexes, $layer)
{% endhighlight %}
  </div>
</div>











# Extend

The `@extend` directive has to be one of the features that made Sass so popular a couple of years ago. As a reminder, it makes it possible to tell Sass to style an element A exactly as though it also matched selector B. Needless to say this can end up being a valuable ally when writing modular CSS.

However I feel like I must warn you against this feature. As clever as it is, `@extend` still is a tricky concept that might do more harm than good, especially when poorly used. The thing is, when extending a selector, you have little to no way to answer these questions without having an in-depth knowledge of the whole codebase:

* where is my current selector going to be appended?
* am I likely to be causing undesired side-effects?
* how large is the CSS generated by this single extend?

For all you know, the result could range from doing nothing to causing disastrous side-effects. Because of this, my first advice would be to avoid the `@extend` directive altogether. It might sound brutal, but at the end of the day it can save you some headaches and troubles.

That being said, you know the saying:

> Never say never.<br>
> &mdash; Apparently, [not Beyonce](https://github.com/HugoGiraudel/sass-guidelines/issues/31#issuecomment-69112419).

There are scenarios where extending selectors might be helpful and worthwhile. Yet, always keep in mind those rules so you don't get yourself into trouble:

* Use extend from within a module, not across different modules.
* Use extend on placeholders exclusively, not on actual selectors.
* Make sure the placeholder you extend is present as little as possible in the stylesheet.

If you are going to use extend, let me also remind you that it does not play well with `@media` blocks. As you may know, Sass is unable to extend an outer selector from within a media query. When doing so, the compiler simply crashes, telling you that you cannot do such a thing. Not great. Especially since media queries are almost all we do know.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  content: 'foo';
}

@media print {
  .bar {
    // This doesn't work. Worse: it crashes.
    @extend .foo;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  content: 'foo'

@media print
  .bar
    // This doesn't work. Worse: it crashes.
    @extend .foo
{% endhighlight %}
  </div>
</div>

> You may not @extend an outer selector from within @media.<br>
> You may only @extend selectors within the same directive.

<div class="note">
  <p>It is often said that <code>@extend</code> helps with the file size since it combines selectors rather than duplicated properties. That is true, however the difference is negligible once <a href="http://en.wikipedia.org/wiki/Gzip">Gzip</a> has done its compression.</p>
  <p>That being said, if you cannot use Gzip (or any equivalent) then switching to a <code>@extend</code> approach might not be that bad as long as you know what you are doing.</p>
</div>

To sum up, I would **advise against using the `@extend` directive**, unless under some specific circumstances, but I would not go as far as to forbid it.



### Дальнейшее чтение

* [What Nobody Told you About Sass Extend](http://www.sitepoint.com/sass-extend-nobody-told-you/)
* [Why You Should Avoid Extend](http://www.sitepoint.com/avoid-sass-extend/)
* [Don't Over Extend Yourself](http://pressupinc.com/blog/2014/11/dont-overextend-yourself-in-sass/)
* [When to Use Extend; When to Use a Mixin](http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/)











# Mixins

Mixins are one of the most used features from the whole Sass language. They are the key to reusability and DRY components. And for good reason: mixins allow authors to define styles that can be reused throughout the stylesheet without needing to resort to non-semantic classes such as `.float-left`.

They can contain full CSS rules and pretty much everything that is allowed anywhere in a Sass document. They can even take arguments, just like functions. Needless to say, the possibilities are endless.

But I feel I must warn you against abusing the power of mixins. Again, the keyword here is *simplicity*. It might be tempting to build extremely powerful mixins with massive amounts of logic. It's called over-engineering and most developers suffer from it. Don't over think your code, and above all keep it simple. If a mixin ends up being longer than 20 lines or so, then it should be either split into smaller chunks or completely revised.






## Basics

That being said, mixins are extremely useful and you should be using some. The rule of thumb is that if you happen to spot a group of CSS properties that always appear together for a reason (i.e. not a coincidence), you can put them in a mixin instead. The [micro-clearfix hack from Nicolas Gallagher](http://nicolasgallagher.com/micro-clearfix-hack/) deserves to be put in a (argumentless) mixin for instance.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Helper to clear inner floats
/// @author Nicolas Gallagher
/// @link http://nicolasgallagher.com/micro-clearfix-hack/ Micro Clearfix
@mixin clearfix {
  &::after {
    content: '';
    display: table;
    clear: both;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Helper to clear inner floats
/// @author Nicolas Gallagher
/// @link http://nicolasgallagher.com/micro-clearfix-hack/ Micro Clearfix
@mixin clearfix
  &::after
    content: ''
    display: table
    clear: both
{% endhighlight %}
  </div>
</div>

Another valid example would be a mixin to size an element, defining both `width` and `height` at the same time. Not only would it make the code lighter to type, but also easier to read.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Helper to size an element
/// @author Hugo Giraudel
/// @param {Length} $width
/// @param {Length} $height
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Helper to size an element
/// @author Hugo Giraudel
/// @param {Length} $width
/// @param {Length} $height
=size($width, $height: $width)
  width: $width
  height: $height
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Sass Mixins to Kickstart your Project](http://www.sitepoint.com/sass-mixins-kickstart-project/)
* [A Sass Mixin for CSS Triangles](http://www.sitepoint.com/sass-mixin-css-triangles/)
* [Building a Linear-Gradient Mixin](http://www.sitepoint.com/building-linear-gradient-mixin-sass/)






## Arguments list

When dealing with an unknown number of arguments in a mixin, always use an `arglist` rather than a list. Think of `arglist` as the 8th hidden undocumented data type from Sass that is implicitly used when passing an arbitrary number of arguments to a mixin or a function whose signature contains `...`.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@mixin shadows($shadows...) {
  // type-of($shadows) == 'arglist'
  // ...
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
=shadows($shadows...)
  // type-of($shadows) == 'arglist'
  // ...
{% endhighlight %}
  </div>
</div>

Now, when building a mixin that accepts a handful of arguments (understand 3 or more), think twice before merging them out as a list or a map thinking it will be easier than passing them all one by one.

Sass is actually pretty clever with mixins and function declarations, so much so that you can actually pass a list or a map as an arglist to a function/mixin so that it gets parsed as a series of arguments.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@mixin dummy($a, $b, $c) {
  // ...
}

// Yep
@include dummy(true, 42, 'kittens');

// Yep but nope
$params: true, 42, 'kittens';
$value: dummy(nth($params, 1), nth($params, 2), nth($params, 3));

// Yep
$params: true, 42, 'kittens';
@include dummy($params...);

// Yep
$params: (
  'c': 'kittens',
  'a': true,
  'b': 42
);
@include dummy($params...);
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
=dummy($a, $b, $c)
  // ...

// Yep
+dummy(true, 42, 'kittens')

// Yep but nope
$params: true, 42, 'kittens'
$value: dummy(nth($params, 1), nth($params, 2), nth($params, 3))

// Yep
$params: true, 42, 'kittens'
+dummy($params...)

// Yep
$params: ( 'c': 'kittens', 'a': true, 'b': 42, )
+dummy($params...)
{% endhighlight %}
  </div>
</div>



### Дальнейшее чтение

* [Sass Multiple Arguments, Lists or Arglist](http://www.sitepoint.com/sass-multiple-arguments-lists-or-arglist/)






## Mixins and vendor prefixes

It might be tempting to define custom mixins to handle vendor prefixes for unsupported or partially supported CSS properties. But we do not want to do this. First, if you can use [Autoprefixer](https://github.com/postcss/autoprefixer), use Autoprefixer. It will remove Sass code from your project, will always be up-to-date and will necessarily do a much better job than you at prefixing stuff.

Unfortunately, Autoprefixer is not always an option. If you use either [Bourbon](http://bourbon.io/) or [Compass](http://compass-style.org/), you may already know that they both provide a collection of mixins that handle vendor prefixes for you. Use those.

If you cannot use Autoprefixer and use neither Bourbon nor Compass, then and only then, you can have your own mixin for prefixing CSS properties. But. Please do not build a mixin per property, manually printing each vendor.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Nope
@mixin transform($value) {
  -webkit-transform: $value;
  -moz-transform: $value;
  transform: $value;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Nope
=transform($value)
  -webkit-transform: $value
  -moz-transform: $value
  transform: $value
{% endhighlight %}
  </div>
</div>

Do it the clever way.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Mixin helper to output vendor prefixes
/// @access public
/// @author HugoGiraudel
/// @param {String} $property - Unprefixed CSS property
/// @param {*} $value - Raw CSS value
/// @param {List} $prefixes - List of prefixes to output
@mixin prefix($property, $value, $prefixes: ()) {
  @each $prefix in $prefixes {
    -#{$prefix}-#{$property}: $value;
  }

  #{$property}: $value;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Mixin helper to output vendor prefixes
/// @access public
/// @author HugoGiraudel
/// @param {String} $property - Unprefixed CSS property
/// @param {*} $value - Raw CSS value
/// @param {List} $prefixes - List of prefixes to output
=prefix($property, $value, $prefixes: ())
  @each $prefix in $prefixes
    -#{$prefix}-#{$property}: $value

  #{$property}: $value
{% endhighlight %}
  </div>
</div>

Then using this mixin should be very straightforward:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
.foo {
  @include prefix(transform, rotate(90deg), webkit ms);
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
.foo
  +prefix(transform, rotate(90deg), webkit ms)
{% endhighlight %}
  </div>
</div>

Please keep in mind this is a poor solution. For instance, it cannot deal with complex polyfills such as those required for Flexbox. In that sense, using Autoprefixer would be a far better option.



### Дальнейшее чтение

* [Autoprefixer](https://github.com/postcss/autoprefixer)
* [Building a Linear-Gradient Mixin](http://www.sitepoint.com/building-linear-gradient-mixin-sass/)











# Conditional statements

You probably already know that Sass provides conditional statements via the `@if` and `@else` directives. Unless you have some medium to complex logic in your code, there is no need for conditional statements in your everyday stylesheets. Actually, they mainly exist for libraries and frameworks.

Anyway, if you ever find yourself in need of them, please respect the following guidelines:

* No parentheses unless they are necessary;
* Always an empty new line before `@if`;
* Always a line break after the opening brace (`{`);
* `@else` statements on the same line as previous closing brace (`}`).
* Always an empty new line after the last closing brace (`}`) unless the next line is a closing brace (`}`).

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
@if $support-legacy {
  // ...
} @else {
  // ...
}

// Nope
@if ($support-legacy == true) {
  // ...
}
@else {
  // ...
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
@if $support-legacy
  // ...
@else
  // ...

// Nope
@if ($support-legacy == true)
  // ...
@else
  // ...
{% endhighlight %}
  </div>
</div>

When testing for a falsy value, always use the `not` keyword rather than testing against `false` or `null`.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
@if not index($list, $item) {
  // ...
}

// Nope
@if index($list, $item) == null {
  // ...
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
@if not index($list, $item)
  // ...

// Nope
@if index($list, $item) == null
  // ...
{% endhighlight %}
  </div>
</div>

When using conditional statements within a function to return a different result based on some condition, always make sure the function still has a `@return` statement outside of any conditional block.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
// Yep
@function dummy($condition) {
  @if $condition {
    @return true;
  }

  @return false;
}

// Nope
@function dummy($condition) {
  @if $condition {
    @return true;
  } @else {
    @return false;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
// Yep
@function dummy($condition)
  @if $condition
    @return true

  @return false;

// Nope
@function dummy($condition)
  @if $condition
    @return true
  @else
    @return false
{% endhighlight %}
  </div>
</div>











# Loops

Because Sass provides complex data structures such as [lists](#lists) and [maps](#maps), it is no surprise that it also gives a way for authors to iterate over those entities.

However, the presence of loops usually implies moderately complex logic that probably does not belong to Sass. Before using a loop, make sure it makes sense and that it actually solves an issue.






## Each

The `@each` loop is definitely the most-used out of the three loops provided by Sass. It provides a clean API to iterate over a list or a map.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@each $theme in $themes {
  .section-#{$theme} {
    background-color: map-get($colors, $theme);
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@each $theme in $themes
  .section-#{$theme}
    background-color: map-get($colors, $theme)
{% endhighlight %}
  </div>
</div>

When iterating on a map, always use `$key` and `$value` as variable names to enforce consistency.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@each $key, $value in $map {
  .section-#{$key} {
    background-color: $value;
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@each $key, $value in $map
  .section-#{$key}
    background-color: $value
{% endhighlight %}
  </div>
</div>

Also be sure to respect those guidelines to preserve readability:

* Always an empty new line before `@each`;
* Always an empty new line after the closing brace (`}`) unless the next line is a closing brace (`}`).






## For

The `@for` loop might be useful when combined with CSS' `:nth-*` pseudo-classes. Except for these scenarios, prefer an `@each` loop if you *have to* iterate over something.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@for $i from 1 through 10 {
  .foo:nth-of-type(#{$i}) {
    border-color: hsl($i * 36, 50%, 50%);
  }
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@for $i from 1 through 10
  .foo:nth-of-type(#{$i})
    border-color: hsl($i * 36, 50%, 50%)
{% endhighlight %}
  </div>
</div>

Always use `$i` as a variable name to stick to the usual convention and unless you have a really good reason to, never use the `to` keyword: always use `through`. Many developers do not even know Sass offers this variation; using it might lead to confusion.

Also be sure to respect those guidelines to preserve readability:

* Always an empty new line before `@each`;
* Always an empty new line after the closing brace (`}`) unless the next line is a closing brace (`}`).






## While

The `@while` loop has absolutely no use case in a real Sass project, especially since there is no way to break a loop from the inside. **Do not use it**.











# Warnings and Errors

If there is a feature that is often overlooked by Sass developers, it is the ability to dynamically output warnings and errors. Indeed, Sass comes with three custom directives to print content in the standard output system (CLI, compiling app...):

* `@debug`;
* `@warn`;
* `@error`.

Let's put `@debug` aside since it is clearly intended to debug SassScript, which is not our point here. We are then left with `@warn` and `@error` which are noticeably identical except that one stops the compiler while the other does not. I'll let you guess which does what.

Now, there is a lot of room in a Sass project for warnings and errors. Basically any mixin or function expecting a specific type or argument could throw an error if something went wrong, or display a warning when doing an assumption.



### Дальнейшее чтение

* [An Introduction To Error Handling](http://webdesign.tutsplus.com/tutorials/an-introduction-to-error-handling-in-sass--cms-19996)
* [Building a Logger Mixin](http://webdesign.tutsplus.com/tutorials/building-a-logger-mixin-in-sass--cms-22070)
* [SassyLogger](https://github.com/HugoGiraudel/SassyLogger)






## Warnings

Take this function from [Sass-MQ](https://github.com/sass-mq/sass-mq) attempting to convert a `px` value to `em`, for instance:

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
@function mq-px2em($px, $base-font-size: $mq-base-font-size) {
  @if unitless($px) {
    @warn 'Assuming #{$px} to be in pixels, attempting to convert it into pixels.';
    @return mq-px2em($px + 0px);
  } @else if unit($px) == em {
    @return $px;
  }

  @return ($px / $base-font-size) * 1em;
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
@function mq-px2em($px, $base-font-size: $mq-base-font-size)
  @if unitless($px)
    @warn 'Assuming #{$px} to be in pixels, attempting to convert it into pixels.'
    @return mq-px2em($px + 0px)
  @else if unit($px) == em
    @return $px

  @return ($px / $base-font-size) * 1em
{% endhighlight %}
  </div>
</div>

If the value happens to be unitless, the function assumes the value is meant to be expressed in pixels. At this point, an assumption may be risky so the user should be warned that the software did something that could be considered unexpected.






## Errors

Errors, unlike warnings, prevent the compiler from going any further. Basically, they stop the compilation and display a message in the output stream as well as the stack trace, which is handy for debugging. Because of this, errors should be thrown when there is no way for the program to keep running. When possible, try to work around the issue and display a warning instead.

As an example, let's say you build a getter function to access values from a specific map. You could throw an error if the requested key does not exist in the map.

<div class="code-block">
  <div class="code-block__wrapper" data-syntax="scss">
{% highlight scss %}
/// Z-indexes map, gathering all Z layers of the application
/// @access private
/// @type Map
/// @prop {String} key - Layer's name
/// @prop {Number} value - Z value mapped to the key
$z-indexes: (
  'modal': 5000,
  'dropdown': 4000,
  'default': 1,
  'below': -1,
);

/// Get a z-index value from a layer name
/// @access public
/// @param {String} $layer - Layer's name
/// @return {Number}
/// @require $z-indexes
@function z($layer) {
  @if not map-has-key($z-indexes, $layer) {
    @error 'There is no layer named `#{$layer}` in $z-indexes. '
         + 'Layer should be one of #{map-keys($z-indexes)}.';
  }

  @return map-get($z-indexes, $layer);
}
{% endhighlight %}
  </div>
  <div class="code-block__wrapper" data-syntax="sass">
{% highlight sass %}
/// Z-indexes map, gathering all Z layers of the application
/// @access private
/// @type Map
/// @prop {String} key - Layer's name
/// @prop {Number} value - Z value mapped to the key
$z-indexes: ('modal': 5000, 'dropdown': 4000, 'default': 1, 'below': -1,)

/// Get a z-index value from a layer name
/// @access public
/// @param {String} $layer - Layer's name
/// @return {Number}
/// @require $z-indexes
@function z($layer)
  @if not map-has-key($z-indexes, $layer)
    @error 'There is no layer named `#{$layer}` in $z-indexes. '
         + 'Layer should be one of #{map-keys($z-indexes)}.'

  @return map-get($z-indexes, $layer)
{% endhighlight %}
  </div>
</div>











# Tools

What's nice about a CSS preprocessor as popular as Sass is that it comes with a whole ecosystem of frameworks, plugins, libraries and tools. After 8 years of existence, we are getting closer and closer to the point where [everything that can be written in Sass has been written in Sass](http://hugogiraudel.com/2014/10/27/rethinking-atwoods-law/).

However my advice would to be to lower the number of dependencies to the strict minimum. Managing dependencies is some sort of hell you don't want to be part of. Plus, there is little to no need for external dependencies when it comes to Sass.






## Compass

[Compass](http://compass-style.org/) is the main Sass framework out there. Developed by [Chris Eppstein](https://twitter.com/chriseppstein), one of the two core designers of Sass, I don't see it dramatically losing in popularity for a while, if you want my opinion.

Still, I do not use Compass anymore, the main reason is that it slows Sass down a lot. Ruby Sass is quite slow in itself, so adding more Ruby and more Sass on top of it doesn't really help.

The thing is, we use very little from the whole framework. Compass is huge. Cross-browser compatibility mixins is just the tip of the iceberg. Math functions, image helpers, spriting... There is so much that can be done with this great piece of software.

Unfortunately, this is all sugar and there is no killer feature in there. An exception could be made of the sprite builder which is *really great*, but [Grunticon](https://github.com/filamentgroup/grunticon) and [Grumpicon](http://grumpicon.com/) do the job as well, and have the benefit of being pluggable in the build process.

Anyway, I do not forbid the use of Compass although I would not recommend it either, especially since it is not LibSass-compatible (even if efforts have been made in that direction). If you feel better using it, fair enough, but I don't think you'll get much from it at the end of the day.

<div class="note">
  <p>Ruby Sass is currently going under some outstanding optimizations that are specifically targeted at logic-heavy styles with many functions and mixins. They should dramatically improve performance to the point where Compass and other frameworks might not be slowing Sass anymore.</p>
</div>



### Дальнейшее чтение

* [Compass](http://compass-style.org/)
* [Sass Frameworks: Compass or Bourbon](http://www.sitepoint.com/compass-or-bourbon-sass-frameworks/)
* [Is Compass to Sass with jQuery is to JavaScript?](http://www.sitepoint.com/compass-sass-jquery-javascript/)






## Grid systems

Not using a grid system is not an option now that Responsive Web Design is all over the place. To make designs look consistent and solid across all sizes, we use some sort of grid to lay out the elements. To avoid having to code this grid work over and over again, some brilliant minds made theirs reusable.

Let me put this straight: I am not a big fan of grid systems. Of course I do see the potential, but I think most of them are completely overkill and are mostly used to draw red columns on a white background in nerdy designers' speaker decks. When is the last time you thought *thank-God-I-have-this-tool-to-build-this-2-5-3.1-π-grid*? That's right, never. Because in most cases, you just want the usual regular 12-columns grid, nothing fancy.

If you are using a CSS framework for your project like [Bootstrap](http://getbootstrap.com/) or [Foundation](http://foundation.zurb.com/), chances are high it includes a grid system already in which case I would recommend to use it to avoid having to deal with yet another dependency.

If you are not tied to a specific grid system, you will be pleased to know there are two top-notch Sass powered grid engines out there: [Susy](http://susy.oddbird.net/) and [Singularity](http://singularity.gs/). Both do much more than you will ever need so you can pick the one you prefer between these two and be sure all your edge cases&mdash;even the most nifty ones&mdash;will be covered. If you ask me, Susy has a slightly better community, but that's my opinion.

Or you can head over to something a bit more casual, like [csswizardry-grids](https://github.com/csswizardry/csswizardry-grids). All in all, the choice will not have much of an impact on your coding style, so this is pretty much up to you at this point.



### Дальнейшее чтение

* [Singularity](http://singularity.gs/)
* [Singularity: Grids Without Limits](http://fourword.fourkitchens.com/article/singularity-grids-without-limits)
* [Singularity Grid System](http://www.mediacurrent.com/blog/singularity-grid-system)
* [Susy](http://susy.oddbird.net/)
* [Build Web Layouts Easily with Susy](http://css-tricks.com/build-web-layouts-easily-susy/)
* [A Complete Tutorial to Susy 2](http://www.zell-weekeat.com/susy2-tutorial/)
* [Sass Grids: From Neat to Susy](http://www.sitepoint.com/sass-grids-neat-susy/)
* [Bootstrap's Grid System vs Susy: a Comparison](http://www.sitepoint.com/bootstraps-grid-system-vs-susy-comparison/)
* [How to Use Susy: Superpowered Sass Grids](http://webdesign.tutsplus.com/tutorials/how-to-use-susy-superpowered-sass-grids--cms-22744)
* [A Creative Grid System with Sass and calc()](http://www.sitepoint.com/creative-grid-system-sass-calc/)






## SCSS-lint

Linting code is very important. Usually, following guidelines from a styleguide helps reducing the amount of code quality mistakes but nobody's perfect and there are always things to improve. So you could say that linting code is as important as commenting it.

[SCSS-lint](https://github.com/causes/scss-lint) is a tool to help you keep your SCSS files clean and readable. It is fully customisable and easy to integrate with your own tools.

Fortunately, SCSS-lint recommendations are very similar to those described in this document. In order to configure SCSS-lint according to Sass Guidelines, may I recommend the following setup:

{% highlight yaml %}
# For SCSS-Lint v0.32.0

linters:

  BangFormat:
    enabled: true
    space_before_bang: true
    space_after_bang: false

  BorderZero:
    enabled: true

  ColorKeyword:
    enabled: false

  Comment:
    enabled: false

  DebugStatement:
    enabled: true

  DeclarationOrder:
    enabled: true

  DuplicateProperty:
    enabled: false

  ElsePlacement:
    enabled: true
    style: same_line

  EmptyLineBetweenBlocks:
    enabled: true
    ignore_single_line_blocks: false

  EmptyRule:
    enabled: true

  FinalNewline:
    enabled: true
    present: true

  HexLength:
    enabled: true
    style: short

  HexNotation:
    enabled: true
    style: lowercase

  HexValidation:
    enabled: true

  IdSelector:
    enabled: true

  ImportPath:
    enabled: true
    leading_underscore: false
    filename_extension: false

  Indentation:
    enabled: true
    character: space
    width: 2

  LeadingZero:
    enabled: true
    style: include_zero

  MergeableSelector:
    enabled: false
    force_nesting: false

  NameFormat:
    enabled: true
    convention: hyphenated_lowercase
    allow_leading_underscore: true

  NestingDepth:
    enabled: true
    max_depth: 3

  PlaceholderInExtend:
    enabled: true

  PropertySortOrder:
    enabled: false
    ignore_unspecified: false

  PropertySpelling:
    enabled: true
    extra_properties: []

  QualifyingElement:
    enabled: true
    allow_element_with_attribute: false
    allow_element_with_class: false
    allow_element_with_id: false

  SelectorDepth:
    enabled: true
    max_depth: 3

  SelectorFormat:
    enabled: true
    convention: hyphenated_lowercase
    class_convention: '^(?:u|is|has)\-[a-z][a-zA-Z0-9]*$|^(?!u|is|has)[a-zA-Z][a-zA-Z0-9]*(?:\-[a-z][a-zA-Z0-9]*)?(?:\-\-[a-z][a-zA-Z0-9]*)?$'

  Shorthand:
    enabled: true

  SingleLinePerProperty:
    enabled: true
    allow_single_line_rule_sets: false

  SingleLinePerSelector:
    enabled: true

  SpaceAfterComma:
    enabled: true

  SpaceAfterPropertyColon:
    enabled: true
    style: one_space

  SpaceAfterPropertyName:
    enabled: true

  SpaceBeforeBrace:
    enabled: true
    style: space
    allow_single_line_padding: true

  SpaceBetweenParens:
    enabled: true
    spaces: 0

  StringQuotes:
    enabled: true
    style: single_quotes

  TrailingSemicolon:
    enabled: true

  TrailingZero:
    enabled: true

  UnnecessaryMantissa:
    enabled: true

  UnnecessaryParentReference:
    enabled: true

  UrlFormat:
    enabled: false

  UrlQuotes:
    enabled: true

  VendorPrefixes:
    enabled: true
    identifier_list: base
    include: []
    exclude: []

  ZeroUnit:
    enabled: true
{% endhighlight %}

<div class="note">
  <p>If you want to plug SCSS lint into your Grunt build process, you will be pleased to know there is a Grunt plugin for that called <a href="https://github.com/ahmednuaman/grunt-scss-lint">grunt-scss-lint</a>.</p>
  <p>Also, if you are on the hunt for a neat application that works with SCSS-lint and the like, the guys at <a href="http://thoughtbot.com/">Thoughtbot</a> (Bourbon, Neat...) are working on <a href="https://houndci.com/">Hound</a>.</p>
</div>



### Дальнейшее чтение

* [SCSS-lint](https://github.com/causes/scss-lint)
* [Clean Up your Sass with SCSS-lint](http://blog.martinhujer.cz/clean-up-your-sass-with-scss-lint/)
* [Improving Sass code quality on theguardian.com](http://www.theguardian.com/info/developer-blog/2014/may/13/improving-sass-code-quality-on-theguardiancom)
* [grunt-scss-lint](https://github.com/ahmednuaman/grunt-scss-lint)
* [An Auto-Enforceable SCSS Styleguide](http://davidtheclark.com/scss-lint-styleguide/)









# Too Long; Didn't read

To sum up, we want:

* Two (2) spaces indents, no tabs;
* 80-characters wide lines;
* Properly written multi-line CSS;
* Meaningful use of whitespaces;
* Quoted strings (single quotes) & URLs;
* No trailing 0, mandatory leading 0;
* Calculations wrapped in parentheses;
* No magic numbers;
* Colors expressed in keywords > HSL > RGB > hexadecimal;
* Lists separated with commas;
* No trailing comma in lists (since they are inlined);
* Trailing comma in maps;
* No selector nesting except for pseudo-classes and pseudo-elements;
* Hyphen-delimited naming;
* Extensive comments;
* SassDoc-powered API comments;
* Limited usage of `@extend`;
* Simple mixins;
* As few loops as possible, no `@while`;
* Reduced number of dependencies;
* Meaningful use of warnings and errors.

{% include donate.html %}
