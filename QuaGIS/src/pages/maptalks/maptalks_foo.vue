<template>
  <div id="map" class="container"></div>
</template>
<script>
import 'maptalks/dist/maptalks.css';
import * as maptalks from 'maptalks';

export default {
  mounted() {
    this.$nextTick(() => {
      const map = new maptalks.Map('map', {
        center: [125.1, 47.15],

        zoom: 6,
        baseLayer: new maptalks.TileLayer('base', {
          urlTemplate: 'http://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png',
          // urlTemplate: 'http://t{s}.tianditu.gov.cn/img_w/wmts?tk=bb11a33c4377f10603478ed166691455&SERVICE=WMTS&REQUEST=GetTile&VERSION=1.0.0&LAYER=img&STYLE=default&TILEMATRIXSET=w&FORMAT=tiles&TileMatrix={z}&TileCol={x}&TileRow={y}',
          subdomains: ['a', 'b', 'c', 'd'],
          attribution: '© <a href="http://osm.org">OpenStreetMap</a> contributors, © <a href="https://carto.com/">CARTO</a>',
        }),
        layers: [
          new maptalks.WMSTileLayer('wms', {
            'urlTemplate': 'http://tile.igadc.cn/service?',
            'crs': 'EPSG:3857',
            'layers': 'qn9326',
            'styles': '',
            'version': '1.3.0',
            'format': 'image/png',
            'transparent': true,
            'uppercase': true
          })
        ]
      });

    });
  },
};
</script>

<style lang="scss">
.container {
  width: 100%;
  height: 90vh
}
</style>

