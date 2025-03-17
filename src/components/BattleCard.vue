<template>
  <div class="result-container">
    <div class="result-user-info">
      <ResultCard :dev="results?.dev1" />
      <img src="../assets/vs-showdown.png" alt="" class="showdown" />
      <ResultCard :dev="results?.dev2" />
    </div>

    <div v-if="results?.winner">
      <div class="winner">
        <h4>WINNER</h4>
        <p>{{ results.winner }}</p>

        <Tooltip />
      </div>

      <div class="button">
        <GBButton title="Return" @click="$emit('resetBattle')" />
      </div>
    </div>
  </div>
</template>

<script setup>
import ResultCard from "./ResultCard.vue";
import GBButton from "./GBButton.vue";
import Tooltip from "./Tooltip.vue";

defineProps({
  results: Object,
});
</script>

<style scoped>
.result-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.result-user-info {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

.showdown {
  width: 100px;
}

.winner {
  position: relative;
  margin-top: 2rem;
  border: 0.5px solid var(--primary-color);
  width: 250px;
  padding: 1rem;
  color: var(--white-color);
}

.winner h4 {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: -2rem;
  background-color: var(--bg-color);
}

.winner p {
  margin-top: 0.5rem;
  padding: 0;
  text-align: center;
  font-size: 24px;
}

.button {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.how-winner {
  margin-top: 5rem;
  color: var(--white-color);
}

.how-winner:hover {
  text-decoration: underline;
}
</style>
