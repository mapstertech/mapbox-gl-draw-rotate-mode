Mapbox GL Draw Rotate Mode - rotation in GL JS
=================================================

<div>
    <div id="map" style="width:100%;height:400px;"></div>
    <button id="rotate">Rotate</button> <button id="rotate-off">Rotate off</button>
    
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.1/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v0.44.1/mapbox-gl.css' rel='stylesheet' />
    <script type="text/javascript">
        
    mapboxgl.accessToken = 'pk.eyJ1IjoidGVtcHJhbm92YSIsImEiOiJjaWd0c3M2MW4wOHI2dWNrbzZ5dWo1azVjIn0.x5sm8OjRxO9zO_uUmxYEqg';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mapbox/streets-v9', // stylesheet location
        center: [-74.50, 40], // starting position [lng, lat]
        zoom: 9 // starting zoom
    });
    
    </script>
 </div>


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
