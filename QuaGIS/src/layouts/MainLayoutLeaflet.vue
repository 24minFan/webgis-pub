<template>
  <q-layout view="hHh lpR fFf">

 <EssentialHead />

    <q-drawer show-if-above v-model="store.leftDrawerOpen" side="left" bordered>


      <q-list>
        <q-item-label header>
          页面Leaflet

        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view/>
    </q-page-container>

  </q-layout>
</template>

<script lang="ts">
import {defineComponent, ref} from 'vue';
import EssentialLink from 'components/EssentialLink.vue';
import EssentialHead from "components/Head.vue";
  import {useCommonFunctionStore} from 'stores/common_function'

const linksList = [
  // {
  //   title: 'Home',
  //   caption: '内容介绍说明',
  //   icon: 'school',
  //   link: '/#/leaflet/index'
  // },


  {
    title: '使用GeoJson',
    caption: '全能型WebGIS类库',
    icon: 'chat',
    link: '/leaflet/index'
  },
  {
    title: 'Leaflet黑土应用',
    caption: '轻量级WebGIS类库',
    icon: 'code',
    link: '/leaflet/bleaflet'
  },
  {
    title: 'Leaflet风场可视化',
    caption: '数据可视化',
    icon: 'code',
    link: '/leaflet/bwind'
  },
  {
    title: 'Leaflet弹窗',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf4'
  },

  {
    title: 'Leaflet坐标弹窗',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf6'
  },
  {
    title: 'Leaflet WMS',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf7'
  },
  {
    title: 'Leaflet IMG',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf8'
  },
  {
    title: 'Leaflet Video',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf9'
  },

     {
    title: 'Leaflet Geojson 点击弹窗',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf12'
  },
      {
    title: 'Leaflet SmoothWheelZoom',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf13'
  },
       {
    title: 'Leaflet 鼠标划过展示坐标',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf15'
  },
  {
    title: 'Leaflet 增删WMS图层',
    caption: 'Leaflet 简单示例',
    icon: 'code',
    link: '/leaflet/lf14'
  },
  // {
  //   title: 'MapTalks',
  //   caption: 'Developed in China',
  //   icon: 'record_voice_over',
  //   link: '/leaflet/bmaptalks'
  // },
  // {
  //   title: 'MapBox',
  //   caption: '精美地图',
  //   icon: 'rss_feed',
  //   link: '/leaflet/bmapbox'
  // },
  //
  // {
  //   title: 'Cesium',
  //   caption: '开源的3D GIS',
  //   icon: 'favorite',
  //   link: '/leaflet/bcesium'
  // }
];

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialHead,
    EssentialLink
  },

  setup() {

      const store = useCommonFunctionStore();
    return {
      essentialLinks: linksList,

      store
    }
  }
});
</script>
