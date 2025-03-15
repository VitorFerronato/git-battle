<template>
  <div id="app">
    <BattleInputs v-if="!results" @update:results="results = $event" />

    <BattleCard v-else :results="results" @resetBattle="results = null" />
  </div>
</template>

<script setup>
import { ref } from "vue";

import BattleCard from "./components/BattleCard.vue";
import BattleInputs from "./components/BattleInputs.vue";

const results = ref(null);
</script>

<style scoped>
#app {
  min-width: 100vw;
  min-height: 100vh;
  background-color: var(--bg-color);
  overflow: hidden;
}
</style>
