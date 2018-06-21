<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/3603793/15085619/b7b0423a-13b1-11e6-8e47-e8ed523f6ff6.png" width="200">
</p>

Стиль кода от LFeh
============

> "Каждая линия кода должна быть написана так, будто её писал лишь один человек, вне зависимости от количества разработчиков." - Китайская народная пословица.

Этот документ описывает правила написания кода для языков, которые я использую: HTML, CSS и Javascript.

Этот репозиторий не был задуман как целый проект для описания моего стиля кода. Я лишь хотел поместить её сюда для себя и для других разработчиков, участвующих в моих проектах, чтобы информировать их о стандартах, которые я использую.

Так как это новый документ, некоторые участки кода в старых проектах могут не соответствовать данным правилам.

Этот документ постоянно обновляется и время от времени могут появляться изменения

## Содержание

1. [Git](#commits)
1. [HTML](#html)
1. [Jade](#jade)
1. [CSS](#css)
1. [CSS-препроцессоры](#css-preprocessors)
1. [Javascript](#js)
1. [Стартовый шаблон](#js)
1. [Ссылки](#references)
1. [Переводы](#translations)
1. [Лицензия](#license)

<a name="commits"></a>
## 1. Git

Для облегчения содействия других людей в проектах, все описания commit'ов, названия pull request'ов или записей о багах должны быть написаны на **Английском языке**

Прежде чем commit'ить что-либо, нужно проверять, нет ли других commit'ов с таким названием. Если такие есть, писать номер исправления после символа #

```javascript
// Правильно
git commit -m "Add placeholder in input #10"

// Неправильно
git commit -m "Add placeholder in input"
```

<a name="html"></a>
## 2. HTML

Основы раздела про HTML взяты с ["Code Guide by @mdo"](https://github.com/mdo/code-guide).

### Оглавление HTML

1. [Синтаксис HTML](#html-syntax)
1. [Комментарии HTML](#html-comments)
1. [Кодировка документов HTML](#html-encoding)
1. [Порядок аттрибутов в HTML](#html-attribute-order)
1. [Производительность HTML-кода](#html-performance)
1. [Базовый шаблон HTML-кода](#html-base)

<a name="html-syntax"></a>
### 2.1. Синтаксис HTML

Используйте мягкую табуляцию (soft tabs) размером в два пробела. Это настраивается в редакторе кода.

```html
<!-- Правильно -->
<nav class="nav">
  <ul class="nav-menu">
    <li class="nav-item">
      <a class="nav-link">

<!-- Неправильно -->
<nav class="nav">
      <ul class="nav-menu">
            <li class="nav-item">
                  <a class="nav-link">
```

Всегда используйте двойные кавычки в HTML.

```html
<!-- Правильно -->
<div class="main">

<!-- Неправильно -->
<div class='main'>
```

Не включайте символ '/' в самозакрывающиеся теги.

```html
<!-- Правильно -->
<hr>

<!-- Неправильно -->
<hr />
```

Разделяйте блочные элементы пустой строкой и группируйте внутренние элементы блоков

```html
<!-- Правильно -->
<ul class="nav-tabs">
  <li>...</li>
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ul>

<div class="tab-content">
  ...
</div>

<!-- Неправильно -->
<ul class="nav-tabs">

  <li>...</li>

  <li>...</li>

  <li>...</li>

  <li>...</li>

</ul>
<div class="tab-content">
  ...
</div>
```

<a name="html-comments"></a>
### 2.2. Комментарии в HTML

Следуйте этому правилу при написании комментариев:

```html
<!-- Пример комментариев в HTML -->
<!-- /Конец примера комментариев в HTML -->
```

<a name="html-encoding"></a>
### 2.3. Кодировка HTML-документов

Всегда используйте кодировку UTF-8 в документах.

```html
<head>
  <meta charset="UTF-8">
</head>
```

<a name="html-attribute-order"></a>
### 2.4. Порядок атрибутов в HTML

Атрибуты в HTML должны следовать данному порядку для облегчения чтения кода.

1. `class`
1. `id`, `name`
1. `data-*`
1. `src`, `for`, `type`, `href`
1. `title`, `alt`
1. `aria-*`, `role`

```html
<a class="..." id="..." data-modal="toggle" href="#">

<input class="form-control" type="text">

<img class="img-rounded" src="..." alt="...">
```

<a name="html-performance"></a>
### 2.5. Производительность HTML

Нет необходимости указывать тип CSS и JS файлов в атрибуте type, такие как `text/css` и `text/javascript`.

```html
<!-- Правильно -->
<link rel="stylesheet" href="assets/css/style.css" />
<script src="scripts.min.js"></script>

<!-- Не правильно -->
<script src="scripts.min.js"></script>
</head>
<body>
```

Для увеличения скорости загрузки страницы указывайте ссылки на Javascript-скрипты перед закрывающим тегом `<body>`.

```html
<!-- Правильно -->
<script src="scripts.min.js"></script>
</body>

<!-- Не правильно -->
<script src="scripts.min.js"></script>
</head>
<body>
```

Всегда сокращайте код в проектах на чистом HTML. Таск-менеджеры, вроде [Gulp](http://gulpjs.com/) упрощают эту задачу.

```html
<!-- Правильно -->
<html><head>...</head><body><div class="container">...</div></body></html>

<!-- Неправильно -->
<html>
  <head>
    ...
  </head>
  <body>
    <div class="container">
      ...
    </div>
  </body>
</html>
```

<a name="html-base"></a>
### 2.6. Базовый шаблон HTML-документа

Этот код следует использовать для быстрого начала работы над новым проектом:

```html
<!DOCTYPE html>
<html lang="en">
<head>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="format-detection" content="telephone=no">
<meta name="viewport" content="width=device-width">

<link rel="shortcut icon" href="assets/img/ico/favicon.ico" />
<link rel="logo" type="image/svg" href="../assets/img/logo/logo.svg" />
<link rel="stylesheet" href="assets/css/style.css" />

<title></title>

</head>
<body>

<!-- Скрипты -->
<script src="assets/js/scripts.min.js"></script>

</body>
</html>
```

Немного совместимости с IE...

```html
<!DOCTYPE html>
<!--[if IE]><![endif]-->
<!--[if IE 7 ]> <html lang="en" class="ie7">    <![endif]-->
<!--[if IE 8 ]>    <html lang="en" class="ie8">    <![endif]-->
<!--[if IE 9 ]>    <html lang="en" class="ie9">    <![endif]-->
<!--[if (gt IE 9)|!(IE)]><!--><html lang="en"><!--<![endif]-->
<head>
...
```

<a name="jade"></a>
## 3. Jade

Сейчас я (автор) использую Jade как шаблонизатор.

### Разделы по Jade

1. [Синтаксис Jade](#jade-syntax)
1. [Комментарии Jade](#jade-comments)
1. [Стартовый шаблон на Jade](#jade-base)

<a name="jade-syntax"></a>
### 3.1. Синтаксис Jade

Аналогично с HTML, используйте мягкие табы размером в два пробела. Настраивается в вашем редакторе.

```javascript
//- Правильно
nav.navbar
  ul.nav
    li.nav-item
      a.nav-link

//- Неправильно
nav.navbar
    ul.nav
        li.nav-item
            a.nav-link
```

Всегда используйте *одинарные* кавычки.

```javascript
//- Правильно
button.btn(data-toggle='collapse')

//- Неправильно
button.btn(data-toggle="collapse")
```
 
Напишите заголовок блока, разделяйте блочные элементы **двумя** чистыми линиями и группируйте внутренние элементы блока.

```javascript
//- Правильно
 
//- Header
//- ===================================
header.header(role='banner')
  a.logo(href='#', role='logo')


//- Main
//- ===================================
main.main(role='main')
  section.content
 
//- Неправильно
header.header(role='banner')
  a.logo(href='#', role='logo') 
main.main(role='main') 
  section.content
```

<a name="jade-comments"></a>
### 3.2. Комментарии Jade

При добавлении комментариев следуйте этому правилу

```javascript
//- Это пример правильного комментария 

// А это пример неправильного
```

Комментарии с `//-` в начале не компилируются в HTML.
  
<a name="jade-base"></a>
### 3.3. Стартовый шаблон на Jade

Код далее помогает быстро стартовать проект

```javascript
doctype html
html(lang='en')
  head 
    meta(charset='utf-8')
    meta(name='description', content='')
    meta(name='viewport', content='width=device-width, initial-scale=1')
    meta(name='format-detection', content='telephone=no')

    //- Title
    //- ===================================
    title Заголовок страницы

    //- Favicon and SVG logo
    //- ===================================
    link(rel='shortcut icon', href='ico/favicon.ico')  
    link(rel='logo', type='image/svg', href='svg/logo/logo.svg')

    //- Stylesheet and fonts
    //- ===================================
    link(href='css/style.css', rel='stylesheet')  

  body 
 
    //- Scripts
    //- ===================================
    script(src='js/scripts.min.js') 
```

<a name="css"></a>
## 4. CSS

Основы раздела про CSS взяты с [Code Guide by @mdo](https://github.com/mdo/code-guide) и ["Разговорный CSS"](https://github.com/necolas/idiomatic-css/).

### Оглавление CSS

1. [Синтаксис CSS](#css-syntax)
1. [Порядок обьявления в CSS](#css-order)
1. [Имена классов в CSS](#css-class-name)
1. [Производительность CSS](#css-performance)
1. [Адаптивность и @media-запросы](#mobile-first-and-media-queries)

<a name="css-syntax"></a>
### 4.1. Синтаксис

Используйте мягкую табуляцию размером в два символа пробела. Это настраивается в редакторе кода.

```css
/* Правильно */
.nav-item {
  display: inline-block;
  margin: 0 5px;
}

/* Неправильно */
.nav-item {
    display: inline-block;
    margin: 0 5px;
}
```

Всегда используйте двойные кавычки.

```css
/* Правильно */
[type="text"]
[class^="..."]

.nav-item:after {
  content: "";
}

/* Неправильно */
[type='text']
[class^='...']

.nav-item:after {
  content: '';
}
```

Всегда вставляйте один пробел перед символом фигурной скобки

```css
/* Правильно */
.header {
  ...
}

/* Неправильно */
.header{
  ...
}
```

После двоеточия объявления свойства также вставляйте один пробел

```css
/* Правильно */
.header {
  margin-bottom: 20px;
}

/* Неправильно */
.header{
  margin-bottom:20px;
}
```

В блоке объявлений свойств после каждого свойства всегда вставляйте точку с запятой

```css
/* Правильно */
.header {
  margin-bottom: 20px;
}

/* Неправильно */
.header{
  margin-bottom:20px
}
```

Каждый селектор при его объявлении пишите на отдельной строке

```css
/* Правильно */
.selector-1,
.selector-2,
.selector-3 {
  ...
}

/* Неправильно */
.selector-1, .selector-2, .selector-3 {
  ...
}
```

Обьявления селекторов с единственным свойством пишите вместе со свойством на одной строке

```css
/* Правильно */
.selector-1 { width: 50%; }

/* Неправильно */
.selector-1 {
  width: 50%;
}
```

Разделяйте каждое объявление селектора пустой строкой.

```css
/* Правильно */
.selector-1 {
  ...
}

.selector-2 {
  ...
}

/* Неправильно */
.selector-1 {
  ...
}
.selector-2 {
  ...
}
```

Используйте нижний регистр и сокращения для обозначения шестнадцетиричных цветов

Не пишите обозначений для нулевых величин.

```css
/* Правильно */
.selector-1 {
  color: #aaa;
  margin: 0;
}

/* Неправильно */
.selector-1 {
  color: #AAAAAA;
  margin: 0px;
}
```

<a name="css-order"></a>
### 4.2. Порядок объявлений в CSS

Объявления свойств должны идти в алфавитном порядке

```css
/* Правильно */
.selector-1 {
  background: #fff;
  border: #333 solid 1px;
  color: #333;
  display: block;
  height: 200px;
  margin: 5px;
  padding: 5px;
  width: 200px;
}

/* Неправильно */
.selector-1 {
  padding: 5px;
  height: 200px;
  background: #fff;
  margin: 5px;
  width: 200px;
  color: #333;
  border: #333 solid 1px;
  display: block;
}
```

<a name="css-class-name"></a>
### 4.3. Имена классов в CSS

Используйте только нижний регистр и вставляйте дефисы между словами

```css
/* Правильно */
.nav-item { ... }

/* Неправильно */
.NavItem { ... }
.nav_item { ... }
```

Дефисы также необходимы для того, чтобы показать принадлежность одного селектора к другому. Префиксами можно подписывать селекторы родителей для удобного чтения кода.

```css
/* Правильно */
.navbar { ... }
.nav { ... }
.nav-item { ... }
.nav-link { ... }

/* Неправильно */
.item-nav { ... }
.link-nav { ... }
```

Избегайте слишком коротких имён селекторов и всегда выбирайте пододящие по смыслу имена

```css
/* Правильно */
.btn { ... }
.page-header { ... }
.progress-bar { ... }

/* Неправильно */
.s { ... }
.ph { ... }
.block { ... }
```

<a name="css-performance"></a>
### 4.4. Производительность CSS

Никогда не используйте идентификаторы.

```css
/* Правильно */
.header { ... }
.section { ... }

/* Неправильно */
#header { ... }
#section { ... }
```

Всегда отдавайте предпочтения классам, а не названиям тегов или другим стандартным селекторам

```css
/* Правильно */
.form-control { ... }
.header { ... }
.section { ... }

/* Неправильно */
input[type="text"] { ... }
header
section
```

Избегайте вложенных элементов, используйте вместо них отдельные классы

```css
/* Правильно */
.navbar { ... }
.nav { ... }
.nav-item { ... }
.nav-link { ... }

/* Неправильно */
.navbar ul { ... }
.navbar ul li { ... }
.navbar ul li a { ... }
```

Используйте селекторы со вложенностью только когда нужно поменять свойства класса в зависимости от его вложенности в другие классы. Не углубляйтесь дальше трёх селекторов

```css
/* Правильно */
.modal-footer .btn { ... }
.progress.active .progress-bar { ... }

/* Неправильно */
.modal-btn { ... }
.progress.active .progress-bar .progress-item span { ... }
```

Сокращайте CSS-код. Таск-менеджеры, такие как [Gulp](http://gulpjs.com/) упрощают это.

```css
/* Правильно */
.navbar { ... }.nav { ... }.nav-item { ... }.nav-link { ... }

/* Неправильно */
.nav-item {
  ...
}
.nav-link {
  ...
}
```

<a name="mobile-first-and-media-queries"></a>
### 4.5 Адаптивность и @media-запросы

Начинайте разработку с введения основных правил и @media-запросов для разработки с паттерном mobile-first.

```css
/* Правильно */
.navbar {
  margin-bottom: 20px;
}

@media (min-width: 480px) {
  .navbar {
    padding: 10px;
  }
}

@media (min-width: 768px) {
  .navbar {
    position: absolute;
    top: 0;
    left: 0;
  }
}

@media (min-width: 992px) {
  .navbar {
    position: fixed;
  }
}

/* Неправильно */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
}

@media (max-width: 767px) {
  .navbar {
    position: static;
    padding: 10px;
  }
}

```

Держите @media-запросы как можно ближе к тому правилу, к которому они относятся. Не выделяйте их в отдельную таблицу стилей или в конец документа

```css
.navbar { ... }
.nav { ... }
.nav-item { ... }

@media (min-width: 480px) {
  .navbar { ... }
  .nav { ... }
  .nav-item { ... }
}
```

<a name="css-preprocessors"></a>
### 5. Препроцессоры

Во всех своих проектах я (автор) использую препроцессоры. Сейчас я перешёл на Stylus, но в некоторых проектах ещё используется `LESS`.

### Оглавление по CSS-препроцессорам

1. [Синтаксис CSS-препроцессоров](#preprocessors-syntax)  
1. [Производительность CSS-препроцессоров](#preprocessors-performance) 
1. [Медиазапросы в препроцессорах](#preprocessors-media-queries) 
1. [Комментарии в CSS-препроцессорах](#preprocessors-comments)


<a name="preprocessors-syntax"></a>
### 5.1. Синтаксис CSS-препроцессоров

Используйте мягкую табуляцию размером в два символа пробела. Это настраивается в редакторе кода.

```css
// Правильно
.nav-item 
  display inline-block  

// Неправильно
.nav-item 
    display inline-block  
```

Не используйте символы ";", ":" и фигурные скобки

```css
// Правильно
.header 
  position fixed
  top 0
  right 0
  left 0

// Неправильно
.header {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
}
``` 

Каждый селектор объявляйте на отдельной строке.

```css
// Правильно
.selector-1,
.selector-2,
.selector-3 
  ...
 

// Неправильно
.selector-1, .selector-2, .selector-3 
  ... 
``` 

Разделяйте вложенные правила пустыми строками, а блоки разделяйте двумя пустыми строками.

```css
// Правильно
.navbar 
  margin 0 0 20px

  li 
    display inline-block


.nav 
  display block

  li 
    float left


// Неправильно
.navbar 
  margin 0 0 20px 
  li 
    display inline-block 
.nav 
  display block 
  li 
    float left
``` 

Используйте **$** для переменных.

```css
// Правильно
$gray-darker  = #111
$gray-dark    = #393C45
$gray         = #555
$gray-light   = #aaa
$gray-lighter = #ECF1F5
$gray-white   = #fbfbfb
```

<a name="preprocessors-performance"></a>
### 5.2. Производительность CSS-препроцессоров

Держитесь подальше от вложенностей, как и в чистом CSS

```css
// Правильно
.nav-item 
  ...

// Неправильно
.navbar 
  .nav 
    .nav-item 
      ... 
```

**Не используйте @extend'ы**, [Всегда пользуйтесь миксинами](http://csswizardry.com/2016/02/mixins-better-for-performance/).

```css
reset(arg = '')
  
  if (arg == list) 
    margin 0
    padding-left 0
    list-style none
    
  if (arg == form)  
    background 0
    border 0
    padding 0

.nav
  reset(list)

.btn
  reset(form)
```
 
<a name="preprocessors-media-queries"></a>
### 5.3. Медиазапросы в препроцессорах

Пишите медиазапросы для элементов прямо внутри них

```css 
.navbar 
  position absolute
  top 5px
  z-index 5
   
  @media (min-width $screen-sm) 
    position fixed
    margin-right $space-sm
  
  @media (min-width $screen-md)  
    right 0 
    top 10px 
```
 
<a name="preprocessors-comments"></a>
### 5.4. Комментарии в CSS-препроцессорах

Предоставляйте оглавление в начале каждого файла.

```css 
//  
// Variables
//
// 1. Colors
// 2. Spaces 
// 3. Media Queries 
// 4. Typography
//
// ===============================================================

// 
// 1. Colors
// --------------------------------------------------

...

// 
// 2. Spaces
// --------------------------------------------------

...
```

Для главных элементов

```css  
// 
// 1. Header
// -------------------------------------------------- 
... 
```

Для подэлементов

```css   
// 1.1 Header Item
// -------------------------------------------------- 
...
```

Обычные комментарии

```css   
// Простой комментарий

// Блочный
// комментарий
...
``` 

<a name="js"></a>
## 6. Javascript

Основой этой части документа стали: ["idiomatic.js"](https://github.com/rwldrn/idiomatic.js/) и ["Zeno Rocha Coding Style"](https://github.com/zenorocha/my-coding-style/).

### Оглавление Javascript

1. [Синтаксис Javascript](#js-syntax)
1. [Переменные Javascript](#js-variables)
1. [Производительность Javascript-кода](#js-performance)
1. [JS и data-атрибуты HTML5](#js-data-attributes)
1. [Комментарии в Javascript](#js-comments)

<a name="js-syntax"></a>
### 6.1. Синтаксис Javascript

Используйте мягкую табуляцию размером в два символа пробела. Это настраивается в редакторе кода.

```js
// Правильно
while (condition) {
  statements
}

// Неправильно
while (condition) {
    statements
}
```

Всегда прописывайте точку с запятой в конце строки.

```js
// Правильно
var me = $(this);
test();

// Неправильно
var me = $(this)
test()
```

Всегда используйте одинарные кавычки

```js
// Правильно
var string = '<p class="foo">Lorem Ipsum</p>';
var noteClick = me.attr('data-note');

// Неправильно
var string = "<p class='foo'>Lorem Ipsum</p>";
var noteClick = me.attr("data-note");
```

Пишите `else` на той же строке, что и закрывающая фигурная скобка блока инструкций выражения `if`.

```js
// Правильно
if ( true ) {
  ...
} else {
  ...
}

// Неправильно
if ( true ) {
  ...
}
else {
  ...
}
```

Добавляйте пробелы между операторами.

```js
// Правильно
for (i = 0; i < 10; i++) {
  ...
}

// Неправильно
for (i=0;i<10;i++) {
  ...
}
```

Никогда не добавляйте пробелов после названия функции и перед её первым аргументом.

```js
// Правильно
foo(function() {
  ...
});

// Неправильно
foo ( function () {
  ...
});
```

Добавляйте пробелы за пределами круглых скобок, но избегайте пробелов внутри.

```js
// Правильно
if (condition) {
  statement
}

// Неправильно
if( condition ){
  statement
}
```

Для условных операторов if/else/else if всегда использовать фигурные скобки `{}`.

```js
// Правильно
if (condition) {
  statement
} else if (condition) {
  statement
} else {
  statement
}

// Неправильно
if (condition) statement;
else if (condition) statement;
else statement;
```

Проверка значений на равенство чаще всего должна быть строгой (`===`), нестрогую (`==`) использовать только в крайних случаях.

```js
// Правильно
if (foo === 'foo') {
  statement
}

// Неправильно
if (foo == 'foo') {
  statement
}
```

<a name="js-variables"></a>
### 6.2. Переменные Javascript

Все переменные перед использованием должны быть объявлены.

```js
// Правильно
var me = $(this);
var noteClick = me.attr('data-note');
notes[noteClick].play();

// Неправильно
notes[noteClick].play();
var me = $(this);
var noteClick = me.attr('data-note');
```

Всегда используйте `var` для объявления переменных.

```js
// Правильно
var me = $(this);

// Неправильно
me = $(this);
```

<a name="js-performance"></a>
### 6.3. Производительность Javascript-кода

Используйте [JSHint](http://www.jshint.com/) для выявления ошибок и проблем кода.

Всегда сокращайте и конкатенируйте весь Javascipt-код. Таск-менеджеры, такие как [Grunt](http://gruntjs.com/) упрощают этот процесс.

<a name="js-data-attributes"></a>
### 6.4. JavaScript and HTML5 Data Attributes

Избегайте использования классов в javascript-манипуляциях. Лучше используйте ***Data-атрибуты HTML5***.

```js
// Правильно
$('[data-toggle="tab"]');

// Неправильно
$('.tab');
```

Такой подход оставляет на классах всё, что связано со стилями.
Потому что некоторые элементы, стилизованные одинаково могут по-разному функционировать.

<a name="js-comments"></a>
### 6.5. Комментарии Javascript

Комментарий должен идти одной строкой над строкой комментируемого кода

```js
// Правильно
// Пример хорошего комментария
var me = $(this);

// Неправильно
var me = $(this); // Пример плохого комментария
```

<a name="boilerplate"></a>
## 7. Стартовый шаблон

Я (автор) сделал стартовый шаблон для этого code style.

<p>
  <img src="https://cloud.githubusercontent.com/assets/3603793/14390922/a999424c-fd8f-11e5-8fbb-ab908a1d4740.png" width="100">
</p>

Он называется [Kratos Boilerplate](https://github.com/LFeh/kratos-boilerplate).

<a name="references"></a>
## 8. Ссылки

* [Code Guide by @mdo](https://github.com/mdo/code-guide)
* [idiomatic CSS](https://github.com/necolas/idiomatic-css/)
* [idiomatic.js](https://github.com/rwldrn/idiomatic.js/)
* [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style/)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

<a name="translations"></a>
## 9. Переводы

* [Português (Brasil)](/translations/pt-BR/)
* [English (оригинал)](https://github.com/LFeh/coding-style)

<a name="license"></a>
## 10. Лицензия

[MIT License](http://felipefialho.mit-license.org/) © Luiz Felipe Tartarotti Fialho
