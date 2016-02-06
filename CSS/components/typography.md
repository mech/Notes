# Typography

```css
@mixin truncate($boundary) {
  max-width: $boundary;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```