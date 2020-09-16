# SCSS vs CSS

If you are a programmer and you are also fed up of repeating same things several times in CSS
**SCSS** Or Syntactically Awesome Stylesheet can help you, SCSS is a preprocessor scripting language which can be compiled or interpreted to **CSS**. What does that mean? It provides a more simpler and programatic way of writing **CSS**, so it contains all the features of **CSS** plus some additional features.

## Key Features of SCSS

### Variables

We can declare variables in **SCSS** and use them as values to any property:

```scss
$myColor: red;
body {
  color: $myColor;
}

p {
  background-color: $myColor;
}
```

Equivalent CSS:

```css
body {
  color: red;
}

p {
  background-color: red;
}
```

So now when you want to change the color you just have to do it in one place.

### Nesting

We can nest selectors the same way we nest tags in html

```scss
.container {
  ul {
    list-style: none;
  }
}
```

Equivalent CSS:

```css
.container ul {
  list-style: none;
}
```

### `@import`

Many times we may want to create a base CSS file, which we can directy import in **CSS** we can do it by:

```scss
@import filename;
```

### `@mixin`

We can use `@mixin` to create block of statements which can be reused at different places, like we user functions in any programming language.

Declaration:

```scss
@mixin important-text {
  color: red;
  font-size: 25px;
  font-weight: bold;
  border: 1px solid blue;
}
```

Usage
The `@include` directive is used to include a mixin.

```scss
.danger {
  @include important-text;
  background-color: green;
}
```

Equivalent CSS:

```css
.danger {
  color: red;
  font-size: 25px;
  font-weight: bold;
  border: 1px solid blue;
  background-color: green;
}
```

### `@extend`

We can use `@extend` to share the properties from one element to other, it is useful when we have almost identical elements.

```scss
.button-basic {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report {
  @extend .button-basic;
  background-color: red;
}

.button-submit {
  @extend .button-basic;
  background-color: green;
  color: white;
}
```

CSS equivalent:

```css
.button-basic,
.button-report,
.button-submit {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.button-report {
  background-color: red;
}

.button-submit {
  background-color: green;
  color: white;
}
```

## Converting SCSS to CSS

Now that we have a gist about how **SCSS** works let's see how we can convert **SCSS** to **CSS**.
There are multiple ways to achive this:

- **Using online compiler:**
  You can use online converter like [safeconverter](https://www.safetoconvert.com/scss-to-css-converter), [JSON Formatter](https://jsonformatter.org/scss-to-css) etc, where you can paste your **SCSS** code and it will automatically generate **CSS** code.
- **Using plugin in IDE:**
  IDEs like VScode or Webstrom have an option to compile **SCSS** file find one for your IDE and install it.
- **Using Command Line:**
  - Install SASS for command line. You download **SASS** from [here](https://github.com/sass/dart-sass/releases/tag/1.26.10)
  - Execute `sass source/stylesheets/index.scss build/stylesheets/index.css`

## References

- [W3 schools SASS tutorial](https://www.w3schools.com/sass/default.php)
- [SASS Installation](https://sass-lang.com/install)
