<template>
  <div id="center_fz8">

    <div ref="map_vkz" style=" width: 84%;
    height: 95vh;
    z-index: 1;
    position: absolute">

    </div>

  </div>

</template>

<script>

import L from 'leaflet';
import "leaflet/dist/leaflet.css";
import jilingeo from "../../../public/data/jilingeo";

export default {
// name: 'Test',
  mounted() {
    this.init_leaf();

  },


  data() {
    return {
      map: undefined,
    }
  },
  components: {},
  methods: {
    onMapClick(e) {
      this.popup
        .setLatLng(e.latlng)
        .setContent("Location:" + e.latlng.toString())
        .openOn(this.map);
    },
    onMapZoom() {
      // if (this.map.getZoom() > 9) {
      //   this.map.removeLayer(this.glayer_fusheqv);
      // }
      // if (this.map.getZoom() < 8) {
      //   this.map.addLayer(this.glayer_heituqv);
      //
      // }
      //
      // if (this.map.getZoom() < 9) {
      //
      //   this.map.addLayer(this.glayer_fusheqv);
      // }
    },
    init_leaf() {
      //创建地图
      this.map = L.map(this.$refs.map_vkz, {
        center: [43.430018, 126.629423],
        zoom: 6,
        crs: L.CRS.EPSG3857,
        maxZoom: 18,
        editable: true,
        // 去除放大缩小控件
        // https://stackoverflow.com/questions/16537326/leafletjs-how-to-remove-the-zoom-control
        zoomControl: false,
        layerControl: false,
        attributionControl: false,
        // Attribution: false,
      });
      this.popup = L.popup();
      this.map.on('click', this.onMapClick);
      this.map.on('zoom', this.onMapZoom);


      // 天地图地图及标示  osm，osm1.
      // this.osm = L.tileLayer('http://t4.tianditu.gov.cn/DataServer?T=vec_w&X={x}&Y={y}&L={z}&tk=57f1b8146ef867f14189f3f4bb1adc1c', {
      //   title: '天地图网格图',
      //   maxZoom: 18,
      //   id: "mapbox.streets"
      // });
      this.osm1 = L.tileLayer('http://t4.tianditu.gov.cn/DataServer?T=cia_w&X={x}&Y={y}&L={z}&tk=57f1b8146ef867f14189f3f4bb1adc1c', {
        title: '天地图中文标注',
        maxZoom: 18,
        id: "mapbox.streets"
      });

      this.osm2 = L.tileLayer('http://t4.tianditu.gov.cn/DataServer?T=img_w&X={x}&Y={y}&L={z}&tk=57f1b8146ef867f14189f3f4bb1adc1c', {
        title: '影像',
        maxZoom: 18,
        id: "mapbox.streets"
      });
      this.osm2.addTo(this.map);




 this.tilelayer = L.geoJSON(jilingeo, {onEachFeature: this.onEachTaizhan})
      this.tilelayer.addTo(this.map)



      L.control.scale({
        position: 'topright',
        maxWidth: '100',
        imperial: false
      }).addTo(this.map);
    },

       onEachTaizhan: function (feature, layer) {


        // layer.bindTooltip("<div><b>" + feature.properties.Name + "</b></div>",
        //     {
        //       permanent: true,
        //       direction: 'auto',
        //       className: 'kind4',
        //     });

      layer.bindPopup(
          "<b>" + feature.properties.Name + "</b>",
        {
          closeButton: false
        }
      )


      layer.on('click', function (e) {

        console.log(e.latlng);



      });
    },

  }
}
</script>

<style lang="scss" scoped>


#center_fz8 {
  height: 95vh;
}
</style>
