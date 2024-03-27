<script setup>
import sideMenuData from './assets/data.json'
import SideMenu from './components/SideMenu.vue'
</script>

<template>
  <SideMenu :data="sideMenuData" />
</template>

<style scoped></style>
