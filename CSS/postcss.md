# PostCSS

* [Breaking up with Sass](http://benfrain.com/breaking-up-with-sass-postcss/)
* [Who will save us from the dark side of CSS pre-processors?](http://alistapart.com/column/what-will-save-us-from-the-dark-side-of-pre-processors)

## Against PostCSS

* [The trouble with preprocessing based on future specs](https://css-tricks.com/the-trouble-with-preprocessing-based-on-future-specs/)

## Plugins

* [PostCSS.parts - Searchable catalog of plugins](http://postcss.parts/)

---

* [postcss-simple-vars - Sass-like variables if you hate `var(--)`](https://github.com/postcss/postcss-simple-vars)
* [postcss-vertical-rhythm - `vr(2)`](https://github.com/markgoodyear/postcss-vertical-rhythm)
* [postcss-nested](https://github.com/postcss/postcss-nested)
* [postcss-mixins](https://github.com/postcss/postcss-mixins)
* [cssgrace](https://github.com/cssdream/cssgrace)
* [postcss-colorblind](https://github.com/btholt/postcss-colorblind)
* [postcss-sorting](https://github.com/hudochenkov/postcss-sorting)
* [postcss-short-size - `size(), min-size()`](https://github.com/jonathantneal/postcss-short-size)

**Media Queries**

* [postcss-if-media](https://github.com/arccoza/postcss-if-media)

## Linter

Prevent code from gradually degrading in quality.

* [postcss-bem-linter](https://github.com/postcss/postcss-bem-linter)

## Stylelint

* [How to lint your CSS properly with Stylelint](http://www.creativenightly.com/2016/02/How-to-lint-your-css-with-stylelint/)
* [stylelint-statement-max-nesting-depth](https://github.com/davidtheclark/stylelint-statement-max-nesting-depth)

## People

* [David Clark](http://davidtheclark.com/)

## Examples

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