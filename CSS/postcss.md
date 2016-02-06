# PostCSS

* [Breaking up with Sass](http://benfrain.com/breaking-up-with-sass-postcss/)
* [Who will save us from the dark side of CSS pre-processors?](http://alistapart.com/column/what-will-save-us-from-the-dark-side-of-pre-processors)

## Plugins

* [PostCSS.parts](http://postcss.parts/)
* [postcss-vertical-rhythm](https://github.com/markgoodyear/postcss-vertical-rhythm)
* [postcss-nested](https://github.com/postcss/postcss-nested)
* [postcss-mixins](https://github.com/postcss/postcss-mixins)
* [cssgrace](https://github.com/cssdream/cssgrace)
* [postcss-colorblind](https://github.com/btholt/postcss-colorblind)
* [postcss-bem-linter](https://github.com/postcss/postcss-bem-linter)

```css
/* Nesting */
.phone {
  /* .phone_title */
  &_title {
    width: 500px;
    
    @media (max-width: 500px) {
      width: auto;
    }

    /* body.is_dark .phone_title */
    body.is_dark & {
      color: white;
    }
  }

  /* .phone img */
  img {
    display: block;
  }
}
```