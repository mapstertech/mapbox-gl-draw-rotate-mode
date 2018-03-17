Mapbox GL Draw Rotate Mode - rotation in GL JS
=================================================

__[Online Demo](http://mapster.me/mapbox-gl-draw-rotate-mode)__

This implements a rotation mode in GL Draw. Module is still in active development.

Installation
------------

### npm

```
npm install mapbox-gl-draw-rotate-mode
```

Include in your project

```
import RotateMode from 'mapbox-gl-draw-rotate-mode';

var draw = new MapboxDraw(
  defaultMode: 'RotateMode'
  modes: Object.assign(
    RotateMode: RotateMode
  }, MapboxDraw.modes)
});

draw.changeMode('RotateMode'); // turn on RotateMode
draw.changeMode('simple_select'); // turn off RotateMode
```
