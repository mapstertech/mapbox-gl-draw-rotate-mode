Mapbox GL Draw Rotate Mode
==========================

This implements a rotation mode in GL Draw. Module is still in active development.

Installation
------------

### npm

```
npm install mapbox-gl-draw-rotate-mode

import RotateMode from 'mapbox-gl-draw-rotate-mode';
```

### browser

Get the js file from the `dist/` folder and include in your project.

```
<script type="text/javascript" src="mapbox-gl-draw-rotate-mode.js></script>"
```

## Usage

Ensure you are loading draw onto your map as a control before triggering `changeMode`.

```
var draw = new MapboxDraw(
  defaultMode: 'RotateMode'
  modes: Object.assign(
    RotateMode: RotateMode
  }, MapboxDraw.modes)
});

map.addControl(draw);

/*
 After load, or on events, activate or deactivate rotation:
*/

draw.changeMode('RotateMode');
draw.changeMode('simple_select');
```

## Events

Mapbox GL Draw Rotate Mode offers you a few events. Redefine these as you need.

```
RotateMode.rotatestart = function(selectedFeature,originalCenter) {
   console.log('ROTATESTART');
   console.log('feature: ',selectedFeature);
   console.log('center: ',originalCenter);
}

RotateMode.rotating = function(selectedFeature,originalCenter,lastMouseDown) {
   console.log('ROTATING');
   console.log('feature: ',selectedFeature);
   console.log('center: ',originalCenter);
   console.log('lastMouseDown: ',lastMouseDown);
}

RotateMode.rotateend = function(selectedFeature) {
   console.log('ROTATEEND');
   console.log('feature: ',selectedFeature);
}
```
