# CSS selector specificity

In CSS there are different ways to edit an element for example universal `*`, `element` `class` etc. When multiple selectors are targetting the same element the browser need to know which one to apply and it decides so by the `specifity` of the selector, i.e the more specific the selector the higher importance it will have.

This the ordere of selectors from low to high specificity:

| Selector     | CSS                                       | HTML                                                                                               |
| ------------ | ----------------------------------------- | -------------------------------------------------------------------------------------------------- |
| element      | a { <br> color: red; <br>}                | `<a href="https://example.com"> Example </a>`                                                      |
| class        | .link { <br> color: blue; <br>}           | `<a href="https://example.com" class='link'> Example </a>`                                         |
| id           | #example-link { <br> color: yellow; <br>} | `<a href="https://example.com" class='link' id='example-link'> Example </a>`                       |
| inline style |                                           | `<a href="https://example.com" class='link' id='example-link' style='color: purple'> Example </a>` |
| !importatnt  | a { <br> color: red !important; <br>}     | `<a href="https://example.com"> Example </a>`                                                      |

If there are multiple rules defined for same selector the the latest one will be followed:

```css
p {
    color: red;
    padding: 20px;
}

p {
    color: green;
}
```

In the above example the final color of content in all the `<p>` will have `green` color.

### References:

https://egghead.io/lessons/css-utilize-selector-specificity-to-control-applied-styles
