# Buttons

Functional CSS and not visual CSS!

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

## .btn-group

A group of button. Sort of like `UISegmentedControl`.