<script setup>
import { ref } from 'vue'

const props = defineProps({
  data: {
    type: Array,
    required: true
  },
  open: {
    type: String,
    default: '',
    required: true
  }
})

const emit = defineEmits(['dropdown'])
const currentOpened = ref('')

function toggleOpen(data) {
  currentOpened.value = currentOpened.value === data.key ? '' : data.key
  onDropdown(currentOpened.value)
}

function validate(key) {
  return props.open.split('/').includes(key)
}

function onDropdown(value) {
  emit('dropdown', value)
}
</script>

<template>
  <ul class="dropdown__wrapper">
    <li class="dropdown__item" :class="{ open: validate(item.key) }" v-for="item in data" :key="item.key">
      <button class="dropdown__btn" @click="toggleOpen(item)">{{ item.text }}</button>
      <Transition :duration="300">
        <DropdownItem :open="open" @dropdown="onDropdown($event ? `${item.key}/${$event}` : item.key)"
          v-if="item.children && validate(item.key)" :data="item.children" />
      </Transition>
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
  background-color: #aaa;
}

.dropdown__item.open>.dropdown__btn {
  color: yellow;
}


.dropdown__item>.dropdown__wrapper {
  margin-left: 1em;
}

.dropdown__btn {
  padding: 1em;
  text-align: left;
}
</style>