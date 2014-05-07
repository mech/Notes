# Tricks

* [Skewed hit boxes with CSS transforms](http://viget.com/inspire/skewed-hit-boxes-with-css-transforms)

## Sites with tricks to learn

[Sign up shake page](http://www.emojiweather.com/)

```
form.shake-me {
  animation: formShakeAnimation 400ms ease-in-out
}

@keyframes formShakeAnimation {
  0% {
    transform: translateX(0)
  }

  12.5% {
    transform: translateX(-6px) rotateY(-5deg)
  }

  37.5% {
    transform: translateX(5px) rotateY(4deg)
  }

  62.5% {
    transform: translateX(-3px) rotateY(-2deg)
  }

  87.5% {
    transform: translateX(2px) rotateY(1deg)
  }

  100% {
    transform: translateX(0)
  }
}
```

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