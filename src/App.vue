<template>
  <div id="app">
    <Transition name="slide" mode="out-in">
      <BattleInputs v-if="!results" @update:results="results = $event" />
      <BattleCard v-else :results="results" @resetBattle="results = null" />
    </Transition>
  </div>
</template>

<script setup>
import { ref } from "vue";

import BattleCard from "./components/BattleCard.vue";
import BattleInputs from "./components/BattleInputs.vue";

const results = ref(null);
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.2s ease, opacity 0.2s ease;
}

.slide-enter-from {
  transform: translateX(-80%);
  opacity: 0;
}

.slide-leave-to {
  transform: translateX(-80%);
  opacity: 0;
}

#app {
  min-width: 100vw;
  min-height: 100vh;
  background-color: var(--bg-color);
  overflow: hidden;
}
</style>
