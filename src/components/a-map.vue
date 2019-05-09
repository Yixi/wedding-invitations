<template>
  <div class="map-info">
    <div id="wrap" class="my-map">
      <div id="mapContainer"></div>
    </div>
  </div>
</template>

<script>
  export default {
    mounted() {
      this.initMap()
    },
    methods: {
      initMap() {
        const AMap = window.AMap

        !function () {
          var infoWindow, map, level = 15,
              center = {lng: 103.902062, lat: 30.792991},
              features = [{
                type: "Marker",
                name: "",
                desc: "",
                color: "red",
                icon: "cir",
                offset: {x: -9, y: -31},
                lnglat: {lng: 103.902083, lat: 30.792954}
              }];

          function loadFeatures() {
            for (var feature, data, i = 0, len = features.length, j, jl, path; i < len; i++) {
              data = features[i];
              switch (data.type) {
                case "Marker":
                  feature = new AMap.Marker({
                    map: map,
                    position: new AMap.LngLat(data.lnglat.lng, data.lnglat.lat),
                    zIndex: 3,
                    extData: data,
                    offset: new AMap.Pixel(data.offset.x, data.offset.y),
                    title: data.name,
                    content: '<div class="icon icon-' + data.icon + ' icon-' + data.icon + '-'
                        + data.color + '"></div>'
                  });
                  break;
                case "Polyline":
                  for (j = 0, jl = data.lnglat.length, path = []; j < jl; j++) {
                    path.push(new AMap.LngLat(data.lnglat[j].lng, data.lnglat[j].lat));
                  }
                  feature = new AMap.Polyline({
                    map: map,
                    path: path,
                    extData: data,
                    zIndex: 2,
                    strokeWeight: data.strokeWeight,
                    strokeColor: data.strokeColor,
                    strokeOpacity: data.strokeOpacity
                  });
                  break;
                case "Polygon":
                  for (j = 0, jl = data.lnglat.length, path = []; j < jl; j++) {
                    path.push(new AMap.LngLat(data.lnglat[j].lng, data.lnglat[j].lat));
                  }
                  feature = new AMap.Polygon({
                    map: map,
                    path: path,
                    extData: data,
                    zIndex: 1,
                    strokeWeight: data.strokeWeight,
                    strokeColor: data.strokeColor,
                    strokeOpacity: data.strokeOpacity,
                    fillColor: data.fillColor,
                    fillOpacity: data.fillOpacity
                  });
                  break;
                default:
                  feature = null;
              }
              if (feature) {
                AMap.event.addListener(feature, "click", mapFeatureClick);
              }
            }
          }

          function mapFeatureClick(e) {
            if (!infoWindow) {
              infoWindow = new AMap.InfoWindow({autoMove: true});
            }
            var extData = e.target.getExtData();
            infoWindow.setContent("<h5>" + extData.name + "</h5><div>" + extData.desc + "</div>");
            infoWindow.open(map, e.lnglat);
          }

          map = new AMap.Map("mapContainer",
              {center: new AMap.LngLat(center.lng, center.lat), level: level});

          loadFeatures();
        }();
      }
    }
  }
</script>

<style>
  .my-map {
    margin: 0 auto;
    width: calc(100% - 40px);
    height: 200px;
    border: 1px solid #c1c1c1;
  }

  .my-map .icon {
    background: url(http://lbs.amap.com/console/public/show/marker.png) no-repeat;
  }

  .my-map .icon-cir {
    height: 31px;
    width: 28px;
  }

  .my-map .icon-cir-red {
    background-position: -11px -5px;
  }

  .amap-container {
    height: 100%;
  }

  .map-info {
    height: 200px;
    width: 100%;
    padding: 20px 0px;
  }
</style>
