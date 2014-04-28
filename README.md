Стиль кода от LFeh
============

> "Каждая линия кода должна быть написана так, будто её писал лишь один человек, вне зависимости от количества разработчиков." - Китайская народная пословица.

Этот документ описывает правила написания кода для языков, которые я использую: HTML, CSS и Javascript.

Этот репозиторий не был задуман как целый проект для описания моего стиля кода. Я лишь хотел поместить её сюда для себя и для других разработчиков, участвующих в моих проектах, чтобы информировать их о стандартах, которые я использую.

Так как это новый документ, некоторые участки кода в старых проектах могут не соответствовать данным правилам.

Этот документ постоянно обновляется и время от времени могут появляться изменения

## Содержание

1. [Git] (#commits)
1. [HTML] (#html)
1. [CSS] (#css)
1. [Javascript] (#js)
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

Некоторые части раздела про HTML взяты с ["Code Guide by @mdo"](https://github.com/mdo/code-guide).

### Оглавление HTML

1. [Синтаксис HTML] (#html-syntax)
1. [Комментарии HTML] (#html-comments)
1. [Кодировка документов HTML] (#html-encoding)
1. [Порядок аттрибутов в HTML] (#html-attribute-order)
1. [Производительность HTML-кода] (#html-performance)
1. [Базовый шаблон HTML-кода] (#html-base)

<a name="html-syntax"></a>
### 2.1. Синтаксис HTML

Используйте мягкую табуляцию размером в два символа пробела. Это настраивается в редакторе кода.

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
### 2.3. Кодировка HTML-документво

Всегда используйте кодировку UTF-8 в документах.

```html
<head>
  <meta charset="UTF-8">
</head>
```

<a name="html-attribute-order"></a>
### 2.4. Порядок аттрибутов в HTML

Аттрибуты в HTML должны следовать данному порядку для облегчения чтения кода.

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

Нет необходимости указывать тип CSS и JS файлов в аттрибуте type, такие как `text/css` и `text/javascript`.

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

Всегда сокращайте код в проектах на чистом HTML. Таск-менеджеры, вроде [Grunt](http://gruntjs.com/) leaves this easier.

```html
<!-- Good -->
<html><head>...</head><body><div class="container">...</div></body></html>

<!-- Bad -->
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
### 2.6. HTML Base Code

The following code is a HTML base for faster start the projects.

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

<!-- Scripts -->
<script src="assets/js/scripts.min.js"></script>

</body>
</html>
```

For give support a olds Internet Explorer...

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

<a name="css"></a>
## 3. CSS

The main influences for the CSS rules are [Code Guide by @mdo](https://github.com/mdo/code-guide) and [idiomatic CSS](https://github.com/necolas/idiomatic-css/).

### CSS Summary

1. [CSS Syntax] (#css-syntax)
1. [CSS Declaration Order] (#css-order)
1. [CSS Class Name] (#css-class-name)
1. [CSS Performance] (#css-performance)
1. [Mobile First and Media Queries] (#mobile-first-and-media-queries)
1. [Pre-Processors] (#css-pre-processors)
1. [CSS Comments] (#css-comments)

<a name="css-syntax"></a>
### 3.1. CSS Syntax

Use soft tabs with two spaces. You can configure your editor for this.

```css
/* Good */
.nav-item {
  display: inline-block;
  margin: 0 5px;
}

/* Bad */
.nav-item {
    display: inline-block;
    margin: 0 5px;
}
```

Always use double quotes.

```css
/* Good */
[type="text"]
[class^="..."]

.nav-item:after {
  content: "";
}

/* Bad */
[type='text']
[class^='...']

.nav-item:after {
  content: '';
}
```

Include a single space before the opening brace of a ruleset.

```css
/* Good */
.header {
  ...
}

/* Bad */
.header{
  ...
}
```

Include a single space after the colon of a declaration.

```css
/* Good */
.header {
  margin-bottom: 20px;
}

/* Bad */
.header{
  margin-bottom:20px;
}
```

Include a semi-colon at the end of the last declaration in a declaration block.

```css
/* Good */
.header {
  margin-bottom: 20px;
}

/* Bad */
.header{
  margin-bottom:20px
}
```

Keep one declaration per line.

```css
/* Good */
.selector-1,
.selector-2,
.selector-3 {
  ...
}

/* Bad */
.selector-1, .selector-2, .selector-3 {
  ...
}
```

Single declarations should remain in one line.

```css
/* Good */
.selector-1 { width: 50%; }

/* Bad */
.selector-1 {
  width: 50%;
}
```

Separate each ruleset by a blank line.

```css
/* Good */
.selector-1 {
  ...
}

.selector-2 {
  ...
}

/* Bad */
.selector-1 {
  ...
}
.selector-2 {
  ...
}
```

Use lowercase, shorthand hex values and avoid specifying units is zero-values.

```css
/* Good */
.selector-1 {
  color: #aaa;
  margin: 0;
}

/* Bad */
.selector-1 {
  color: #AAAAAA;
  margin: 0px;
}
```

<a name="css-order"></a>
### 3.2. CSS Declaration Order

The declarations should be added in alphabetical order.

```css
/* Good */
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

/* Bad */
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
### 3.3. CSS Class Name

Keep class lowercase and use dashes.

```css
/* Good */
.nav-item { ... }

/* Bad */
.NavItem { ... }
.nav_item { ... }
```

Dashes serve as natural breaks in related class. Prefix class based on the closest parent or base class.

```css
/* Good */
.navbar { ... }
.nav { ... }
.nav-item { ... }
.nav-link { ... }

/* Bad */
.item-nav { ... }
.link-nav { ... }
```

Avoid giving too short names for class and always choose meaningful names that provide the class function.

```css
/* Good */
.btn { ... }
.page-header { ... }
.progress-bar { ... }

/* Bad */
.s { ... }
.ph { ... }
.block { ... }
```

<a name="css-performance"></a>
### 3.4. CSS Performance

Never use IDs.

```css
/* Good */
.header { ... }
.section { ... }

/* Bad */
#header { ... }
#section { ... }
```

Do not use selectors standards for not generic rules, always preferably for class.

```css
/* Good */
.form-control { ... }
.header { ... }
.section { ... }

/* Bad */
input[type="text"] { ... }
header
section
```

Avoid nesting elements, the preference is always to use class.

```css
/* Good */
.navbar { ... }
.nav { ... }
.nav-item { ... }
.nav-link { ... }

/* Bad */
.navbar ul { ... }
.navbar ul li { ... }
.navbar ul li a { ... }
```

Nest only when need change the class comportament with interference for other class. Keep the nested on max of three elements.

```css
/* Good */
.modal-footer .btn { ... }
.progress.active .progress-bar { ... }

/* Bad */
.modal-btn { ... }
.progress.active .progress-bar .progress-item span { ... }
```

Always minify the CSS code. Task builders like [Grunt](http://gruntjs.com/) leaves this easier.

```css
<!-- Good -->
.navbar { ... }.nav { ... }.nav-item { ... }.nav-link { ... }

<!-- Bad -->
.nav-item {
  ...
}
.nav-link {
  ...
}
```

<a name="mobile-first-and-media-queries"></a>
### 3.5 Mobile First and Media Queries

Start the development with generic rules with and add media queries with mobile first.

```css
/* Good */
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

/* Bad */
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

Keep the media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document.

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

<a name="css-pre-processors"></a>
### 3.6. Pre-Processors

I use pre-processors in all projects. Today I use `LESS`.

Warning with nesting rules of pre-processors. Continue keep without nesting.

```css
/* Good */
.nav-item { ... }

/* Bad */
.navbar {
  .nav {
    .nav-item {
      ...
    }
  }
}
```

Provide semantic names for variables.

```css
/* Good */
@brand-primary: #049cdb;

/* Bad */
@color-blue: #049cdb;
```

<a name="css-comments"></a>
### 3.7. CSS Comments

All comments must be made using the syntax of the preprocessor in use.

```js
//
// Section
// --------------------------------------------------

// Sub-section
// --------------------------------------------------

//
// Commentary block
//
//

// Simple commentary
```

<a name="js"></a>
## 4. Javascript

The main influences for the javascript rules are [idiomatic.js](https://github.com/rwldrn/idiomatic.js/) and [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style/).

### Javascript Summary

1. [Javascript Syntax] (#js-syntax)
1. [Javascript Variables] (#js-variables)
1. [Javascript Performance] (#js-performance)
1. [Javascript Comments] (#js-comments)

<a name="js-syntax"></a>
### 4.1. Javascript Syntax

Use soft tabs with two spaces. You can configure your editor for this.

```js
// Good
while (condition) {
  statements
}

// Bad
while (condition) {
    statements
}
```

Always use semicolons.

```js
// Good
var me = $(this);
test();

// Bad
var me = $(this)
test()
```

Always use single quotes.

```js
// Good
var string = '<p class="foo">Lorem Ipsum</p>';
var noteClick = me.attr('data-note');

// Bad
var string = "<p class='foo'>Lorem Ipsum</p>";
var noteClick = me.attr("data-note");
```

Keep `else` in the same line of closure of the `if`.

```js
// Good
if ( true ) {
  ...
} else {
  ...
}

// Bad
if ( true ) {
  ...
}
else {
  ...
}
```

Add spaces between operators.

```js
// Good
for (i = 0; i < 10; i++) {
  ...
}

// Bad
for (i=0;i<10;i++) {
  ...
}
```

Never add a space between the keyword function and the function name.

```js
// Good
foo(function() {
  ...
});

// Bad
foo ( function () {
  ...
});
```

Add spaces outside parentheses `()` but avoid it inside.

```js
// Good
if (condition) {
  statement
}

// Bad
if( condition ){
  statement
}
```

For conditionals always use curly brackets `{}`.

```js
// Good
if (condition) {
  statement
} else if (condition) {
  statement
} else {
  statement
}

// Bad
if (condition) statement;
else if (condition) statement;
else statement;
```

For strict equality checks `===` should be used in favor of `==`.

```js
// Good
if (foo === 'foo') {
  statement
}

// Bad
if (foo == 'foo') {
  statement
}
```

<a name="js-variables"></a>
### 4.2. Javascript Variables

All variables should be declared before used.

```js
// Good
var me = $(this);
var noteClick = me.attr('data-note');
notes[noteClick].play();

// Bad
notes[noteClick].play();
var me = $(this);
var noteClick = me.attr('data-note');
```

Always use `var` to declare variables.

```js
// Good
var me = $(this);

// Bad
me = $(this);
```

<a name="js-performance"></a>
### 4.3. Javascript Performance

Use [JSHint](http://www.jshint.com/) to detect errors and potential problems.

Always minify and concat the javascript code. Task builders like [Grunt](http://gruntjs.com/) leaves this easier.

<a name="js-comments"></a>
### 4.4. Javascript Comments

A single line above the code that is commented.

```js
// Good
// Good example of comment
var me = $(this);

// Bad
var me = $(this); // Bad example of comment
```

<a name="references"></a>
## 5. References

* [Code Guide by @mdo](https://github.com/mdo/code-guide)
* [idiomatic CSS](https://github.com/necolas/idiomatic-css/)
* [idiomatic.js](https://github.com/rwldrn/idiomatic.js/)
* [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style/)
* [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

<a name="translations"></a>
## 6. Translations

* [Português (Brasil)](/translations/pt-BR/)

<a name="license"></a>
## 7. License

[MIT License](http://felipefialho.mit-license.org/) © Luiz Felipe Tartarotti Fialho
