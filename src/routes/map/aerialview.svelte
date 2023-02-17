<head>
    <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no" />
    <link
        rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.7.1/leaflet.css"
    />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.7.1/leaflet.js"></script>

    <style>
        #map {
            height: 50vh;
            width: 70vw;
            margin-left: auto;
            margin-top: 1em;
            border-radius: 10px;
            margin-right: 0em;
        }

        .arrow-icon {
            width: 14px;
            height: 14px;
        }

        .arrow-icon > div {
            margin-left: -1px;
            margin-top: -3px;
            transform-origin: center center;
            font: 12px/1.5 'Helvetica Neue', Arial, Helvetica, sans-serif;
        }
    </style>
</head>
<body>
    <div id="map" />
    <script>
        //implementing the map
        var map = L.map('map').setView([49.2606, -123.246], 14);
        L.tileLayer(
            'https://api.maptiler.com/maps/openstreetmap/{z}/{x}/{y}.jpg?key=trso7A0Tlla6OjFKuxky',
            {
                tileSize: 512,
                zoomOffset: -1,
                minZoom: 1,
                attribution:
                    '\u003ca href="https://www.maptiler.com/copyright/" target="_blank"\u003e\u0026copy; MapTiler\u003c/a\u003e \u003ca href="https://www.openstreetmap.org/copyright" target="_blank"\u003e\u0026copy; OpenStreetMap contributors\u003c/a\u003e',
                crossOrigin: true
            }
        ).addTo(map);

        const waypoints = [
            {
                name: 'Alpha',
                longitude: 49.2606,
                latitude: -123.246,
                altitude: 50.7
            },
            {
                name: 'Beta',
                longitude: 49.2606,
                latitude: -123.256,
                altitude: 50.7
            },
            {
                name: 'Gamma',
                longitude: 49.2506,
                latitude: -123.236,
                altitude: 50.7
            },
            {
                name: 'Gamma',
                longitude: 49.2406,
                latitude: -123.206,
                altitude: 50.7
            }
        ];

        //for the drones position on the map

        let mockdata = {
            velocity: 22.2,
            longitude: 49.2606,
            latitude: -123.248,
            altitude: 28.1111,
            heading: 11.2
        };

        let velocity = mockdata.velocity;
        let longitude = mockdata.longitude;
        let latitude = mockdata.latitude;
        let heading = mockdata.heading;
        let altitude = mockdata.altitude;

        //displaying markers

        for (i in waypoints) {
            L.marker([waypoints[i].longitude, waypoints[i].latitude]).addTo(map);
        }

        //connecting line between markers
        var polylinePoints = [];

        for (i in waypoints) {
            polylinePoints.push([waypoints[i].longitude, waypoints[i].latitude]);
        }

        var polyline = L.polyline(polylinePoints).addTo(map);

        // zoom the map to the polyline
        map.fitBounds(polyline.getBounds());

        //displaying the position of the drone on the map
        var greenIcon = L.icon({
            iconUrl: 'https://www.pngall.com/wp-content/uploads/4/Drone-PNG-Free-Download.png',
            iconSize: [40, 50] // size of the icon
        });

        L.marker([longitude, latitude], { icon: greenIcon }).addTo(map);

        //showing direction of movement of the drone on the map
        //connecting line between markers
        var polylinePoints2 = [];

        var heading_longitude = longitude + 5 * Math.cos((heading * Math.PI) / 180);
        var heading_latitude = latitude + 5 * Math.sin((heading * Math.PI) / 180);

        polylinePoints2.push([longitude, latitude]);
        polylinePoints2.push([heading_longitude, heading_latitude]);

        var polyline2 = L.polyline(polylinePoints2, { color: '#E60026' }).addTo(map);

        //placing arrows in with the waypoint lines (from stackoverflow)

        function getArrows(arrLatlngs, color, arrowCount, mapObj) {
            if (
                typeof arrLatlngs === undefined ||
                arrLatlngs == null ||
                !arrLatlngs.length ||
                arrLatlngs.length < 2
            )
                return [];

            if (typeof arrowCount === 'undefined' || arrowCount == null) arrowCount = 1;

            if (typeof color === 'undefined' || color == null) color = '';
            else color = 'color:' + color;

            var result = [];
            for (var i = 1; i < arrLatlngs.length; i++) {
                var icon = L.divIcon({
                    className: 'arrow-icon',
                    bgPos: [5, 5],
                    html:
                        '<div style="' +
                        color +
                        ';transform: rotate(' +
                        getAngle(arrLatlngs[i - 1], arrLatlngs[i], -1).toString() +
                        'deg)">▶</div>'
                });
                for (var c = 1; c <= arrowCount; c++) {
                    result.push(
                        L.marker(
                            myMidPoint(
                                arrLatlngs[i],
                                arrLatlngs[i - 1],
                                c / (arrowCount + 1),
                                mapObj
                            ),
                            { icon: icon }
                        )
                    );
                }
            }
            return result;
        }

        function getAngle(latLng1, latlng2, coef) {
            var dy = latlng2[0] - latLng1[0];
            var dx = Math.cos((Math.PI / 180) * latLng1[0]) * (latlng2[1] - latLng1[1]);
            var ang = (Math.atan2(dy, dx) / Math.PI) * 180 * coef;
            return ang.toFixed(2);
        }

        function myMidPoint(latlng1, latlng2, per, mapObj) {
            if (!mapObj) throw new Error('map is not defined');

            var halfDist,
                segDist,
                dist,
                p1,
                p2,
                ratio,
                points = [];

            p1 = mapObj.project(new L.latLng(latlng1));
            p2 = mapObj.project(new L.latLng(latlng2));

            halfDist = distanceTo(p1, p2) * per;

            if (halfDist === 0) return mapObj.unproject(p1);

            dist = distanceTo(p1, p2);

            if (dist > halfDist) {
                ratio = (dist - halfDist) / dist;
                var res = mapObj.unproject(
                    new Point(p2.x - ratio * (p2.x - p1.x), p2.y - ratio * (p2.y - p1.y))
                );
                return [res.lat, res.lng];
            }
        }

        function distanceTo(p1, p2) {
            var x = p2.x - p1.x,
                y = p2.y - p1.y;

            return Math.sqrt(x * x + y * y);
        }

        function toPoint(x, y, round) {
            if (x instanceof Point) {
                return x;
            }
            if (isArray(x)) {
                return new Point(x[0], x[1]);
            }
            if (x === undefined || x === null) {
                return x;
            }
            if (typeof x === 'object' && 'x' in x && 'y' in x) {
                return new Point(x.x, x.y);
            }
            return new Point(x, y, round);
        }

        function Point(x, y, round) {
            this.x = round ? Math.round(x) : x;
            this.y = round ? Math.round(y) : y;
        }

        L.featureGroup(getArrows(polylinePoints, 'black', 1, map)).addTo(map);
    </script>
</body>
