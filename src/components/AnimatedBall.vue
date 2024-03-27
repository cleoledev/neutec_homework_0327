<script setup>
// defineProps({
//   start: {
//     type: Object,
//     required: true
//   },
//   end: {
//     type: Object,
//     required: true
//   }
// })
</script>

<template>
  <div class="frame">
    <span class="ball">
      <slot />
    </span>
  </div>
</template>

<style scoped>
.frame {
  display: grid;
  place-content: center;
  animation: move 2s linear infinite;
}

.ball {
  isolation: isolate;
  display: grid;
  place-content: center;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  background-color: #A5F12B;
}

@keyframes move {
  0% {
    transform: translateX(0);
  }

  80% {
    transform: translateX(100vw);
  }

  100% {
    transform: translateX(100vw);
  }
}
</style>