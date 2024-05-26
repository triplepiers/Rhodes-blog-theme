<script setup lang="ts">
import Cursor from '@/components/home/Cursor.vue'
import Rhodes from '@/components/home/Rhodes.vue'
import Menu from '@/components/home/Menu.vue'

import '@/lib/fullpage.min.css'
import '@/lib/fullpage.js'
import '@/lib/typed.js'

import configs from '@/data/config.js';
import { onMounted } from 'vue'

function initFullPage(config) {
  // init 
  $('#fullpage').fullpage(config);

  // other methods
  // $.fn.fullpage.setAllowScrolling(false); // 禁止滚动（只能方向键 / menu）
}

function initTyped(typedList) {
  typedList.forEach((typedConfig) => {
    new Typed(...typedConfig)
  })
}

function initHomePage(configs) {
  $(document).ready(function () {
    // overall
    initFullPage(configs['fullpageOptions']);

    // section1
    initTyped(configs['typedList']);
  });
}

onMounted(() => {
  initHomePage(configs);
})
</script>

<template>
  <!-- cursor -->
  <Cursor />

  <!-- fullPage -->
  <div id="fullpage">
    <Rhodes />
    <Menu />
  </div>
</template>

<style>
body {
  cursor: none;
  background-size: cover;
  background-image: url('@/assets/img/main-background.jpg');
  background-position: center center;
}

.section {
  padding: 20px 30px;
}
</style>