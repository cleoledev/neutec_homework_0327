<script setup>
import DropdownItem from './DropdownItem.vue';

const props = defineProps({
  data: {
    type: Array,
    required: true
  }
})

</script>

<template>
  <div class="sidemenu">
    <DropdownItem :data="data"></DropdownItem>
  </div>
</template>

<style>
.sidemenu {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  padding: 2rem;
  min-width: 20vw;
  color: #fff;
  background-color: #000;
}
</style>