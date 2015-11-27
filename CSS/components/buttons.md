# Buttons

Functional CSS and not visual CSS!

* [CSS Buttons](http://cssbuttons.tumblr.com/)
* [How our CSS framework enforce accessibility](http://www.ebaytechblog.com/2015/11/04/how-our-css-framework-helps-enforce-accessibility/)

## HTML

```html
<button type="button"></button>
```

## MISTAKES

If you have solid and outline button, you need to think of positive and negative variants also:

```css
.btn-solid {}
.btn-plain {}
.btn-outline {}

.btn-solid--positive {}
.btn-solid--negative {}

.btn-outline--positive {}
.btn-outline--negative {}
```

## .btn

```
button,
.btn {
  display: inline-block;      // Side by side
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #fff;
  
  padding: ?
  
  font-family: ?
  line-height: ?
  
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;        // prevent text wrapping
  cursor: pointer;
  user-select: none;
  
  -webkit-appearance: button; // remove iOS style
  overflow: visible;          // fixes odd inner spacing in IE7}
```

**Important**: When using `line-height` to vertically center a single line of text, be sure to set the `line-height` to the height of the container minus 1.

```
.btn {
  height: 50px;
  line-height: 49px; // Minus 1}
```

## .btn-group

A group of button. Sort of like `UISegmentedControl`.

## With icon

```
.btn--next {
  &:after {
    @include icon(next);  }}
```