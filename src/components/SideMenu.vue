<script setup>
import { ref } from 'vue'
import DropdownItem from './DropdownItem.vue';

const props = defineProps({
  data: {
    type: Array,
    required: true
  }
})

const isOpen = ref(false)
</script>

<template>
  <div class="sidemenu">
    <button class="trigger" @click="isOpen = !isOpen">
      open
      <span></span>
      <span></span>
      <span></span>
    </button>
    <Transition name="fade">
      <div class="sidemenu__mask" v-show="isOpen" @click="isOpen = false"></div>
    </Transition>
    <Transition name="slide">
      <div class="sidemenu__panel" v-show="isOpen">
        <DropdownItem :data="data"></DropdownItem>
      </div>
    </Transition>
  </div>
</template>

<style>
.sidemenu {
  display: flex;
  align-items: center;
  justify-content: end;
  background-color: #fff;
  height: 60px;
}

.trigger {
  display: grid;
  place-content: center;
  gap: 6px;
  font-size: 0;
  line-height: 0;
  padding: 1rem;
  cursor: pointer;
}

.trigger span {
  display: block;
  background-color: #000;
  width: 30px;
  height: 2px;
}

.sidemenu__panel {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  padding: 1.5rem 0;
  min-width: 25vw;
  color: #fff;
  background-color: #000;
  z-index: 2;
}

.sidemenu__mask {
  position: fixed;
  inset: 0;
  z-index: 1;
  background-color: rgba(0 0 0 / 0.4);
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 400ms ease;
}

.slide-enter-from,
.slide-leave-to {
  transform: translateX(100%);
}

.slide-enter-to,
.slide-leave-from {
  transform: translateX(0);
}


.fade-enter-active,
.fade-leave-active {
  transition: opacity 300ms ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
</style>