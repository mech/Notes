# Tricks

* [Skewed hit boxes with CSS transforms](http://viget.com/inspire/skewed-hit-boxes-with-css-transforms)

## Border radius

* [CSS arrow](http://cssarrowplease.com/)
* Animatable - You can animate between any 2 radii.

```
// Half of a elliptical shape
border-radius: 50% / 100% 100% 0 0;
width: 400px;
height: 420px;

// Quarter
border-radius: 100% 0 0 0;
width: 400px;
height: 420px;

// Animate
.br {
  border-radius: 50% / 100% 100% 0 0;
  // transition: .5s;
  animation: .5s silly_bouncing infinite alternate;
}

.br:hover {
  border-radius: 50%;
}

@keyframes silly_bouncing {
  to {
    border-radius: 50%;
    bottom: 100px;
  }
}
```

## Gradient

```
// Cut-corner shape
background: #f06;
background: linear-gradient(135deg, transparent 20px, #f06 0),
            linear-gradient(225deg, transparent 20px, #f06 0),
            linear-gradient(315deg, transparent 20px, #f06 0),
            linear-gradient( 45deg, transparent 20px, #f06 0);
background-position: top left, top right,
                     bottom right, bottom left;
background-size: 50% 50%;
background-repeat: no-repeat;
```