<script setup>
import sideMenuData from './assets/data.json'
import SideMenu from './components/SideMenu.vue'
import PuzzleBlock from './components/PuzzleBlock.vue'
</script>

<template>
  <SideMenu :data="sideMenuData" />
  <PuzzleBlock />
</template>
