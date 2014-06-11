# Tricks

* [Skewed hit boxes with CSS transforms](http://viget.com/inspire/skewed-hit-boxes-with-css-transforms)
* [7 things your didn't know you could do with CSS](http://davidwalsh.name/css-facts)
* [Pure CSS slide up and down](http://davidwalsh.name/css-slide)
* [Useful?](http://snippetrepo.com/)
* [Reading position indicator](http://css-tricks.com/reading-position-indicator/)
* [Some components to learn from](http://goratchet.com/components/)

```
/* do nothing when clicked even through JavaScript */
.disabled { pointer-events: none; }
```


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

## Input

```
// See search input from https://slack.zendesk.com/hc/en-us/articles/201723133-Billing-FAQ
input {
  border: 1px solid #CCC;
  box-shadow: inset 0 1px 1px rgba(0,0,0,0.075);
  transition: border linear .2s,box-shadow linear .2s;
  border-radius: 2rem;
  padding: 10px;
}
```

## Drag and Drop

```
[draggable] {
  user-select: none;
  // Required to make elements draggable in old WebKit
  -khtml-user-drag: element;
  -webkit-user-drag: element;
}
```