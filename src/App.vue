<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <com :title-info="{value: '笨蛋', color: 'red'}"></com> -->
  <!-- <echartsDemo></echartsDemo> -->
  <!-- <ComSetup :title-info="{value: '笨蛋', color: 'red'}"></ComSetup> -->
  <!-- <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" /> -->
  <router-view></router-view>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'
const router = useRouter()
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
// import HelloWorld from './components/HelloWorld.vue'
// import com from './components/com.vue'
// import ComSetup from './components/comSetup.vue';
// import echartsDemo from './components/echartsDemo.vue'
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
