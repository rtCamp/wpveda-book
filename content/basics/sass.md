# SASS tutorial
---
## Introduction to SASS
- Sass is a preprocessor scripting language that is interpreted or compiled into Cascading Style Sheets (CSS).
- Sass is written in Ruby.
- Provides variables, functions, conditional statements and more.
- Sass files can be splited up into modules for bigger projects.
- Browser doesn't understand Sass code.

### What you schould know
- Programming fundamentals - functions, conditional statements etc.
- CSS !
---
## Tools
- You'll need a Sass processor. It could be any of your choice.
---

## 1.Get to know
HTML <br />
Simple HTML file that you write normally.
```HTML
<div class="block">
    <p>Testing Sass</p>
    <div class="box"></div>
</div>
```
SASS<br />
.scss files goes to src folder.
```scss
.box{
    border: 10px solid crimson;
    height: 100px;
    width: 100px;
}
```
CSS<br />
.css files will be compiled and stored in a seperate directory.
```css
.box {
    border: 10px solid crimson;
    height: 100px;
    width: 100px;
}
```
---
## 2 Nesting in SCSS
Nesting is not preffered due to it becomes hard to know that why a specific element is having style. Because of they will not have a class or id.<br />

HTML
```HTML
<div class="block">
    <p>Nesting</p>
    <div class="nest">
        <span>Hey, what's up ?</span> <br />
        <a>I am green text.</a><br />
        <a><span>I am span under anchor tag.</span></a>
    </div>
</div>
```
SASS
```scss
.nest{
    color:red;
    border: 10px solid cornflowerblue;
    height: 100px;
    a{
        color:green;
        span{
            color:blue;
        }
    }
}
```
CSS
```css
.nest {
    color: red;
    border: 10px solid cornflowerblue;
    height: 100px;
}

.nest a {
    color: green;
}

.nest a span {
    color: blue;
}
```
---
## 3 Variables
Sass variables are similar as they are in other programming languages.<br />
Syntax: `$variable-name:vaue;`<br />
After the compilation the css will hold the exact value which was passed to the sass variable not the variable itself.<br />

HTML
```HTML
<div class="block">
    <p>Variables</p>
    <span class="rtstyle">rtCamp is cool !</span>
</div>
```
SASS
```scss
$rtblue: #3478bd;
$rtsize: 24px;

.rtstyle{
    color:$rtblue;
    font-size:$rtsize;
}
```
CSS
```css
.rtstyle {
    color: #3478bd;
    font-size: 24px;
}
```
---
## 4 Mixins
Mixins are re-usable chunks of code.<br />
Mixins can also be used as functions.<br />
Syntax: `@mixin mixin-name{ ... }` <br />
and to use that mixin inside some class:
`@include mixin-name()`<br />

HTML
```HTML
<div class="block">
    <p>Mixins</p>
    <div class="mixin-demo">
        <div class="mixin-blue"></div>
        <div class="mixin-red"><span>Hey I'm span</span></div>
    </div>
</div>
```
SASS
```scss
@mixin main-mixin{
    border: 10px solid;
    .mixin-blue{
        height:50px;
        margin:5px;
        border:3px solid royalblue;
    }

    .mixin-red{
    	height:50px;
    	margin:5px;
    	border:3px solid red;
    }

    .mixin-red span{
    	color: green;
    }
}

.mixin-demo{
    @include main-mixin();
    border-color: gold;

}
```
CSS
```css
.mixin-demo {
    border: 10px solid;
    border-color: gold;
}

.mixin-demo .mixin-blue {
    height: 50px;
    margin: 5px;
    border: 3px solid royalblue;
}

.mixin-demo .mixin-red {
    height: 50px;
    margin: 5px;
    border: 3px solid red;
}
.mixin-demo .mixin-red span {
    color: green;
}
```
---
## 5 Mixins with arguments
Mixins with arguments works same as functions like in other programming laguages. <br />
You pass variables in the arguments and function returns the output ! <br />
Just remember to give meaningful names to the variables <br />
Syntax:
```scss
@mixin mixin-name($variable-name) {
    height: $variable-name;
}
// To use that mixin ...
.some-clss {
    @include mixin-name(1000px);
}
```

HTML
```HTML
<div class="block">
    <p>Mixin with arguments</p>
    <div class="mixin-arg-eg"></div>
</div>
```
SASS
```scss
@mixin mixin-arg($h, $w) {
    height: $h;
    width: $w;
}

.mixin-arg-eg {
    @include mixin-arg(100px,1000px);
    border:10px solid crimson;
}
```
CSS
```css
.mixin-arg-eg {
    height: 100px;
    width: 1000px;
    border: 10px solid crimson;
}
```
---
## 6 Importing files
How about keeping your variables and mixins in different directories ? <br />
That's you should be doing ! (Best practices) <br />
Well you can keep all the scss in different files to make your code modular. <br />
Syntax: `@import "file-tobe-import.scss";` <br />

HTML
```HTML
<div class="block">
    <p>Import</p>
    <div class="import-demo">
        <span>Hey</span>
    </div>
</div>
```
SASS
```scss
@import "imported.scss";
.import-demo{
    @include gradient();
    height: $height;
    color:white;
    font-size: 30px;
}

//file-2:importend.scss
$height : 100px;

@mixin gradient{
    background: linear-gradient(to right, #5c258d, #4389a2);
}
```
CSS
```css
.import-demo {
  background: linear-gradient(to right, #5c258d, #4389a2);
  height: 100px;
  color: white;
  font-size: 30px;
}
```
---
## 7 Pseudo Classes/Elements
To add pseudo elements to your classes use `&:<element>` <br />

HTML
```html
<div class="block">
    <p>Pseudo Classes</p>
    <div class="pseudo-example"></div>
</div>
```
SASS
```scss
.pseudo-example{
    height:100px;
    background: #4b6cb7;

    &:hover{
        background: #cb2d3e;
    }
}
```
CSS
```css
.pseudo-example {
  height: 100px;
  background: #4b6cb7;
}

.pseudo-example:hover {
  background: #cb2d3e;
}
```
---
## 8 Math Operations
Simple math operations like addition, Subtraction, Multiplication, Division are possible in sass <br />
To perform math operation just wrap the things in `()` like `height: (300px/3);` <br />

HTML
```html
<div class="block">
    <p>Math Operations</p>
    <div class="math-demo">
        <ul>
            <li>ITEM 1</li>
            <li>ITEM 2</li>
            <li>ITEM 3</li>
        </ul>
    </div>
</div>
```
SASS
```scss
.math-demo{
    border: 10px solid cornflowerblue;
    width: 720px;
    height: 110px;
    margin: auto;
    li{
        width: (700px / 3);
        border: 10px solid crimson;
        float: left;
        height: 90px;
    }
    ul{
        list-style: none;
        padding: 0;
        margin: 0;
    }
}
```
CSS
```css
.math-demo {
    border: 10px solid cornflowerblue;
    width: 720px;
    height: 110px;
    margin: auto;
}

.math-demo li {
    width: 233.33333px;
    border: 10px solid crimson;
    float: left;
    height: 90px;
}

.math-demo ul {
    list-style: none;
    padding: 0;
    margin: 0;
}
```
---
## 9 Color Functions
There are many functions available to play around with colors. <br />
Links are provided at the end. <br />

HTML
```HTML
<div class="block">
    <p>Color functions</p>
    <div class="color-example"></div>
</div>
```
SASS
```scss
.color-example{
    height: 100px;
    background: #1d518b;

    &:hover{
        background: lighten(#1d518b,20);
    }
}
```
CSS
```css
.color-example {
    height: 100px;
    background: #1d518b;
}

.color-example:hover {
    background: #3883d6;
}
```
---
## 10 @content in Sass
@content keyword is like a place holder. <br />
It will grab whatever comes at the same possition where it is defined. <br />

HTML
```html
<div class="block">
    <p>@content keyword</p>
    <div class="content-demo">
        <ul>
            <li>ITEM 1</li>
            <li>ITEM 2</li>
            <li>ITEM 3</li>
        </ul>
    </div>
</div>
```
SASS
```scss
@mixin mQ($arg) {
    @media screen and (max-width: $arg){
        @content;
    }
}

.content-demo{
    border: 10px solid cornflowerblue;
    width: 100%;
    height: 110px;
    margin: auto;
    li{
        width: (100%/ 3);
        border: 10px solid crimson;
        float: left;
        height: 90px;
        @include mQ(720px){
            width:100%;
        }
    }
    ul{
        list-style: none;
        padding: 0;
        margin: 0;
    }
}
```
Here when we included our mixin `@content` will be replaced by the content in the mixin ie. `width:100%` <br />
CSS
```css
.content-demo {
    border: 10px solid cornflowerblue;
    width: 100%;
    height: 110px;
    margin: auto;
}

.content-demo li {
    width: 33.33333%;
    border: 10px solid crimson;
    float: left;
    height: 90px;
}

@media screen and (max-width: 720px) {
    .content-demo li {
        width: 100%;
    }
}

.content-demo ul {
    list-style: none;
    padding: 0;
    margin: 0;
}
```
---
## 11 If with multiple argument
There are many conditional statements available in Sass.<br />
You can check them out on the link provided at the end <br />

HTML
```html
<div class="block">
    <p>If with Multiple Arguments</p>
    <div class="mul-arg-example"></div>
</div>
```
SASS
```scss
//arrays starts at 1 here !!!
@mixin mul-arg($list...){
    @if length($list) == 1{
        height: nth($list, 1);
    }
    @if length($list) == 2{
        height: nth($list, 1);
        border-color: nth($list, 2);
    }
}

.mul-arg-example{
    border : 10px solid red;
    @include mul-arg(100px, blue);
}
```
`$list...` <br />
accepts multiple arguments that can be in any number.<br />
`length($list)`<br />
returns number of elements in the `$list`.<br />
`nth($list,2)`<br />
variable at possition 2 in the `$list`.<br />

CSS
```css
.mul-arg-example {
    border: 10px solid red;
    height: 100px;
    border-color: blue;
}
```
---
## Useful Links
```
Loops :
https://clubmate.fi/for-while-and-each-loops-in-sass/
https://www.sitepoint.com/sass-reference/loops/
https://www.tutorialsteacher.com/sass/sass-control-directives

Color Functions :
http://sass-lang.com/documentation/Sass/Script/Functions.html
```
> Creator's quote
> > Do follow coding standards <br />
> > Divide code in modules ( Makes maintenance easy ).<br />
> > Documentation is the best way to learn. <br />
> > Create !
