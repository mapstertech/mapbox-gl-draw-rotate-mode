Mapbox GL Draw Rotate Mode
==========================

<style>
    .button-container {
        text-align: center;
        margin-top: 15px;
    }
    .button-container .btn {
        color: black;
        border: thin black solid;
    }
</style>
<div>
    <div id="map" style="width:100%;height:400px;"></div>
    <div class="button-container">
        <button id="rotate" class="btn">Rotate</button> <button class="btn" id="rotate-off">Rotate off</button>
    </div>

    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.1/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.1/mapbox-gl.css' rel='stylesheet' />
    <link rel='stylesheet' href='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-draw/v1.0.4/mapbox-gl-draw.css' type='text/css' />
    <script src='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-draw/v1.0.4/mapbox-gl-draw.js'></script>
    <script type="text/javascript" src='https://rawgit.com/mapstertech/mapbox-gl-draw-rotate-mode/master/dist/mapbox-gl-draw-rotate-mode.min.js'></script>

    <script type="text/javascript">

    mapboxgl.accessToken = 'pk.eyJ1IjoidGVtcHJhbm92YSIsImEiOiJjaWd0c3M2MW4wOHI2dWNrbzZ5dWo1azVjIn0.x5sm8OjRxO9zO_uUmxYEqg';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mapbox/streets-v9', // stylesheet location
    });

    var geojson = {"type": "FeatureCollection","features": [{"type": "Feature","properties": {},"geometry": {"type": "Polygon","coordinates": [[[-42.890625,59.355596110016315],[-52.03125,52.908902047770255],[-43.59375,25.799891182088334],[-29.8828125,16.636191878397664],[-13.7109375,17.644022027872726],[11.6015625,32.24997445586331],[18.28125,47.754097979680026],[-1.0546875,58.99531118795094],[-21.796875,61.60639637138628],[-42.890625,59.355596110016315]]]}},{"type": "Feature","properties": {},"geometry": {"type": "Polygon","coordinates": [[[-61.87499999999999,56.75272287205736],[-69.60937499999999,38.8225909761771],[-62.22656249999999,30.44867367928756],[-46.05468749999999,32.54681317351514],[-35.859375,39.639537564366684],[-37.265625,52.482780222078226],[-39.0234375,60.930432202923335],[-41.1328125,65.2198939361321],[-58.35937499999999,59.355596110016315],[-61.87499999999999,57.89149735271034],[-61.87499999999999,56.75272287205736]]]}}]};

    var draw = new MapboxDraw({
       defaultMode: 'RotateMode',
       modes: Object.assign({
         RotateMode: RotateMode,
       }, MapboxDraw.modes),
    });
    map.addControl(draw);

    map.on('load',function() {
      draw.add(geojson);
    })

    document.getElementById('rotate').addEventListener('click',function() {
      draw.changeMode('RotateMode'); // turn on RotateMode
    });

    document.getElementById('rotate-off').addEventListener('click',function() {
      draw.changeMode('simple_select'); // turn off RotateMode
    });

    </script>
 </div>


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
<script type="text/javascript" src="mapbox-gl-draw-rotate-mode.js"></script>
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
