<script setup>
import { onMounted, ref } from 'vue';
import AnimatedBall from './AnimatedBall.vue';

const data = [
  { start: { x: 1, y: 1 }, end: { x: 3, y: 1 } },
  { start: { x: 3, y: 1 }, end: { x: 3, y: 1 } },
  { start: { x: 1, y: 3 }, end: { x: 3, y: 1 } },
  { start: { x: 3, y: 3 }, end: { x: 3, y: 1 } }
]

const panel = ref(null)
</script>

<template>
  <div class="wrapper">
    <div class="panel" ref="panel">
      <div class="box" v-for="item in 9" :key="item">
        {{ item }}
      </div>
      <div class="panel">
        <AnimatedBall v-for="(item, idx) in data" :key="idx" :from="item.from" :to="item.to">
          {{
        idx
        +
        1 }}
        </AnimatedBall>
      </div>
    </div>

  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  padding: 1rem;
}

.panel {
  position: relative;
  width: 100%;
  display: grid;
  grid-template: repeat(3, 100px) / repeat(3, 1fr);
  gap: 10px;
}

.panel>.panel {
  position: absolute;
  inset: 0;
}

:deep(.frame:nth-child(2)) {
  grid-column: 3 / 4;
}

:deep(.frame:nth-child(3)) {
  grid-column: 1 / 2;
  grid-row: 3 / 4;
}

:deep(.frame:nth-child(4)) {
  grid-column: 3 / 4;
  grid-row: 3 / 4;
}

.box {
  display: grid;
  place-content: center;
  height: 100px;
  border: black solid 2px;
  background: radial-gradient(circle, rgba(113, 81, 95, 1) 81%, rgba(0, 0, 0, 1) 100%);
}

.box:nth-child(6n+3),
.box:nth-child(6n+5) {
  animation: flash 1s infinite;
}

@keyframes flash {
  0% {
    opacity: 1;
  }

  50% {
    opacity: 0.6;
  }

  100% {
    opacity: 1;
  }
}
</style>