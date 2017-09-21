# Basics of SASS

## Description
* Sass is a scripting language that is interpreted or compiled into Cascading Style Sheets (CSS).
* Sass extends CSS by providing several mechanisms available in more traditional programming languages, particularly object-oriented languages, but that are not available to CSS3 itself.

Click [HERE](http://sass-lang.com/) for more information.

## Compile SASS to CSS
* From the command line interface we can compile de Sass code doing:
```shell
sass sass_file.scss compiled_file.css
```
* There are plugins that automatically compile the code for you.
  * For Atom: [Atom-Sass](https://atom.io/packages/atom-sass), [Sass Compiler](https://atom.io/packages/sass-compiler), [sass-autocompile package](https://atom.io/packages/sass-autocompile)
  * For Sublime:[Sass​Builder](https://packagecontrol.io/packages/SassBuilder)

## Useful tools

### Nesting selectors

```sass
/* SASS */
.parent{
  color: blue;
  .child{
    font-size: 12px;
  }
}
```

```css
/* CSS */
.parent{
  color: blue;
}
.parent .child{
  font-size: 12px;
}
```

### Nesting CSS properties

```sass
/* SASS */
.parent{
  font : {
    family: Roboto, sans-serif;
    size: 12px;
    decoration: none;
  }
}
```

```css
/* CSS */
.parent{
  font-family: Roboto, sans-serif;
  font-size: 12px;
  font-decoration: none;
}
```

### Variables

To declare a new variable we just need to write:
```sass
$new-variable: rgba(255,255,255);
/* It can be any type of value */
```

There are the following data types:
* **Numbers**, such as 8.11, 12, and 10px.
* **Strings** of text, with and without quotes. Some examples are "potato", 'tomato', span.
* **Booleans**, or simply true and false.
* **Null**, which is considered an empty value.
* **Lists** (1.5em Helvetica bold; or Helvetica, Arial, sans-serif; )
* **Maps** (key1: value1, key2: value2);

### String interpolation

```sass
@mixin photo-content($file) {
    content: url(#{$file}.jpg); //string interpolation
    object-fit: cover;
}
```

### Mixins
* Try to only create mixins that take in an argument, otherwise you should extend.
* Always look at your CSS output to make sure your extend is behaving as you intended.

```sass
/* SASS */
@mixin text-hover($color) {
  &:hover {
    color: $color;
  }
}
.word{
  display: block;
  @include text-hover(red);
}
```

```css
/* CSS */
.word{
  display: block;
}
.word:hover{
  color: red;
}
```

### Color parameters

```sass
//Decrease opacity value in an specific amount
$color1: fade-out($color, $amount);	 

//Add up opacity value in an specific amount
$color2: fade-in($color, $amount);

//Changes hue value between [-360,360]
$color3: adjust-hue($color, $degrees)

//RGB color declaration divided in 2 each
$red: #990000;
$blue: #000099;

//Add up for complementary colors		
$newColor : red + blue;			
```

### SASS Operands

* Addition: **+**
* Subtraction: **-**
* Multiplication: *****
* Division: **/**
* Modulo: **%**

### Loops

```sass
/* Each Loop */
@each $item in $list {
  .#{$item} {
    backgorund: $item;
  }
}
/* For Loop */
@for $i from 1 through $total {
  .ray:nth-child(#{$i}) {
    background: blue;
  }
}
```
### Conditionals
```sass
/* Inline / Simple conditional */
width: if($condition, $value-if-true, $value-if-false);
/* Multiple Conditional */
@mixin deck($suit) {
  @if($suit == hearts || $suit == spades){
    color : blue;
  }
  @else-if($suit == clovers || $suit == diamonds){
    color: red;
  }
  @else {
    color: green;
  }
}
```

### @Extend

```sass
.lemonade{
  border: 1px yellow;
  background-color: #fdd;
}
.strawberry{
  @extend .lemonade;
  border-color: pink;
}
```

```css
/* CSS */
.lemonade, .strawberry{
  border: 1px yellow;
  background-color: #fdd;
}
.strawberry{
  border-color: pink;
}
```

### %Placeholder
Placeholders prevent rules from being rendered to CSS on their own and only become active once they are extended anywhere an id or class could be extended.

```sass
/* SASS */
a%drink{
  font-size: 2em;
  background-color: %lemon-yellow;
}
.lemonade{
  @extend %drink;
  //more rules
}
```

```css
/* CSS */
a.lemonade{
  font-size: 2em;
  background-color: yellow;
}
.lemonade{
  //more rules
}
```
## About
Examples from [Codeacademy](https://www.codecademy.com/) courses.
