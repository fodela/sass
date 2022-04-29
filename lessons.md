# Sass

Is a css preprocessor, or an extension of css that adds power and elegance to the basic language

sass code is compiled back to css using a sass compiler

Other preprocessor are less and stylus. Sass is the most popular one.

### Main features

1. Variables => for reusable values
2. Nesting => to nest selectors inside one another
3. Operators => for mathematical operations
4. Partials and imports => to write CSS in different and import them all into one single file
5. Mixins => to write reusable pieces of css code
6. Functions => similar to mixins, with the difference being that they produce a value that can be used.
7. Extends => to make different selectors inherit declarations that are common to all of them.
8. Control directives => for writing complex code using conditionals and loops

### Variables

```
    /* declaration */
    $solor-text-dark: #333;

    /* usage */
    font-color: $color-text-dark
```

### Mixin

Declaration

```
@mixin clearfix {
    &::after {
        content:"";
        clear: both;
        display: table;
    }
}

//Can take argument

@mixin style-link-text($color){
    text-decoration:none;
    text-transform: uppercase;
    color: $color;
}
```

Usage or implementation

```
nav {
    @include clearfix

    @include style-link-text($color-text-light)
}
```

### Functions

In-built functions
There are built-in sass functions such as:
darken() and lighten

```
background-color: darken($color-primary, 10%)
```

Custom functions

```
declaration
@function divide($a, $b){
    @return $a / $b
}

usage
margin: divide(60, 12) * 1px;

```

# Extends

We create a placeholder for every properties to prevent repetition.

It copies the selector to the placeholder content there by keep the code "DRY". While mixins copies the code to where ever we include it.

```
/* declaration */
%btn-placeholder{
    padding:10px;
    display: inline-block;
    text-align: center;
    border-radius: 100px;
    width: $width-button;
    @include style-link-text($color-text-light)
}
/* usage */
.btn-main{
    &:link{
        @extend %btn-placeholder;
        background-color: $color-secondary;
    }
}
```
