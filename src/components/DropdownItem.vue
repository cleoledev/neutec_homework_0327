<script setup>
import { ref } from 'vue'

defineProps({
  data: {
    type: Array,
    required: true
  },
  open: {
    type: Boolean
  }
})

const currentOpened = ref('')

function toggleOpen(key) {
  currentOpened.value = currentOpened.value === key ? '' : key
}
</script>

<template>
  <ul class="dropdown__wrapper">
    <li class="dropdown__item" :class="{ open: currentOpened === item.key }" v-for="item in data" :key="item.key">
      <button class="dropdown__btn" @click="toggleOpen(item.key)">{{ item.text }}</button>
      <DropdownItem v-if="item.children?.length" :data="item.children" :key="currentOpened === item.key" />
    </li>
  </ul>
</template>

<style scoped>
.dropdown__wrapper {
  min-height: 0;
  overflow: hidden;
  z-index: 0;
}

.dropdown__item {
  display: grid;
  grid-template-rows: max-content 0fr;
  transition: grid-template-rows 300ms ease;
}

.dropdown__item.open {
  grid-template-rows: max-content 1fr;
}


.dropdown__item>.dropdown__wrapper {
  margin-left: 1em;
}

.dropdown__btn {
  padding: 0.5em 0;
  text-align: left;
}
</style>