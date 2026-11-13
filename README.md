# EV Custom View

A demo of how to use the EUMETView APIs to build custom, mobile-friendly viewers. It can be used as a starting point for your own dashboards based on the EUMETView services.

It shows WMS layers on a map with a time slider, plus WFS and WCS point data: click the map and the panel lists
the attributes of the vector features under the cursor and the values of the visible coverages at that spot.

## License

This code is licensed under an MIT license. See file LICENSE.txt for details on the usage and distribution terms.

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
- `layers.yaml` – the title and the layers configuration

### Dependencies
The following dependencies are not included in the package but they are required and will be downloaded at runtime, when the page loads in the browser:
| dependency              | version | license      | copyright                                    | home\_url                                                                                                  | comments              |
| ----------------------- | ------- | ------------ | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------- |
| maplibre-gl             | 5.24.0  | BSD-3-Clause | 2023, MapLibre contributors                  | [https://github.com/maplibre/maplibre-gl-js](https://github.com/maplibre/maplibre-gl-js)                                      | map                   |
| maplibre-gl-opacity     | 1.8.0   | MIT          | 2021-2025 Yasunori Kirimoto, Kanahiro Iguchi | [https://github.com/dayjournal/maplibre-gl-opacity](https://github.com/dayjournal/maplibre-gl-opacity)     | layer chooser         |
| maplibre-gl-time-slider | 0.4.0   | MIT          | 2026 Open Geospatial Solutions               | [https://github.com/opengeos/maplibre-gl-time-slider](https://github.com/opengeos/maplibre-gl-time-slider) | time slider           |
| geotiff                 | 2.1.3   | MIT          | 2015 EOX IT Services GmbH                    | [https://github.com/geotiffjs/geotiff.js](https://github.com/geotiffjs/geotiff.js)                         | reads the WCS answers |
| js-yaml                 | 4.3.2   | MIT          | 2011-2015 by Vitaly Puzrin                   | [https://github.com/nodeca/js-yaml](https://github.com/nodeca/js-yaml)                                     | reads `layers.yaml`   |
