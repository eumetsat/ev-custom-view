# EV Custom View

A demo of how to use the EUMETView APIs to build custom, mobile-friendly viewers. It can be used as a starting point for your own dashboards based on the EUMETView services.

It shows WMS layers on a map with a time slider, plus WFS and WCS point data: click the map and the panel lists
the attributes of the vector features under the cursor and the values of the visible coverages at that spot.

## License

This code is licensed under an MIT license. See file LICENSE.txt for details on the usage and distribution terms.

All product names, logos, and brands are property of their respective owners. All company, product and service names used in this website are for identification purposes only

## Authors

- [**Niklas Jordan**](mailto://niklas.jordan@external.eumetsat.int) - *Initial work* - [EUMETSAT](http://www.eumetsat.int)

## How to use it

Everything you normally want to change lives in `layers.yaml`: the title of the page and the list of layers,
each with its name, its layer name on the EUMETView GeoServer, its type (`wms`, `wfs` or `wcs`), an optional
style, and whether it is shown at start or follows the time slider. The comments at the top of the file explain
every field. No change to the HTML or JavaScript is needed.

Then open `view.html` in the browser through a web server. Any web host works; locally, run this in the folder
and open http://localhost:8000/view.html:

```
python3 -m http.server 8000
```

A web server is needed because browsers do not let a page opened straight from disk load its YAML file.

## Files

- `view.html` – the viewer: map, layer panel, time slider and point info, with all the code
- `layers.yaml` – the title and the layers

## Dependencies

All libraries are loaded from a CDN at runtime; nothing needs to be installed.

| Library | Version | Purpose | Licence |
|---|---|---|---|
| [MapLibre GL JS](https://maplibre.org/) | 5.24.0 | map | BSD-3-Clause |
| [maplibre-gl-opacity](https://github.com/mug-jp/maplibre-gl-opacity) | 1.8.0 | layer chooser | MIT |
| [maplibre-gl-time-slider](https://www.npmjs.com/package/maplibre-gl-time-slider) | 0.4.0 | time slider | MIT |
| [geotiff.js](https://geotiffjs.github.io/) | 2.1.3 | reads the WCS answers | MIT |
| [js-yaml](https://github.com/nodeca/js-yaml) | 4.1.0 | reads `layers.yaml` | MIT |
