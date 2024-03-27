<script setup>
defineProps({
  start: {
    type: Object,
    required: true
  },
  end: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div class="ball"
    :style="{ '--x': `${start.x}px`, '--y': `${start.y}px`, '--dx': `${end.x}px`, '--dy': `${end.y}px` }">
    <slot />
  </div>
</template>

<style scoped>
.ball {
  position: absolute;
  left: 0;
  top: 0;
  width: 30px;
  height: 30px;
  display: grid;
  place-content: center;
  border-radius: 50%;
  background-color: #A5F12B;
  animation: move 2s ease infinite;
}

@keyframes move {
  from {
    transform: translateX(var(--x)) translateX(-50%) translateY(var(--y)) translateY(-50%);
  }

  to {
    transform: translateX(var(--dx)) translateX(-50%) translateY(var(--dy)) translateY(-50%);
  }
}

/* @keyframes move {
  0% {
    transform: translateX(0);
  }

  80% {
    transform: translateX(100vw);
  }

  100% {
    transform: translateX(100vw);
  }
} */
</style>