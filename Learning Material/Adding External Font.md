# Adding external Font in HTML/CSS
## Adding Downloaded Font
You can add a downloaded font using `@font-face` directive of CSS like this:

```css
@font-face {
  font-family: myFirstFont;
  src: url(sansation_light.woff);
}

div {
  font-family: myFirstFont;
}
```

Define the name of your font using `font-family` property under `@font-face`, and specify the source font file using `src` property.

If you want to add the variations of a font like `bold`,`italic` etc you can do so by specifying different `@font-faces`:
```css
@font-face {
  font-family: myFirstFont;
  src: url(sansation_light.woff);
}

@font-face {
  font-family: myFirstFont;
  src: url(sansation_bold.woff);
  font-weight: bold;
}
div {
  font-family: myFirstFont;
}
```
## Adding a font from online link
If you want to use a font directly using its link you can do so by including this in your `html` `<header>` tag:
```html
<link href="https://fonts.googleapis.com/css2?family=Ranchers&display=swap" rel="stylesheet"> 
```
And specifying the link to your font.

You can also import it in `CSS` like this:
```css
@import url('https://fonts.googleapis.com/css2?family=Ranchers&display=swap');
```

And then you can use it in `CSS` by specifying its name:

```css
div{
    font-family: 'Ranchers', cursive;
}
```

## References

[Google Fonts](https://fonts.google.com/)
[W3Schools web fonts](https://www.w3schools.com/css/css3_fonts.asp)