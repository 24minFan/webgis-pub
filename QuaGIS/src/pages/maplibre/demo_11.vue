<template>

  <div id="mapid" class="absolute"></div>
  <div class="absolute divclass">
    设置localIdeographFontFamily以覆盖用于显示CJK(中文、日文和韩文)字符的字体，忽略地图样式。此设置必须是指定设备上字体回退的CSS字体规则。将localIdeographFontFamily设置为false以使用服务器提供的字体，这要慢得多。
  </div>
</template>

<script>
  import maplibregl from 'maplibre-gl';
  import {onMounted} from "vue";

  import 'maplibre-gl/dist/maplibre-gl.css';

  export default {
    name: "demo_11",
    setup() {

      var map = null;
      const initMap = () => {

        const MAPTILER_KEY = 'hAA4PuTSrWhRcIgil5Fy';
        map = new maplibregl.Map({
          container: 'mapid',

          style:
            `https://api.maptiler.com/maps/streets/style.json?key=${MAPTILER_KEY}`,
          center: [120.3049, 31.4751],
          zoom: 12,
          localIdeographFontFamily: '"Apple LiSung", serif'
        });


        map.on('load', () => {
          //导航控件：
          console.log()
        })

      }

      onMounted(() => {
        initMap()

      })


      return {}
    }
  }
</script>

<style scoped>
  #mapid {
    top: 10vh;
    right: 10px;
    height: 70vh;
    width: 60vw
  }

  .divclass {
    right: 5px;
    width: 18vw;
    top: 20vh;
    height: 20vh;
  }
</style>
